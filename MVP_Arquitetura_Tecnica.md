# GuIA — Arquitetura Técnica do MVP
**MBA Tera · Liderança e Estratégia de Produtos Digitais na Era da IA**
**Documento Técnico — como a IA funciona de fato no produto**
**Produzido em:** Junho 2026

> **Escopo:** Brasil exclusivamente. IRPF de pessoa física. Open Finance regulado pelo BCB. Stack Python (backend) + React (web) + React Native (iOS/Android).

---

## 1. Visão Geral do MVP

O GuIA MVP entrega **três funcionalidades centrais** de IA:

```
┌─────────────────────────────────────────────────────────────┐
│                    USUÁRIO                                   │
│  Clara · Rafael · Lucas · Família Silva                      │
└──────────────┬──────────────┬──────────────┬────────────────┘
               │              │              │
               ▼              ▼              ▼
     [Conecta banco]   [Fotografa nota]  [Pergunta ao GuIA]
           │                 │                 │
           ▼                 ▼                 ▼
   ┌───────────────┐  ┌────────────┐  ┌──────────────────┐
   │ OPEN FINANCE  │  │    OCR     │  │  CHAT TRIBUTÁRIO  │
   │ via Pluggy    │  │  Textract  │  │   Claude Sonnet   │
   │ (extratos,    │  │ + Claude   │  │  + System Prompt  │
   │  investim.)   │  │  Vision    │  │  especialista BR  │
   └───────┬───────┘  └─────┬──────┘  └────────┬─────────┘
           │                │                   │
           ▼                ▼                   │
   ┌───────────────────────────────────┐         │
   │     CATEGORIZADOR DE TRANSAÇÕES   │         │
   │  1. Regex (70% dos casos, grátis) │         │
   │  2. XGBoost + MCC code (20%)      │         │
   │  3. Claude Haiku fallback (10%)   │         │
   └───────────────┬───────────────────┘         │
                   │                             │
                   ▼                             │
   ┌───────────────────────────────────┐         │
   │       RULES ENGINE (IRPF)         │◄────────┘
   │  • Tabelas progressivas 2026      │
   │  • Limites de dedução legais      │
   │  • Simula completa vs simplificada│
   │  • Calcula DARF renda variável    │
   └───────────────┬───────────────────┘
                   │
                   ▼
   ┌───────────────────────────────────┐
   │         RESULTADO                 │
   │  • Deduções identificadas: R$ X   │
   │  • Restituição estimada: R$ Y     │
   │  • Badge DEDUTÍVEL por transação  │
   │  • DARF a pagar (se houver)       │
   └───────────────────────────────────┘
```

---

## 2. Os 4 Níveis de IA do GuIA

### Nível 1 — Rules Engine (determinístico, zero custo de IA)

**O que faz:** Cálculo de IR, DARF, escolha entre modelo completo vs. simplificado, projeção de restituição.

**Por que não usa IA generativa aqui:** Cálculo tributário precisa ser **100% determinístico e auditável**. Um LLM nunca deve calcular o imposto — apenas explicar.

```python
# /app/services/ir_rules.py

TABELA_IRPF_2026 = [
    {"ate": 2259.20, "aliquota": 0.00, "deducao": 0.00},
    {"ate": 2826.65, "aliquota": 0.075, "deducao": 169.44},
    {"ate": 3751.05, "aliquota": 0.15, "deducao": 381.44},
    {"ate": 4664.68, "aliquota": 0.225, "deducao": 662.77},
    {"ate": float("inf"), "aliquota": 0.275, "deducao": 896.00},
]

LIMITES_DEDUCAO_2026 = {
    "dependente": 2275.08,      # por dependente/ano
    "educacao": 3561.50,        # por dependente/ano (com limite)
    "pgbl": 0.12,               # 12% da renda bruta
    "inss_voluntario": 9_000.0, # MEI
    # saúde: sem limite
}

def calcular_ir_anual(renda_bruta: float, deducoes: dict) -> dict:
    """Calcula IR anual e restituição/saldo a pagar."""
    
    # Modelo completo
    base_completo = max(0, renda_bruta
        - deducoes.get("inss", 0)
        - deducoes.get("dependentes_total", 0)
        - deducoes.get("saude", 0)
        - min(deducoes.get("educacao", 0), LIMITES_DEDUCAO_2026["educacao"] * deducoes.get("n_dependentes", 0))
        - min(deducoes.get("pgbl", 0), renda_bruta * LIMITES_DEDUCAO_2026["pgbl"])
    )
    ir_completo = _aplicar_tabela(base_completo)
    
    # Modelo simplificado (desconto de 20%, máx R$ 16.754,34)
    deducao_simpl = min(renda_bruta * 0.20, 16_754.34)
    base_simpl = max(0, renda_bruta - deducao_simpl)
    ir_simpl = _aplicar_tabela(base_simpl)
    
    # Recomendação
    modelo_otimo = "completo" if ir_completo < ir_simpl else "simplificado"
    economia = abs(ir_simpl - ir_completo)
    
    return {
        "modelo_recomendado": modelo_otimo,
        "ir_completo": ir_completo,
        "ir_simplificado": ir_simpl,
        "economia_com_otimizacao": economia,
        "restituicao_estimada": deducoes.get("ir_retido", 0) - min(ir_completo, ir_simpl),
    }

def _aplicar_tabela(base: float) -> float:
    for faixa in TABELA_IRPF_2026:
        if base <= faixa["ate"]:
            return base * faixa["aliquota"] - faixa["deducao"]
    return 0.0
```

