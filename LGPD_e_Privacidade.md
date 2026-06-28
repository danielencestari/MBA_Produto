# GuIA — Política de Privacidade e Conformidade LGPD
**MBA Tera · Liderança e Estratégia de Produtos Digitais na Era da IA**
**Documento transversal — aplicável a todos os módulos**
**Produzido em:** Junho 2026

---

## Por que LGPD é crítico para o GuIA

O GuIA trata três categorias de dados que combinadas representam o maior grau de sensibilidade possível para uma pessoa física:

| Tipo de dado | Exemplos no GuIA | Risco se vazado |
|-------------|-----------------|----------------|
| **Dados de identificação** | CPF, nome, data de nascimento, endereço | Fraude, roubo de identidade |
| **Dados financeiros bancários** | Extratos, saldo, movimentações via Open Finance | Fraude financeira, chantagem |
| **Dados fiscais e patrimoniais** | Renda, bens, investimentos, declaração de IR | Exposição de patrimônio, fraude fiscal |
| **Dados de comportamento financeiro** | Gastos mensais, padrão de consumo, dívidas | Discriminação, oferta predatória |

Combinados, esses dados formam o **perfil financeiro completo de uma pessoa** — o ativo mais sensível que existe além de dados de saúde.

---

## 1. Bases Legais de Tratamento (Art. 7º e Art. 11 LGPD)

### 1.1 Classificação dos dados do GuIA

A LGPD define "dados sensíveis" (Art. 5º, II) como: racial/étnico, religioso, político, sindical, saúde/vida sexual, genético/biométrico. **Dados financeiros não são legalmente "sensíveis" sob a LGPD** — mas exigem base legal sólida e medidas de segurança equivalentes.

Para dados bancários via Open Finance, a regulação específica é a **Resolução Conjunta BCB/CMN nº 1/2020** e a **Resolução BCB nº 86/2021**, que definem requisitos de consentimento e uso dos dados além da LGPD.

### 1.2 Bases legais utilizadas pelo GuIA

| Dado | Base legal LGPD | Fundamento |
|------|----------------|-----------|
| Dados de cadastro (CPF, e-mail, nome) | Art. 7º, I — Consentimento | Usuário aceita os Termos no cadastro |
| Dados do simulador (renda aproximada, perfil) | Art. 7º, I — Consentimento | Dados informados voluntariamente para receber estimativa |
| Dados bancários via Open Finance | Art. 7º, I — Consentimento **específico, granular e revogável** | Exigência da Resolução BCB nº 86/2021 — consentimento separado por tipo de dado e instituição |
| Dados de documentos (OCR de recibos, informes) | Art. 7º, I — Consentimento | Usuário envia ativamente o documento |
| Dados para cálculo do IR | Art. 7º, V — Execução de contrato | Necessário para entregar o serviço contratado |
| Dados para melhoria do modelo de IA | Art. 7º, IX — Legítimo interesse | Mediante opt-in explícito; usuário pode recusar sem perder o serviço |
| Comunicações de marketing | Art. 7º, I — Consentimento | Opt-in explícito separado do cadastro |

> **Regra prática:** nunca usar "legítimo interesse" para dados bancários ou fiscais. Para esses dados, apenas consentimento explícito é defensável.

---

## 2. Mapeamento de Dados (ROPA — Records of Processing Activities)

> Exigido pelo Art. 37 LGPD e pelo Art. 13 da Resolução BCB nº 86/2021 para Open Finance

