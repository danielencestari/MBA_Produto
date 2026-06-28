# GuIA — Pitch do Produto
**Versão:** Junho 2026

---

## Versão curta — WhatsApp / conversa informal

> **GuIA — Seu copiloto tributário pessoal com IA**
>
> Todo ano, 41 milhões de brasileiros encaram o IR com medo: medo de malha fina, medo de perder deduções, medo de pagar mais do que deveriam. E o problema não é só em abril — ele começa em janeiro, quando você joga fora um recibo de farmácia sem saber que valia R$ 300 de dedução.
>
> O GuIA resolve isso. Conecta suas contas bancárias via Open Finance (Mercado Pago, Nubank, Itaú e 800+ bancos), monitora seus gastos o ano todo, e identifica automaticamente o que pode ser deduzido no IR — sem você guardar um comprovante sequer.
>
> Na hora de declarar, a IA já montou sua declaração. Você só confirma.
>
> **O diferencial:** não é um app de abril. É um assistente financeiro que trabalha 12 meses para que em abril você só precise apertar um botão.
>
> Foco no MVP: IRPF de pessoa física. Open Finance regulado pelo BCB. IA com custo viável — a maior parte roda em regras determinísticas (sem tokens caros); o LLM entra só onde o rule-based não resolve.

---

## Versão completa — apresentação / banca

### O problema

**75% dos 41 milhões de declarantes do IR cometem erros que custam dinheiro** — seja pagando mais imposto do que deveriam, perdendo deduções por falta de organização, ou caindo em malha fina.

O problema não é que as pessoas são descuidadas. É que o IR foi projetado para ser complexo. As deduções existem, são legais, mas ficam espalhadas ao longo de 12 meses: um recibo de médico em março, um plano de saúde em julho, uma escola em dezembro. Quando chega abril, a maioria já perdeu metade.

E as alternativas atuais não resolvem:
- **Portal da Receita Federal** → complexo, só existe em abril, sem sugestão alguma
- **Contador** → R$ 300–800 por declaração, também só em abril
- **Apps pontuais de IR** → fazem a declaração, mas não acompanham o ano todo

---

### A solução — GuIA

**GuIA** (Guia + IA) é um assistente financeiro pessoal com IA para brasileiros. Diferente de todos os concorrentes, é um produto **anual** — não uma ferramenta de abril.

**Como funciona em 3 passos:**

**1. Conecte seus bancos**
Via Open Finance regulado pelo BCB, o GuIA acessa seus extratos com seu consentimento. Funciona com Mercado Pago, Nubank, Itaú, Bradesco, BB, Santander, Inter, C6, XP e 800+ instituições.

**2. A IA monitora e categoriza**
Cada transação bancária recebe um badge automaticamente:
- 🟢 **DEDUTÍVEL** — farmácia, médico, escola, plano de saúde, PGBL
- ⚪ Não dedutível — iFood, Uber, supermercado
- 🟡 Verificar — casos ambíguos, o chat esclarece

**3. Em abril, sua declaração já está pronta**
O Rules Engine calcula o cenário ótimo (modelo completo vs. simplificado), estima sua restituição em tempo real, e guia o preenchimento passo a passo. Você revisa e envia.

---

### Para quem

| Persona | Dor principal | O que o GuIA resolve |
|--------|--------------|---------------------|
| **Clara, 32 — CLT** | Perde deduções de saúde e educação por não guardar comprovantes | Captura tudo automaticamente no extrato bancário |
| **Rafael, 41 — Autônomo/MEI** | Confunde despesas PF e PJ, não sabe quando pagar carnê-leão | Separa automaticamente, gera DARF mensal |
| **Lucas, 28 — Investidor** | Não sabe calcular IR de ações/cripto, paga multa por DARF atrasado | Calcula ganho de capital mês a mês, avisa antes do vencimento |
| **Família Silva — Casal** | Não sabe se declara junto ou separado, perde dedução de dependente | Simula ambos os cenários e recomenda o mais vantajoso |

---

### Como a IA funciona — e por que o custo é viável

O erro mais comum em produtos de IA é jogar tudo no LLM. O GuIA usa quatro camadas:

```
L1 — Rules Engine (Python puro)     → calcula IR, DARF, restituição → custo ZERO
L2 — ML + regex                     → categoriza transações         → custo ZERO / mínimo
L3 — Claude Sonnet (Anthropic)      → chat tributário com usuário   → ~R$ 0,07/conversa
L4 — RAG sobre legislação (V1)      → respostas com citação de IN   → custo moderado
```

**Custo total de IA para 1.000 usuários ativos: ~R$ 300–400/mês.**
O LLM entra só nos ~10% de casos ambíguos e nas perguntas do chat. O resto roda determinístico.

---

### Modelo de negócio

| Tier | Preço | Para quem |
|------|-------|----------|
| **Básico** | Grátis | Declaração simples, 1 fonte de renda |
| **Pro** | R$ 9,90/mês | Múltiplas fontes, Open Finance, simulador |
| **Premium** | R$ 29,90/mês | Investimentos, DARF automático, consultoria |

Receita recorrente (SaaS). LTV alto — quem usa o GuIA uma vez e recebe restituição maior renova no ano seguinte.

**OKRs Ano 1:** 250k usuários · R$ 500k MRR · NPS > 40

---

### O que não fazemos (e por quê)

**Não recomendamos ações ou ativos específicos.** Isso exige habilitação CVM (CGA/CGE). O GuIA pode calcular o impacto tributário de qualquer ativo, simular cenários e explicar regras — mas a decisão de compra é sempre do usuário. Para sugestão de alocação, o caminho é parceria com instituição licenciada — isso entra no roadmap de V2.

---

### Stack técnica do MVP

- **Backend:** Python + FastAPI
- **Open Finance:** Pluggy SDK (200+ instituições, widget de conexão pronto)
- **IA:** Anthropic Claude API (Sonnet para chat, Haiku para categorização)
- **OCR:** AWS Textract + Claude Vision (informes de rendimento, recibos)
- **Banco de dados:** PostgreSQL + pgvector (para RAG na V1)
- **LGPD:** dados bancários brutos nunca persistem; declarações cifradas com chave do usuário
- **Prazo do MVP:** 8 semanas com 2 devs

---

### Por que agora

Três forças convergindo em 2026:
1. **Open Finance Brasil** — 55M usuários ativos, todos os bancos participantes, maior Open Finance do mundo
2. **IA generativa madura** — LLMs em português com qualidade suficiente para raciocínio tributário
3. **Digitalização da Receita Federal** — declaração pré-preenchida, e-CAC, APIs via SERPRO

A janela está aberta antes que bancos ou a própria Receita Federal ocupem esse espaço.

---

> *"Pare de temer o Leão. O GuIA cuida do seu IR o ano todo — não só em abril."*