---

### Nível 2 — Categorizador de Transações (ML híbrido)

**O que faz:** Classifica cada transação bancária como dedutível no IR ou não. Usa pipeline de 3 estágios em ordem crescente de custo.

```python
# /app/services/categorizer.py

# Stage 1: Regex (custo zero, ~70% dos casos)
REGRAS_CATEGORIAS = {
    "saude": {
        "keywords": ["farmacia", "drogaria", "hospital", "clinica", "laboratorio",
                     "medico", "dentista", "plano de saude", "unimed", "amil",
                     "sulamerica", "bradesco saude", "notredame", "hapvida"],
        "dedutivel": True,
        "limite": None,  # sem limite para saúde PF
        "ficha_dirpf": "Pagamentos/Deduções > Saúde"
    },
    "educacao": {
        "keywords": ["escola", "colegio", "faculdade", "universidade", "curso",
                     "idiomas", "mensalidade", "matricula", "material escolar"],
        "dedutivel": True,
        "limite_por_dependente": 3561.50,
        "ficha_dirpf": "Pagamentos/Deduções > Educação"
    },
    "pgbl_previdencia": {
        "keywords": ["brasilprev", "icatu", "zurich previdencia", "caixa previdencia",
                     "pgbl", "vgbl", "previdencia privada", "prev"],
        "dedutivel": True,
        "limite_pct_renda": 0.12,
        "ficha_dirpf": "Pagamentos/Deduções > Previdência Privada"
    },
    "alimentacao": {
        "keywords": ["ifood", "rappi", "uber eats", "supermercado", "padaria",
                     "restaurante", "lanchonete", "mercado", "hortifruti"],
        "dedutivel": False
    },
    "transporte": {
        "keywords": ["uber", "99", "cabify", "combustivel", "estacionamento",
                     "onibus", "metro", "bilhete unico"],
        "dedutivel": False  # não dedutível para CLT (apenas para autônomos)
    },
    "pensao_alimenticia": {
        "keywords": ["pensao alimenticia", "alimentos", "pensao judicial"],
        "dedutivel": True,
        "limite": None,
        "ficha_dirpf": "Pagamentos/Deduções > Pensão Alimentícia"
    },
}

def categorizar_transacao(descricao: str, valor: float, mcc_code: str = None) -> dict:
    """
    Pipeline de categorização em 3 estágios.
    Custo: Stage 1 = R$ 0, Stage 2 = R$ 0 (modelo local), Stage 3 = ~R$ 0,0001/transação
    """
    descricao_lower = descricao.lower().strip()

    # Stage 1: Regex (grátis, cobre 70% dos casos)
    for categoria, config in REGRAS_CATEGORIAS.items():
        if any(kw in descricao_lower for kw in config["keywords"]):
            return {
                "categoria": categoria,
                "dedutivel": config["dedutivel"],
                "metodo": "regex",
                "confianca": 1.0,
                "ficha_dirpf": config.get("ficha_dirpf"),
                "limite": config.get("limite"),
                "valor": valor,
            }

    # Stage 2: XGBoost com MCC code + features textuais (modelo local)
    if mcc_code:
        pred = MODELO_ML.predict_proba([descricao_lower, mcc_code, valor])
        if pred.max() >= 0.85:
            categoria = LABELS[pred.argmax()]
            return {
                "categoria": categoria,
                "dedutivel": REGRAS_CATEGORIAS.get(categoria, {}).get("dedutivel", False),
                "metodo": "ml",
                "confianca": float(pred.max()),
                "valor": valor,
            }

    # Stage 3: Fallback Claude Haiku (casos ambíguos, ~10%)
    return _categorizar_com_claude_haiku(descricao, valor)


def _categorizar_com_claude_haiku(descricao: str, valor: float) -> dict:
    """Usa Claude Haiku para categorizar transações ambíguas. Custo: ~$0.0001/transação."""
    import anthropic

    client = anthropic.Anthropic()

    # IMPORTANTE: nunca enviar dados pessoais — apenas a descrição da transação
    prompt = f"""Você é um especialista em tributação brasileira.
Classifique esta transação bancária para fins de IRPF:

Descrição: "{descricao}"
Valor: R$ {valor:.2f}

Responda em JSON com:
- categoria: (saude|educacao|previdencia|pensao|investimento|outros)
- dedutivel: (true|false)
- motivo: (breve explicação — máx 20 palavras)
- ficha_dirpf: (ficha da DIRPF, se dedutível)

Considere apenas a legislação brasileira vigente (IRPF 2026)."""

    resp = client.messages.create(
        model="claude-haiku-4-5-20251001",
        max_tokens=200,
        messages=[{"role": "user", "content": prompt}]
    )

    import json
    resultado = json.loads(resp.content[0].text)
    resultado["metodo"] = "llm"
    resultado["confianca"] = 0.75
    resultado["valor"] = valor
    return resultado
```