| Dado | Finalidade | Base legal | Retenção | Compartilhamento | Risco |
|------|-----------|-----------|---------|-----------------|-------|
| CPF + nome + e-mail | Identificação e autenticação | Consentimento | Enquanto conta ativa + 5 anos | Nenhum (interno) | Médio |
| Senha (hash bcrypt) | Autenticação | Execução de contrato | Enquanto conta ativa | Nenhum | Alto se armazenada em plain text |
| Renda e perfil fiscal (simulador) | Calcular estimativa de economia | Consentimento | 1 ano ou até revogação | Nenhum | Médio |
| Extratos bancários (Open Finance) | Categorizar gastos dedutíveis | Consentimento Open Finance | 12 meses ou até revogação do consentimento | Nenhum — Pluggy acessa, não armazenamos dados brutos além do necessário | Altíssimo |
| Categorização de transações | Identificar deduções de IR | Execução de contrato | Mesmo período dos extratos | Nenhum | Médio |
| Documentos enviados (PDFs, fotos) | OCR e análise para declaração | Consentimento | 5 anos (prazo legal IRPF) | Nenhum | Alto |
| Declaração de IR completa | Preenchimento e envio à RFB | Execução de contrato | 5 anos (prazo prescrição tributária) | Receita Federal (via transmissão pelo usuário) | Altíssimo |
| Dados de investimentos (B3/corretoras) | Calcular DARF e ganho de capital | Consentimento Open Finance | 5 anos | Nenhum | Alto |
| Logs de uso do app | Segurança e debugging | Legítimo interesse | 90 dias | Nenhum | Baixo (com masking de PII) |
| Perguntas ao chat de IA | Melhorar o modelo | Legítimo interesse (opt-in) | 180 dias | Fornecedor de LLM (via API — sem armazenamento pelo fornecedor) | Médio |

---

## 3. Direitos dos Titulares (Art. 18 LGPD)

O GuIA deve implementar todos os direitos de forma **self-service no app**, com prazo de resposta de **15 dias úteis**:

| Direito | Como implementar no GuIA | Prazo |
|--------|------------------------|-------|
| **Confirmação de tratamento** | Seção "Meus Dados" no app — lista todos os dados armazenados | Imediato (automático) |
| **Acesso aos dados** | Download completo dos dados em formato JSON/CSV | ≤ 15 dias úteis |
| **Correção** | Edição de dados cadastrais e perfil fiscal diretamente no app | Imediato |
| **Anonimização / bloqueio / eliminação** | "Excluir minha conta" — apaga todos os dados pessoais (exceto obrigações legais) | ≤ 15 dias úteis |
| **Portabilidade** | Export dos dados estruturados para outro serviço (JSON padrão aberto) | ≤ 15 dias úteis |
| **Informação sobre compartilhamento** | Lista de todos os terceiros que recebem dados (apenas Pluggy/B3 para conexão) | Imediato (na política de privacidade) |
| **Revogação do consentimento** | Botão "Revogar acesso bancário" por instituição (Open Finance) + "Revogar todos os consentimentos" | Imediato |
| **Oposição** | Possibilidade de recusar tratamento por legítimo interesse (marketing, melhoria de IA) | Imediato |

> **Atenção Open Finance:** A Resolução BCB nº 86/2021 exige que o usuário possa revogar o consentimento bancário a qualquer momento, com efeito imediato na coleta (mas não apaga dados já coletados dentro do prazo legal).

---

## 4. Medidas de Segurança Técnicas (Art. 46 LGPD)

### 4.1 Criptografia e proteção de dados

| Camada | Medida | Tecnologia |
|--------|--------|-----------|
| **Dados em repouso** | Criptografia AES-256 para todos os dados sensíveis | AWS KMS / GCP Cloud KMS |
| **Dados em trânsito** | TLS 1.3 obrigatório — sem fallback para versões anteriores | Nginx / CloudFlare |
| **Senhas** | Hash com bcrypt (custo ≥ 12) — nunca armazenar em plain text | bcrypt |
| **CPF e dados de identificação** | Masking parcial em logs (CPF: `***.123.456-**`) | Middleware de log |
| **Tokens Open Finance** | Armazenados criptografados; nunca em logs | Vault (HashiCorp) ou AWS Secrets Manager |
| **Extratos bancários** | Armazenamento mínimo — processar e descartar dados brutos; guardar apenas categorização | Política de minimização |
| **Declaração de IR** | Cifrada por chave derivada do usuário — nem a GuIA consegue ler sem autenticação | Criptografia ponta a ponta com chave do usuário |
| **Backups** | Cifrados e em região diferente do primário | AWS S3 com SSE-KMS |