---

### Nível 3 — Chat Tributário com Claude Sonnet

**O que faz:** Responde perguntas do usuário sobre IR e tributação em linguagem natural. Para o MVP, usa system prompt rico em vez de RAG (mais simples de implementar).

```python
# /app/services/chat_service.py

import anthropic

SYSTEM_PROMPT_TRIBUTARIO = """Você é o GuIA — assistente tributário pessoal para brasileiros.

PERSONA:
- Especialista em IRPF de pessoa física no Brasil
- Tom: amigo que entende de imposto — simples, claro, sem jargão
- Nunca intimida — o Leão não é o vilão, é uma obrigação que pode ser otimizada

REGRAS INEGOCIÁVEIS:
1. NUNCA calcule imposto — diga que o simulador do GuIA faz isso com precisão
2. NUNCA crie um artigo de lei que não existe — se não souber, diga "consulte um contador"
3. SEMPRE responda sobre legislação brasileira vigente (IRPF exercício 2026, ano-calendário 2025)
4. NUNCA sugira evasão fiscal — apenas elisão lícita
5. Quando citar uma regra, diga de onde vem: "Segundo o Art. X da Lei 7.713/88..." ou "A IN RFB nº X define que..."

CONHECIMENTO BASE (IRPF 2026):
- Tabela progressiva: isento até R$ 2.259,20; 7,5% até R$ 2.826,65; 15% até R$ 3.751,05; 22,5% até R$ 4.664,68; 27,5% acima
- Dedução por dependente: R$ 2.275,08/ano
- Limite educação por dependente: R$ 3.561,50/ano
- Saúde: sem limite (médico, dentista, hospital, plano de saúde — COM nota ou recibo)
- PGBL: até 12% da renda bruta tributável
- Desconto simplificado: 20% da renda bruta, máximo R$ 16.754,34

FORMATO DE RESPOSTA:
- Máximo 3 parágrafos curtos
- Se a resposta depende do perfil do usuário, pergunte antes de responder
- Termine com: "Quer que eu simule o impacto exato no seu caso? Use o simulador do GuIA →"
"""

def enviar_mensagem(
    historico: list[dict],
    nova_mensagem: str,
    perfil_usuario: dict = None
) -> str:
    """
    Envia mensagem ao chat tributário.
    historico: lista de mensagens anteriores [{role, content}]
    perfil_usuario: dados do perfil para contexto (NUNCA CPF ou dados pessoais)
    """
    client = anthropic.Anthropic()

    # Contexto do perfil (sem dados sensíveis)
    contexto_perfil = ""
    if perfil_usuario:
        contexto_perfil = f"""
Perfil do usuário (use para personalizar a resposta):
- Fonte de renda: {perfil_usuario.get("fonte_renda", "não informado")}
- Tem dependentes: {perfil_usuario.get("tem_dependentes", False)}
- Tem investimentos: {perfil_usuario.get("tem_investimentos", False)}
"""

    system = SYSTEM_PROMPT_TRIBUTARIO + contexto_perfil

    # Masking de dados sensíveis antes de enviar ao LLM
    nova_mensagem_segura = _mascarar_dados_sensiveis(nova_mensagem)

    messages = historico + [{"role": "user", "content": nova_mensagem_segura}]

    resp = client.messages.create(
        model="claude-sonnet-4-6",  # modelo mais capaz para raciocínio jurídico
        max_tokens=500,
        system=system,
        messages=messages
    )

    return resp.content[0].text


def _mascarar_dados_sensiveis(texto: str) -> str:
    """Remove CPF, CNPJ e valores específicos antes de enviar ao LLM."""
    import re
    # CPF: 000.000.000-00
    texto = re.sub(r'\d{3}\.\d{3}\.\d{3}-\d{2}', '[CPF]', texto)
    # CNPJ: 00.000.000/0000-00
    texto = re.sub(r'\d{2}\.\d{3}\.\d{3}/\d{4}-\d{2}', '[CNPJ]', texto)
    return texto
```

---

### Nível 4 — RAG (V1, não no MVP)

**O que faz:** Fundamenta as respostas do chat em documentos oficiais (IN RFB, CARF, Perguntão IRPF).

```python
# /app/services/rag_service.py  ← implementar na V1

# Documentos a indexar:
FONTES_RAG = [
    "Perguntão IRPF 2026 (RFB)",           # ~400 perguntas e respostas oficiais
    "IN RFB nº 1.500/2014 (declaração)",   # regras gerais do IRPF
    "IN RFB nº 2.180/2024 (cripto)",       # tributação de criptoativos
    "IN RFB nº 1.888/2019 (exterior)",     # bens e direitos no exterior
    "Soluções de Consulta CARF relevantes",
]

# Stack:
# - pgvector (extensão PostgreSQL — sem custo adicional de infra)
# - text-embedding-3-small (OpenAI) — R$ 0,002/1M tokens (muito barato)
# - LangChain para orquestrar retrieval + generation
# - Reranker cross-encoder para melhorar precisão dos chunks recuperados
```

---

## 3. Open Finance — Integração com Pluggy

### Fluxo completo de conexão bancária

```
FRONTEND (React)                    BACKEND (FastAPI)               PLUGGY API
      │                                    │                              │
      │ 1. POST /open-finance/token        │                              │
      │ ─────────────────────────────────► │                              │
      │                                    │ 2. POST /items/token         │
      │                                    │ ─────────────────────────────►
      │                                    │ ◄─────────────────────────────
      │ 3. connect_token                   │ connect_token                │
      │ ◄─────────────────────────────── │                              │
      │                                    │                              │
      │ 4. Pluggy Widget (abre modal)       │                              │
      │ [Usuário seleciona banco e autentica via Open Finance]            │
      │                                    │                              │
      │ 5. item_id (webhook)               │                              │
      │ ─────────────────────────────────► │                              │
      │                                    │ 6. GET /items/{item_id}      │
      │                                    │ ─────────────────────────────►
      │                                    │ ◄─────────────────────────────
      │                                    │ 7. GET /transactions         │
      │                                    │ ─────────────────────────────►
      │                                    │ ◄─────────────────────────────
      │                                    │                              │
      │                                    │ 8. Categorizar cada transação │
      │                                    │    (pipeline L2 acima)       │
      │                                    │                              │
      │ 9. Dashboard com deduções          │                              │
      │ ◄─────────────────────────────── │                              │
```

### Código do backend (FastAPI)