### 4.2 Controle de acesso

| Controle | Implementação |
|---------|--------------|
| **Princípio do menor privilégio** | Cada microserviço acessa apenas os dados que precisa — sem acesso global |
| **MFA obrigatório para equipe interna** | TOTP obrigatório para todos os acessos a dados de produção |
| **Acesso a dados de produção** | Logs de auditoria de todos os acessos; aprovação de segundo nível para dados sensíveis |
| **Segregação de ambientes** | Dev, Staging e Prod completamente isolados — dados reais só em Prod |
| **Dados de teste** | Dados sintéticos em Dev/Staging — nunca usar dados reais de usuários |
| **Zero Trust** | Autenticação obrigatória entre serviços internos (mTLS) |

### 4.3 Gestão de incidentes (Art. 48 LGPD)

| Etapa | Ação | Prazo |
|-------|------|-------|
| Detecção | Alertas automáticos de anomalia (acesso incomum, volume anômalo de queries) | Imediato |
| Contenção | Isolar sistemas afetados; revogar tokens comprometidos | ≤ 2 horas |
| Avaliação | Determinar escopo, dados afetados, número de titulares | ≤ 24 horas |
| Notificação à ANPD | Comunicar incidentes que possam acarretar risco ou dano relevante | **≤ 72 horas** (Art. 48, §1º) |
| Notificação aos titulares | Comunicar usuários afetados com linguagem clara | ≤ 72 horas da ciência |
| Relatório pós-incidente | Causa raiz, medidas tomadas, plano de prevenção | ≤ 30 dias |

---

## 5. Consentimento Open Finance — Fluxo Detalhado

O Open Finance exige um fluxo de consentimento específico, regulado pela Resolução BCB nº 86/2021. É diferente do consentimento LGPD padrão.

### 5.1 Requisitos do consentimento Open Finance

| Requisito | Implementação no GuIA |
|----------|----------------------|
| **Específico por dado** | O usuário escolhe o que compartilha: saldo ✓ · extrato ✓ · investimentos ✓/✗ · crédito ✓/✗ |
| **Específico por instituição** | Consentimento separado para cada banco (Nubank, Itaú, etc.) |
| **Prazo máximo** | 12 meses — após isso, usuário precisa renovar |
| **Revogável a qualquer momento** | Botão "Revogar acesso" por instituição no app, com efeito imediato |
| **Finalidade declarada** | "Identificar despesas dedutíveis no IR e monitorar gastos para planejamento financeiro" |
| **Linguagem simples** | Proibido juridiquês — explicar em linguagem clara o que será acessado e por quê |
| **Registro do consentimento** | Guardar: data, hora, IP, versão do termo, escopo aprovado, instituição |

### 5.2 Tela de consentimento no GuIA (requisitos de UX)

```
┌─────────────────────────────────────────────────────┐
│  Conectar sua conta no Nubank                        │
│                                                      │
│  O GuIA vai acessar:                                 │
│  ✅ Extrato dos últimos 12 meses                     │
│  ✅ Saldo das contas                                 │
│  ☐  Dados de crédito (cartão, empréstimos)          │
│  ☐  Dados de investimentos                          │
│                                                      │
│  Para que?                                           │
│  Identificar automaticamente quais gastos você       │
│  pode deduzir no seu IR — sem precisar guardar       │
│  comprovantes manualmente.                           │
│                                                      │
│  Por quanto tempo?                                   │
│  12 meses — você pode revogar a qualquer momento     │
│  em Configurações > Contas conectadas.               │
│                                                      │
│  Seus dados nunca serão vendidos ou usados           │
│  para publicidade.                                   │
│                                                      │
│  [Saiba mais]        [Cancelar]  [Conectar →]        │
└─────────────────────────────────────────────────────┘
```

---

## 6. DPIA — Data Protection Impact Assessment