```python
# /app/routers/open_finance.py

from fastapi import APIRouter, Depends, HTTPException
from pluggy import PluggyClient
from app.services.categorizer import categorizar_transacao
from app.services.lgpd import mascarar_dado_bruto

router = APIRouter(prefix="/open-finance", tags=["open-finance"])

pluggy_client = PluggyClient(client_id=PLUGGY_CLIENT_ID, client_secret=PLUGGY_CLIENT_SECRET)

@router.post("/connect-token")
async def criar_connect_token(usuario_id: str, current_user = Depends(get_current_user)):
    """Gera connect_token para abrir o Pluggy Widget no frontend."""
    token = await pluggy_client.create_connect_token(
        client_user_id=usuario_id,
        webhook_url=f"{BASE_URL}/webhooks/pluggy",
    )
    return {"connect_token": token}

@router.post("/webhook")
async def processar_webhook_pluggy(payload: dict):
    """Recebe notificação do Pluggy quando conta é conectada."""
    if payload.get("event") == "item/created":
        item_id = payload["data"]["itemId"]
        await importar_transacoes(item_id)
    return {"ok": True}

async def importar_transacoes(item_id: str):
    """Importa e categoriza transações. Nunca persiste dado bruto."""
    transacoes = await pluggy_client.fetch_transactions(item_id, days=365)

    transacoes_processadas = []
    for t in transacoes:
        # Categorizar (L2 — regex + ML + LLM)
        categoria = categorizar_transacao(
            descricao=t["description"],
            valor=t["amount"],
            mcc_code=t.get("merchantCategoryCode")
        )

        # LGPD: NUNCA salvar o dado bruto — apenas a categorização
        transacoes_processadas.append({
            "data": t["date"],
            "descricao_resumida": t["description"][:50],  # truncar
            "valor": t["amount"],
            "categoria": categoria["categoria"],
            "dedutivel": categoria["dedutivel"],
            "ficha_dirpf": categoria.get("ficha_dirpf"),
            # SEM: número de conta, agência, dados bancários completos
        })

    await db.salvar_transacoes(transacoes_processadas)
```

---

## 4. OCR de Documentos

```python
# /app/services/ocr_service.py

import boto3
from anthropic import Anthropic

textract = boto3.client("textract", region_name="sa-east-1")  # Brasil
claude = Anthropic()

def extrair_informe_rendimento(arquivo_bytes: bytes) -> dict:
    """
    Extrai dados de informe de rendimento (PDF/imagem).
    Stage 1: AWS Textract → Stage 2 (fallback): Claude Vision
    """
    # Stage 1: AWS Textract (mais preciso para documentos estruturados)
    try:
        resp = textract.detect_document_text(Document={"Bytes": arquivo_bytes})
        texto_extraido = " ".join(
            b["Text"] for b in resp["Blocks"] if b["BlockType"] == "LINE"
        )
        resultado = _parsear_informe(texto_extraido)
        if resultado["confianca"] >= 0.9:
            return resultado
    except Exception:
        pass

    # Stage 2: Claude Vision como fallback (documentos complexos/manuscritos)
    return _extrair_com_claude_vision(arquivo_bytes)


def _extrair_com_claude_vision(arquivo_bytes: bytes) -> dict:
    """Usa Claude Vision para documentos que Textract não conseguiu ler bem."""
    import base64
    imagem_b64 = base64.standard_b64encode(arquivo_bytes).decode("utf-8")

    resp = claude.messages.create(
        model="claude-sonnet-4-6",
        max_tokens=500,
        messages=[{
            "role": "user",
            "content": [
                {
                    "type": "image",
                    "source": {"type": "base64", "media_type": "image/jpeg", "data": imagem_b64}
                },
                {
                    "type": "text",
                    "text": """Extraia os dados deste informe de rendimentos brasileiro.
Retorne JSON com:
- cnpj_fonte_pagadora
- nome_fonte_pagadora
- rendimentos_tributaveis
- ir_retido_na_fonte
- decimo_terceiro_salario (se houver)
- inss_retido (se houver)

Se algum campo não estiver visível, coloque null."""
                }
            ]
        }]
    )

    import json
    dados = json.loads(resp.content[0].text)
    dados["metodo"] = "claude_vision"
    dados["confianca"] = 0.85
    return dados
```

---

## 5. Stack Completa do MVP

### Backend

```
guia-backend/
├── app/
│   ├── main.py                    # FastAPI entry point
│   ├── routers/
│   │   ├── auth.py                # JWT + OAuth Gov.br
│   │   ├── open_finance.py        # Pluggy integration
│   │   ├── transactions.py        # CRUD transações
│   │   ├── ir_calculator.py       # Rules Engine IRPF
│   │   ├── chat.py                # Claude Sonnet chat
│   │   ├── ocr.py                 # Textract + Claude Vision
│   │   └── dashboard.py           # Dados do dashboard
│   ├── services/
│   │   ├── categorizer.py         # Pipeline L2 (regex+ML+LLM)
│   │   ├── ir_rules.py            # L1 Rules Engine
│   │   ├── chat_service.py        # L3 Claude Sonnet
│   │   ├── ocr_service.py         # OCR pipeline
│   │   ├── pluggy_service.py      # Pluggy SDK wrapper
│   │   └── lgpd.py               # Masking, minimização
│   ├── models/                    # SQLAlchemy models
│   └── schemas/                   # Pydantic schemas (validação)
├── requirements.txt
└── docker-compose.yml
```

### Tecnologias principais

| Camada | Tecnologia | Custo estimado MVP |
|--------|-----------|-------------------|
| **Linguagem** | Python 3.12 | — |
| **Framework API** | FastAPI | Grátis |
| **Banco de dados** | PostgreSQL 16 | ~R$ 50/mês (RDS small) |
| **Open Finance** | Pluggy SDK | ~R$ 2.500/mês (produção) |
| **IA — Chat** | Anthropic Claude Sonnet | ~R$ 100–300/mês |
| **IA — Categorização** | Claude Haiku (fallback) | ~R$ 20–50/mês |
| **OCR** | AWS Textract | ~R$ 30/1.000 docs |
| **Infra cloud** | AWS (sa-east-1 — Brasil) | ~R$ 200/mês |
| **Auth** | JWT + Gov.br OAuth | Grátis |
| **Notificações** | Firebase Cloud Messaging | Grátis |
| **Pagamento** | Stripe / Pagar.me | 2,5% por transação |

**Total MVP (primeiros 1.000 usuários):** ~R$ 3.200–3.800/mês
**Com crescimento:** custo por usuário cai linearmente; Pluggy é o maior custo fixo inicial.

### Frontend Web (React + TypeScript)

```
guia-frontend/
├── src/
│   ├── pages/
│   │   ├── Onboarding/      # simulador de economia
│   │   ├── Dashboard/       # home — deduções + restituição
│   │   ├── Contas/          # Pluggy widget + contas conectadas
│   │   ├── Transacoes/      # lista com badge DEDUTÍVEL
│   │   ├── Chat/            # chat tributário com Claude
│   │   ├── IR/              # declaração guiada
│   │   └── Documentos/      # cofre + OCR
│   └── components/
│       ├── PluggyConnect.tsx # widget de conexão bancária
│       ├── TransactionBadge/ # badge DEDUTÍVEL / Não dedutível
│       ├── RestituicaoCard/  # estimativa em tempo real
│       └── ChatBubble/       # interface do chat
```

### App iOS/Android (React Native)

React Native reutiliza ~80% do código do frontend web. Diferencial: câmera nativa para OCR de documentos.

```
guia-mobile/
├── src/
│   ├── screens/          # mesmas pages do web
│   ├── components/       # mesmos componentes adaptados
│   └── native/
│       └── CameraOCR.tsx # câmera → Textract → dados extraídos
```

---

## 6. Segurança e LGPD no Código

### Regras que nunca podem ser violadas

```python
# /app/services/lgpd.py

# REGRA 1: Dados brutos de extrato nunca persistem
def salvar_transacao(t: dict) -> dict:
    return {
        "data": t["date"],
        "descricao_resumida": t["description"][:50],  # truncar — sem info identificável
        "valor": t["amount"],
        "categoria": t["categoria"],
        "dedutivel": t["dedutivel"],
        # PROIBIDO: numero_conta, agencia, nome_titular, cpf
    }

# REGRA 2: Masking antes de qualquer chamada ao LLM
def mascarar_para_llm(texto: str) -> str:
    import re
    texto = re.sub(r'\d{3}\.\d{3}\.\d{3}-\d{2}', '[CPF]', texto)
    texto = re.sub(r'\d{2}\.\d{3}\.\d{3}/\d{4}-\d{2}', '[CNPJ]', texto)
    return texto

# REGRA 3: Declaração cifrada com chave derivada da senha do usuário
from cryptography.fernet import Fernet
import hashlib

def cifrar_declaracao(dados_ir: dict, senha_usuario: str) -> bytes:
    chave = hashlib.sha256(senha_usuario.encode()).digest()
    f = Fernet(base64.urlsafe_b64encode(chave))
    return f.encrypt(json.dumps(dados_ir).encode())

# REGRA 4: TLS 1.3 obrigatório — configuração nginx
# ssl_protocols TLSv1.3;
# ssl_prefer_server_ciphers off;
```