> Exigida pelo Art. 38 LGPD para tratamentos de alto risco. Dados bancários e fiscais se enquadram.

### 6.1 Avaliação de risco

| Fator de risco | Avaliação | Mitigação |
|---------------|----------|-----------|
| Volume de dados sensíveis | **Alto** — extratos bancários completos + declaração IR | Minimização: processar e descartar dado bruto; armazenar apenas categorização |
| Escala de titulares | **Alto** — potencialmente milhões de usuários | Segmentação de ambientes; rotação de chaves por cohort |
| Natureza dos dados (financeiros) | **Alto** — perda de controle pode causar dano econômico real | Criptografia E2E; zero-knowledge para declarações |
| Transferência internacional | **Médio** — LLMs externos (OpenAI/Anthropic) processam perguntas | Nunca enviar dados brutos ao LLM; masking antes de enviar; usar modelos on-premise quando possível |
| Perfilamento automatizado | **Médio** — categorização automática de gastos | Direito de contestar a categorização; sem decisão automatizada com efeito legal |
| Dados de menores (dependentes) | **Médio** — IR de dependentes pode incluir dados de filhos | Dados mínimos; finalidade estrita de cálculo tributário |

### 6.2 Medidas determinadas pela DPIA

1. **Minimização radical de dados bancários:** o backend GuIA nunca armazena o extrato bruto. Pluggy retorna as transações, o categorizador processa, e apenas a categoria + valor + data + "dedutível: sim/não" são salvos. O dado bruto é descartado em memória.

2. **Zero-knowledge para declarações:** a declaração completa do IR é cifrada com uma chave derivada da senha do usuário (KDF + bcrypt). O servidor GuIA armazena o ciphertext mas não consegue decifrar sem autenticação do usuário.

3. **Masking obrigatório antes de LLM:** qualquer dado enviado ao LLM (perguntas do chat, descrição de transações) passa por um pipeline de masking que substitui CPF, nome, CNPJ e valores por tokens antes de sair do perímetro GuIA.

4. **Auditoria de acesso:** todo acesso a dados de produção por colaboradores internos é logado com identificação, timestamp, dado acessado e justificativa. Logs retidos por 2 anos.

---

## 7. DPO — Encarregado de Dados (Art. 41 LGPD)

| Item | Requisito |
|------|----------|
| **Obrigatoriedade** | Sim — dado o volume e natureza dos dados tratados |
| **Perfil recomendado** | Advogado com especialização em LGPD/privacidade ou profissional certificado (CIPP/E, CIPM) |
| **Funções** | Ponto de contato com a ANPD; receber reclamações de titulares; orientar equipes sobre LGPD; conduzir DPIAs |
| **Canal público** | E-mail `privacidade@guia.com.br` publicado no app e no site |
| **Alternativa para startup** | DPO as a Service (terceirizado) enquanto o time é pequeno — fornecedores: TozziniFreire, Demarest, startups especializadas |

---

## 8. Política de Retenção e Exclusão de Dados

| Dado | Período de retenção | Fundamento legal |
|------|--------------------|--------------------|
| Cadastro e dados de conta | Enquanto ativo + 5 anos após encerramento | Art. 12 CDC; potencial ação de consumidor |
| Extratos bancários (categorias) | 5 anos | Art. 173 CTN — prazo prescricional tributário |
| Declarações de IR completas | 5 anos | Art. 173 CTN — Receita Federal pode questionar em até 5 anos |
| Documentos enviados (recibos, PDFs) | 5 anos | Mesmo fundamento tributário |
| Logs de acesso e segurança | 2 anos | Resolução BCB nº 86/2021 (Open Finance) |
| Consentimentos registrados | 5 anos após revogação | Prova de consentimento válido |
| Dados de marketing (opt-in) | Até revogação + 2 anos | Prova de consentimento |
| Dados descartados por minimização (extratos brutos) | **Imediato** — nunca persistido | Princípio da minimização (Art. 6º, III LGPD) |

### Processo de exclusão ("direito ao esquecimento")