---

## 7. Como Fazer o MVP em 8 Semanas

| Semana | Entrega | Responsável |
|--------|---------|------------|
| S1 | Setup infra: FastAPI + PostgreSQL + Docker | Dev 1 |
| S1 | Design Figma: onboarding + dashboard + chat | Designer |
| S2 | Rules Engine IRPF (tabelas 2026, simulador) | Dev 1 |
| S2 | Frontend: onboarding + simulador | Dev 2 |
| S3 | Integração Pluggy (connect token + webhook) | Dev 1 |
| S3 | Categorizador L2 (regex + regras IR) | Dev 1 |
| S4 | Dashboard frontend (transações + badge DEDUTÍVEL) | Dev 2 |
| S4 | Chat Claude Sonnet (backend + frontend) | Dev 1 |
| S5 | OCR Textract + Claude Vision (backend) | Dev 1 |
| S5 | Tela de documentos (frontend) | Dev 2 |
| S6 | Auth JWT + Gov.br OAuth | Dev 1 |
| S6 | Stripe/Pagar.me (pagamento assinatura) | Dev 2 |
| S7 | LGPD: masking, consentimento Open Finance, política | Dev 1 + Jurídico |
| S7 | Testes com 10 beta testers reais | Todos |
| S8 | Ajustes do beta + hardening de segurança | Dev 1 + Dev 2 |
| **S8** | **MVP pronto para lançamento** | ✅ |

---

## 8. Variáveis de Ambiente (nunca versionar)

```bash
# .env (nunca commitado — usar AWS Secrets Manager em produção)

# Anthropic Claude API
ANTHROPIC_API_KEY=sk-ant-...

# Pluggy Open Finance
PLUGGY_CLIENT_ID=...
PLUGGY_CLIENT_SECRET=...

# AWS (OCR + infra)
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
AWS_REGION=sa-east-1

# Banco de dados
DATABASE_URL=postgresql://guia:senha@localhost:5432/guia_db

# JWT
JWT_SECRET_KEY=...
JWT_ALGORITHM=HS256
JWT_EXPIRE_MINUTES=10080  # 7 dias

# Pagamento
STRIPE_SECRET_KEY=sk_live_...
# ou
PAGARME_API_KEY=ak_live_...

# Firebase (push notifications)
FIREBASE_PROJECT_ID=...
FIREBASE_PRIVATE_KEY=...
```

---

## 9. Custos de IA Detalhados

### Anthropic Claude (preços de referência — verificar em console.anthropic.com)

| Modelo | Input | Output | Caso de uso no GuIA |
|--------|-------|--------|---------------------|
| `claude-haiku-4-5` | ~$0,80/M tokens | ~$4/M tokens | Categorização de transações (batch) |
| `claude-sonnet-4-6` | ~$3/M tokens | ~$15/M tokens | Chat tributário com usuário |

**Estimativa de consumo por usuário ativo/mês:**
- Categorização: ~200 transações × 200 tokens = 40k tokens → $0,032 (Haiku)
- Chat: ~5 perguntas × 800 tokens = 4k tokens → $0,072 (Sonnet)
- OCR (Claude Vision fallback, 20% dos docs): ~500 tokens/doc → $0,0075/doc

**Custo total de IA para 1.000 usuários ativos:** ~R$ 250–400/mês

### Redução de custo conforme crescimento
- Cache de categorizações: transações do mesmo estabelecimento = custo zero (regex)
- Fine-tuning futuro: modelo próprio treinado em transações brasileiras reduz dependência do LLM
- Plano Pro/Premium inclui mais perguntas ao chat → margem contribui para cobrir custo de API

---

## Status do Documento

| # | Seção | Status |
|---|-------|--------|
| 1 | Visão Geral MVP | ✅ |
| 2 | 4 Níveis de IA (código) | ✅ |
| 3 | Open Finance + Pluggy + Mercado Pago | ✅ |
| 4 | OCR (Textract + Claude Vision) | ✅ |
| 5 | Stack completa (backend + frontend + mobile) | ✅ |
| 6 | Segurança e LGPD no código | ✅ |
| 7 | Cronograma 8 semanas | ✅ |
| 8 | Variáveis de ambiente | ✅ |
| 9 | Custos de IA detalhados | ✅ |