```
Usuário solicita exclusão
        ↓
GuIA verifica obrigações legais de retenção
(dados tributários retidos por 5 anos mesmo após pedido)
        ↓
Dados não sujeitos à retenção → exclusão imediata
Dados tributários → anonimização (nome/CPF removidos,
dados fiscais mantidos sem identificação)
        ↓
Confirmação ao usuário com o que foi excluído
e o que foi anonimizado e por quê
        ↓
Registro interno do pedido (prova de cumprimento)
```

---

## 9. Transferência Internacional de Dados (Art. 33 LGPD)

O GuIA usa fornecedores de LLM (Anthropic Claude, OpenAI) que processam dados em servidores nos EUA. Isso configura transferência internacional.

| Fornecedor | País | Mecanismo de adequação | Medida adicional |
|-----------|------|----------------------|-----------------|
| Anthropic (Claude) | EUA | Cláusulas contratuais padrão (SCC) | Masking de PII antes de enviar; dados mínimos no prompt |
| OpenAI (fallback) | EUA | SCC + Data Processing Agreement (DPA) | Idem |
| AWS (infraestrutura) | EUA/Brasil (região sa-east-1) | Adequação por ANPD + SCC | Preferir região br para dados em repouso |
| Google Cloud (alternativa) | EUA/Brasil | SCC | Idem |

**Regra prática:** dados brutos de extratos bancários e declarações de IR **nunca saem do Brasil** (armazenados em sa-east-1). Apenas descrições de transações anonimizadas e perguntas mascaradas chegam aos LLMs externos.

---

## 10. Implementação — Checklist de Compliance por Release

> Cada release com novo tratamento de dados deve passar por este checklist antes do deploy

- [ ] ROPA atualizado com os novos dados e finalidades
- [ ] Base legal identificada e documentada
- [ ] Consentimento adequado implementado (se necessário)
- [ ] Masking de PII em todos os novos logs
- [ ] Criptografia em repouso para novos campos sensíveis
- [ ] Direitos dos titulares funcionando para os novos dados
- [ ] DPO informado e aprovação para dados de alto risco
- [ ] DPIA atualizada se o risco aumentar
- [ ] Contratos com novos fornecedores com DPA (Data Processing Agreement)
- [ ] Política de Privacidade atualizada e publicada
- [ ] Time de Suporte treinado para responder perguntas sobre os novos dados

---

## 11. Resumo — Postura de Privacidade do GuIA

| Princípio | Como o GuIA aplica |
|----------|-------------------|
| **Privacy by Design** | Privacidade é requisito de arquitetura — não é adicionada depois |
| **Minimização** | Coletamos o mínimo necessário; descartamos dados brutos imediatamente após processamento |
| **Transparência** | Usuário sabe exatamente o que coletamos, por quê e por quanto tempo |
| **Consentimento granular** | Usuário escolhe o que compartilha — por dado e por instituição |
| **Zero-knowledge para declarações** | Nem a GuIA lê sua declaração sem sua autenticação |
| **Sem venda de dados** | Nunca. Nosso modelo de negócio é assinatura — dados não são o produto |
| **Direito de saída** | Usuário pode exportar tudo e excluir a conta a qualquer momento |
| **Segurança como investimento** | Auditoria de segurança externa semestral; programa de bug bounty |

---

## Status do Documento LGPD

| # | Seção | Status |
|---|-------|--------|
| 1 | Bases legais de tratamento | ✅ Completo |
| 2 | Mapeamento de dados (ROPA) | ✅ Completo |
| 3 | Direitos dos titulares | ✅ Completo |
| 4 | Medidas de segurança técnicas | ✅ Completo |
| 5 | Consentimento Open Finance | ✅ Completo |
| 6 | DPIA | ✅ Completo |
| 7 | DPO | ✅ Completo |
| 8 | Política de retenção | ✅ Completo |
| 9 | Transferência internacional | ✅ Completo |
| 10 | Checklist de compliance por release | ✅ Completo |
