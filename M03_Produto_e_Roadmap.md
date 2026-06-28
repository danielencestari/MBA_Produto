# GuIA — Artefatos do Módulo 03
**MBA Tera · Liderança e Estratégia de Produtos Digitais na Era da IA**
**Módulo 03 — Design & Delivery**
**Produzido em:** Junho 2026

> **Escopo:** Brasil exclusivamente. Open Finance regulado pelo BCB. Mercado Pago, Nubank e demais bancos acessíveis via Pluggy.

---

## Artefato 1 — User Story Map

> Framework: User Story Mapping (Jeff Patton)
> Estrutura: Atividade → Tarefa → User Stories (ordenadas por prioridade de entrega)
> Leitura: horizontal = jornada do usuário · vertical = prioridade (cima = MVP, baixo = futuro)

### JORNADA PRINCIPAL

```
ATIVIDADE         │ CADASTRO      │ DIAGNÓSTICO        │ ORGANIZAÇÃO        │ DECLARAÇÃO          │ PÓS-IR
──────────────────┼───────────────┼────────────────────┼────────────────────┼─────────────────────┼──────────────
TAREFA            │ Criar conta   │ Calcular economia  │ Guardar documentos │ Preencher IR        │ Acompanhar restituição
                  │ Configurar    │ Ver deduções       │ Importar dados     │ Revisar e enviar    │ Planejar próximo ano
                  │ perfil fiscal │ elegíveis          │ financeiros        │                     │
──────────────────┼───────────────┼────────────────────┼────────────────────┼─────────────────────┼──────────────
MVP               │ US01 Cadastro │ US04 Simulador     │ US08 Cofre manual  │ US11 Preench. guiado│ US15 Status restituição
                  │ US02 Perfil   │ US05 Lista deduções│ US09 OCR nota      │ US12 Validação erros│ US16 Notif. aprovação
                  │ US03 Fonte de │ US06 Alertas prazo │                    │ US13 Envio Receita  │
                  │ renda         │ US07 Aha moment    │                    │ US14 Declaração PDF │
                  │ US-OF01 Conec.│                    │                    │                     │
                  │ conta bancária│                    │                    │                     │
                  │ (Pluggy)      │                    │                    │                     │
                  │ US-OF02 Import│                    │                    │                     │
                  │ extrato 12m   │                    │                    │                     │
                  │ US-OF03 Badge │                    │                    │                     │
                  │ DEDUTÍVEL     │                    │                    │                     │
                  │ US-OF04 Dash. │                    │                    │                     │
                  │ deduções      │                    │                    │                     │
──────────────────┼───────────────┼────────────────────┼────────────────────┼─────────────────────┼──────────────
V1                │ US17 Login    │ US20 Comparação    │ US22 Open Finance  │ US25 Conjunto vs    │ US27 Conselho
                  │ social        │ ano anterior       │ bancário           │ separado (casal)    │ pós-restituição
                  │ US18 Convite  │ US21 Score         │ US23 Importação    │ US26 Sugestão de    │ US28 Relatório
                  │ familiar      │ tributário         │ corretora          │ regime tributário   │ anual PDF
                  │ US19 2FA      │                    │ US24 Categorização │                     │
──────────────────┼───────────────┼────────────────────┼────────────────────┼─────────────────────┼──────────────
V2                │ US29 SSO      │ US31 IA proativa   │ US33 Sync bancário │ US36 Envio via e-CAC│ US38 Planejamento
                  │ empresa       │ fora de abril      │ contínuo           │ US37 Revisão por    │ tributário 12m
                  │ US30 Perfil   │ US32 DARF          │ US34 Multi-conta   │ contador parceiro   │ US39 Marketplace
                  │ MEI integrado │ automático         │                    │                     │ contadores
```

---

## Artefato 2 — Product Backlog priorizado (RICE)

> RICE Score = (Reach × Impact × Confidence) / Effort
> Reach: usuários/trimestre · Impact: 0,25/0,5/1/2/3 · Confidence: % · Effort: pessoa-semanas

| # | User Story | Reach | Impact | Conf. | Effort | RICE | Release |
|---|-----------|------:|-------:|------:|-------:|-----:|:-------:|
| US07 | Aha moment — exibir economia estimada | 10.000 | 3 | 90% | 1 | **27.000** | MVP |
| US01 | Cadastro e login por e-mail | 10.000 | 2 | 100% | 1 | **20.000** | MVP |
| US06 | Alertas de prazo da Receita Federal | 8.000 | 2 | 90% | 1 | **14.400** | MVP |
| US04 | Simulador de economia no onboarding | 10.000 | 3 | 80% | 2 | **12.000** | MVP |
| US15 | Acompanhar status da restituição | 8.000 | 2 | 80% | 2 | **6.400** | MVP |
| US12 | Validação automática de erros antes de enviar | 8.000 | 3 | 80% | 3 | **6.400** | MVP |
| US05 | Lista de deduções elegíveis por perfil | 8.000 | 3 | 70% | 3 | **5.600** | MVP |
| US13 | Envio da declaração para a Receita Federal | 8.000 | 3 | 70% | 4 | **4.200** | MVP |
| US11 | Preenchimento guiado da declaração | 8.000 | 3 | 70% | 5 | **3.360** | MVP |
| US25 | Simulação declaração conjunta vs. separada | 4.000 | 3 | 80% | 3 | **3.200** | V1 |
| US21 | Score tributário pessoal | 5.000 | 2 | 70% | 3 | **2.333** | V1 |
| US22 | Importação bancária via Open Finance | 6.000 | 3 | 60% | 5 | **2.160** | V1 |
| US09 | OCR de nota fiscal (cofre inteligente) | 6.000 | 2 | 60% | 4 | **1.800** | MVP |
| US32 | DARF automático para investidores | 3.000 | 3 | 60% | 4 | **1.350** | V2 |
| US39 | Marketplace de contadores parceiros | 2.000 | 2 | 50% | 6 | **333** | V2 |
| US-OF01 | Conectar conta bancária via Pluggy (Mercado Pago, Nubank, Itaú e outros) | 10.000 | 3 | 80% | 2 | **12.000** | MVP |
| US-OF02 | Importar extrato automático dos últimos 12 meses | 8.000 | 3 | 80% | 2 | **9.600** | MVP |
| US-OF03 | Badge "DEDUTÍVEL" em cada transação — categorização automática por IA | 8.000 | 3 | 75% | 3 | **6.000** | MVP |
| US-OF04 | Dashboard: total de deduções identificadas automaticamente no extrato | 8.000 | 3 | 75% | 2 | **9.000** | MVP |

---

## Artefato 3 — User Stories com Critérios de Aceite

> Formato: Como [persona] quero [ação] para [benefício]
> Critérios no padrão Given / When / Then (BDD)

---

### US-OF01 — Conectar conta bancária (Open Finance)

**Como** Clara (usuária do GuIA),
**quero** conectar minha conta no Mercado Pago, Nubank ou qualquer outro banco,
**para** que o GuIA importe automaticamente meus gastos e identifique o que posso deduzir no IR sem precisar guardar comprovantes.

```
Given  Clara está autenticada no GuIA e acessa "Minhas Contas"
When   clica em "Conectar conta"
Then   o Pluggy Widget abre com a lista de bancos disponíveis (Mercado Pago, Nubank, Itaú, BB, etc.)
And    o banner explica claramente: "O GuIA vai acessar seu extrato dos últimos 12 meses para identificar deduções de IR"
And    existe botão "Saiba mais" com detalhes sobre LGPD e Open Finance

Given  Clara seleciona "Mercado Pago" e autoriza o acesso
When   o fluxo OAuth do Open Finance é concluído
Then   o GuIA exibe "Conta Mercado Pago conectada com sucesso"
And    o número de transações importadas é exibido em até 30 segundos
And    o status de consentimento (válido por 12 meses, revogável) fica visível

Given  Clara acessa "Minhas transações" após conectar a conta
When   a lista de transações é exibida
Then   cada transação tem um badge colorido: verde "DEDUTÍVEL", cinza "Não dedutível", amarelo "Verificar"
And    o total de deduções identificadas aparece no topo em destaque: "R$ 1.847 dedutíveis encontrados"
```

---

### US07 — Aha Moment

**Como** Clara (primeira vez no GuIA),
**quero** ver quanto dinheiro posso economizar logo no início,
**para** entender imediatamente se vale a pena continuar usando o app.

```
Given  Clara acabou de informar sua renda bruta anual e fonte de renda
When   ela chega à tela de resultado do simulador
Then   o app exibe uma estimativa de economia em R$ (ex.: "Você pode economizar até R$ 2.350")
And    o tempo entre o cadastro e a exibição deste valor é ≤ 120 segundos
And    a estimativa é calculada com base em pelo menos 2 deduções padrão aplicáveis ao seu perfil
And    existe um CTA claro "Ver minhas deduções" e outro "Começar minha declaração"

Given  Clara clica em "Ver minhas deduções"
When   a tela de deduções é exibida
Then   cada dedução listada mostra: nome, valor estimado e por que ela se qualifica
And    existe um ícone de informação explicando a base legal de cada dedução
```

---

### US04 — Simulador de Economia no Onboarding

**Como** qualquer usuário no primeiro acesso,
**quero** responder poucas perguntas sobre minha vida financeira,
**para** receber uma estimativa personalizada de quanto posso economizar em impostos.

```
Given  o usuário está na tela de onboarding
When   ele responde as perguntas obrigatórias do simulador
Then   o formulário tem no máximo 5 campos obrigatórios
And    cada campo tem uma explicação de por que está sendo solicitado

Given  o usuário preenche todos os campos
When   confirma as respostas
Then   o sistema retorna a estimativa em ≤ 3 segundos
And    a estimativa discrimina as principais deduções aplicadas
And    o usuário não precisa criar conta para ver o resultado

Given  o usuário vê o resultado sem estar logado
When   clica em "Salvar meu resultado"
Then   é direcionado para tela de cadastro com o contexto do simulador preservado
And    após cadastro, retorna direto ao resultado (sem precisar refazer o simulador)
```

---

### US05 — Lista de Deduções Elegíveis

**Como** Clara (Assalariada CLT com dependente),
**quero** ver todas as deduções que posso aproveitar na minha declaração,
**para** não deixar passar nenhum benefício fiscal ao qual tenho direito.

```
Given  Clara tem perfil configurado (renda, dependentes, despesas médicas)
When   acessa a seção "Minhas Deduções"
Then   o sistema exibe lista agrupada por categoria (Saúde, Educação, Dependentes, Previdência, Outras)
And    cada item mostra: dedução, valor informado, valor dedutível e status

Given  uma dedução está com status "pendente"
When   Clara clica nela
Then   o app exibe o que falta para aproveitá-la
And    existe opção de adicionar o documento diretamente naquele momento

Given  Clara adiciona um novo gasto de saúde
When   salva o lançamento
Then   o valor total de economia estimada é atualizado em tempo real na tela principal
```

---

### US06 — Alertas de Prazo da Receita Federal

**Como** qualquer usuário,
**quero** receber lembretes automáticos sobre datas importantes do IR,
**para** nunca perder um prazo e evitar multas por atraso.

```
Given  o usuário instalou o app e ativou notificações
When   faltam 30 dias para o prazo de entrega da declaração
Then   o app envia uma notificação push com o prazo exato e CTA "Começar minha declaração"

Given  o usuário ainda não iniciou a declaração quando faltam 7 dias para o prazo
When   abre o app
Then   um banner de urgência vermelho aparece na home com contagem regressiva

Given  o usuário tem DARF a pagar
When   o dia 20 do mês seguinte à venda se aproxima (faltam 5 dias)
Then   o app envia notificação push com o valor do DARF e CTA "Gerar boleto"
```

---

### US09 — OCR de Nota Fiscal

**Como** Rafael (Autônomo),
**quero** fotografar uma nota fiscal de despesa com o celular,
**para** que o app extraia os dados automaticamente sem que eu precise digitar nada.

```
Given  Rafael está na seção "Cofre de Documentos"
When   toca em "Adicionar nota fiscal" e escolhe "Câmera"
Then   a câmera abre com guia de enquadramento para o documento

Given  Rafael fotografa uma nota fiscal legível
When   confirma a foto
Then   o OCR extrai: data, valor, CNPJ do prestador e descrição do serviço em ≤ 5 segundos
And    os dados extraídos são exibidos para confirmação antes de salvar

Given  o OCR não consegue extrair algum campo (confiança < 80%)
When   apresenta o resultado
Then   o campo não identificado fica em branco e destacado em amarelo

Given  Rafael confirma os dados
When   salva o documento
Then   o sistema categoriza automaticamente a despesa
And    o impacto na dedução estimada é atualizado na tela principal
And    o documento original (foto) fica armazenado vinculado ao lançamento
```

---

### US11 — Preenchimento Guiado da Declaração

**Como** Clara (primeira declaração com o GuIA),
**quero** ser guiada passo a passo no preenchimento do IR,
**para** não precisar entender a estrutura complexa do programa da Receita Federal.

```
Given  Clara iniciou o fluxo de declaração
When   está em qualquer etapa do preenchimento
Then   cada seção é apresentada em linguagem simples (não no jargão da Receita)
And    cada campo obrigatório tem uma explicação de onde encontrar a informação
And    existe um indicador de progresso mostrando em qual etapa está

Given  Clara tem dados já importados
When   chega à seção correspondente
Then   os dados importados aparecem pré-preenchidos e destacados como "importados automaticamente"
And    Clara pode editar qualquer valor pré-preenchido

Given  Clara tenta avançar com um campo obrigatório vazio
When   clica em "Próximo"
Then   o campo é destacado com mensagem de erro específica
And    não avança até o campo ser preenchido

Given  Clara completa todas as seções
When   chega na tela de revisão
Then   um resumo completo é exibido agrupado por categoria
And    há indicação clara do valor de restituição OU imposto a pagar
And    o CTA "Enviar para Receita Federal" só é habilitado após confirmação de revisão
```

---

## Artefato 4 — Definition of Ready e Definition of Done

### Definition of Ready (DoR)
*Uma User Story só entra no sprint quando:*

- [ ] Escrita no formato "Como [persona], quero [ação], para [benefício]"
- [ ] Tem critérios de aceite no padrão Given/When/Then
- [ ] Foi estimada pelo time (Story Points ou T-shirt size)
- [ ] Dependências externas estão identificadas (APIs, parceiros, legal)
- [ ] Protótipo ou wireframe aprovado pelo PM (para stories de UI)
- [ ] Conformidade legal verificada (LGPD, legislação tributária) quando aplicável
- [ ] RICE calculado e prioridade validada no backlog

### Definition of Done (DoD)
*Uma User Story só é considerada entregue quando:*

- [ ] Código revisado por pelo menos 1 desenvolvedor (code review aprovado)
- [ ] Testes unitários escritos com cobertura ≥ 80%
- [ ] Testes de aceitação executados e passando
- [ ] Sem vulnerabilidades críticas ou altas no SAST/DAST
- [ ] Dados pessoais e fiscais tratados conforme política LGPD
- [ ] Feature testada em dispositivos iOS e Android (quando aplicável)
- [ ] Deployed em staging e validado pelo PM
- [ ] Documentação de API atualizada (quando aplicável)
- [ ] Analytics/tracking implementado (evento de conversão registrado)

---

## Artefato 5 — Roadmap de Entrega: MVP → V1 → V2

### Premissa de time
1 PM · 2 devs full-stack · 1 designer · 1 especialista tributário (part-time)
Sprint: 2 semanas · Capacidade: ~20 Story Points/sprint

---

### FASE MVP — "Declarar e não sofrer" (Meses 1–4)
**Objetivo:** Usuário consegue fazer a declaração completa do IR com sugestão de deduções e envio para a Receita.
**Critério de saída:** ≥100 declarações enviadas com NPS ≥ 7

| Sprint | Entrega | Stories |
|--------|---------|---------|
| S1–S2 | Cadastro, perfil fiscal, simulador de economia | US01, US02, US03, US04 |
| S3 | Aha moment, lista de deduções, alertas de prazo | US05, US06, US07 |
| S4–S5 | Cofre de documentos (manual + OCR) + Integração Pluggy (Open Finance) — conectar conta, importar extrato, categorização automática (US-OF01 a OF04) | US08, US09, US-OF01, US-OF02, US-OF03, US-OF04 |
| S6–S7 | Preenchimento guiado da declaração | US10, US11, US12 |
| S8 | Envio para Receita, PDF, status de restituição | US13, US14, US15 |
| S9 | Notificação de aprovação + paywall Pro | US16 + monetização |

---

### FASE V1 — "Anual e inteligente" (Meses 5–9)
**Objetivo:** Usuário usa o GuIA o ano todo — não só em abril.
**Critério de saída:** ≥40% dos usuários ativos em mês não-IR (maio–outubro)

| Sprint | Entrega | Stories |
|--------|---------|---------|
| S10–S11 | Login social, convite familiar, 2FA | US17, US18, US19 |
| S12 | Comparação com ano anterior, score tributário | US20, US21 |
| S13–S14 | Importação bancária via Open Finance (movida para MVP — US-OF01 a OF04) + aprofundamento de categorização avançada | US22 |
| S15 | Importação de corretora (B3, XP, NuInvest) | US23, US24 |
| S16 | Simulação conjunto vs. separado, sugestão de regime | US25, US26 |
| S17 | Conselho pós-restituição, relatório anual PDF | US27, US28 |

---

### FASE V2 — "Plataforma tributária" (Meses 10–18)
**Objetivo:** GuIA como hub financeiro-tributário — DARF automático, e-CAC direto, marketplace de contadores.
**Critério de saída:** MRR ≥ R$ 150k · LTV/CAC ≥ 5x

| Sprint | Entrega | Stories |
|--------|---------|---------|
| S18 | SSO empresa (B2B), perfil MEI integrado | US29, US30 |
| S19–S20 | IA proativa fora de abril | US31 |
| S21 | DARF automático para investidores | US32 |
| S22 | Sync bancário contínuo, multi-conta | US33, US34 |
| S23 | Envio direto via e-CAC | US36 |
| S24–S25 | Revisão por contador parceiro, marketplace | US37, US39 |

---

## Artefato 6 — APIs Públicas Úteis para o GuIA

### Bloco 1 — Receita Federal / Governo

| API / Serviço | O que fornece | Como usar no GuIA | Acesso |
|--------------|--------------|-------------------|--------|
| **e-CAC (Portal Gov.br)** | Situação fiscal, pendências, malha fina, declarações anteriores | Pré-preencher campos, alertar sobre pendências | OAuth Gov.br |
| **Consulta CNPJ (Receita Federal)** | Dados cadastrais de empresas por CNPJ | Validar automaticamente CNPJ extraído pelo OCR | Pública — receitaws.com.br |
| **PGFN — Situação de débitos** | Dívidas ativas, parcelamentos em aberto | Alertar usuário sobre débitos antes de declarar | Via e-CAC |
| **NFe/NFCe (SEFAZ)** | Notas fiscais eletrônicas emitidas e recebidas | Importar notas automaticamente sem OCR | Certificado digital A1/A3 |
| **Tabelas IRPF (Receita)** | Tabela progressiva, deduções legais, limites anuais | Base do motor de cálculo tributário | Pública (site RFB) |

### Bloco 2 — Open Finance Brasil (Banco Central)

| API | O que fornece | Como usar no GuIA | Acesso |
|----|--------------|-------------------|--------|
| **Open Finance — Dados de conta** | Extrato, saldo, movimentações bancárias | Categorizar despesas, identificar gastos dedutíveis | OAuth 2.0 com consentimento |
| **Open Finance — Dados de investimentos** | Carteira de renda fixa, fundos, LCI/LCA, Tesouro | Preencher bens e direitos e rendimentos isentos | OAuth 2.0 com consentimento |
| **Open Finance — Dados de crédito** | Empréstimos, financiamentos | Identificar juros pagos (possível dedução) | OAuth 2.0 com consentimento |

> Cobre: Nubank, Itaú, Bradesco, BB, Caixa, Santander, XP, Inter e 100+ instituições.

### Bloco 3 — Mercado de Capitais (Investidores)

| API / Serviço | O que fornece | Como usar no GuIA | Acesso |
|--------------|--------------|-------------------|--------|
| **B3 / CEI (Canal do Investidor)** | Histórico consolidado de todas as corretoras do usuário | Importar todas as operações para o GuIA | OAuth — CPF + senha B3 |
| **CoinGecko / CoinMarketCap** | Histórico de preços de criptomoedas | Calcular ganho de capital em cripto | Pública com API key gratuita |
| **BCB — Taxas de câmbio (PTAX)** | Taxa oficial de câmbio por data | Converter operações em moeda estrangeira | Pública — olinda.bcb.gov.br |

### Bloco 4 — Utilidades e Infraestrutura

| API / Serviço | O que fornece | Como usar no GuIA | Acesso |
|--------------|--------------|-------------------|--------|
| **ViaCEP** | Endereço completo por CEP | Preencher endereço automaticamente no cadastro | Pública — viacep.com.br |
| **Google Vision API / AWS Textract** | OCR de alta precisão em documentos | Extrair dados de notas fiscais e comprovantes | Paga — Textract ~$1,50/1000 páginas |
| **OpenAI API / Anthropic Claude** | Modelo de linguagem para interpretação tributária | Responder dúvidas, interpretar regras da RFB, sugerir deduções | Paga por token |
| **Firebase Cloud Messaging** | Push notifications mobile | Alertas de prazo, DARF, novidades | Gratuita para volume inicial |
| **Stripe / Iugu / Pagar.me** | Pagamento recorrente (assinatura) | Cobrar planos Pro e Premium | ~2,5% por transação |

### Mapa de dependências por fase

```
MVP:
  - e-CAC (pré-preenchimento) ← crítico
  - CNPJ Receita (OCR de notas) ← fácil, gratuito
  - Google Vision / Textract (OCR) ← pago, rápido de integrar
  - ViaCEP (cadastro) ← gratuito
  - Tabela IRPF (motor de cálculo) ← dados públicos, manter atualizado
  - Firebase (push) ← gratuito
  - Stripe/Iugu (pagamento) ← obrigatório para monetização

V1:
  - Open Finance (importação bancária) ← complexo, exige registro no BCB
  - CEI/B3 (importação de investimentos) ← médio, exige auth do usuário

V2:
  - NFe/SEFAZ (notas automáticas) ← requer certificado digital do contribuinte
  - CoinGecko/PTAX (cripto e câmbio) ← relativamente simples
```

---

## Artefato 7 — Descrição de Telas e Funcionalidades

### Tela 1 — Onboarding / Simulador

```
┌─────────────────────────────────────────┐
│  GuIA                           [Entrar] │
│                                          │
│  Quanto você está deixando               │
│  de receber na sua restituição?          │
│                                          │
│  Qual é sua fonte de renda?              │
│  ┌─────────────────────────────────┐    │
│  │ ● CLT (assalariado)             │    │
│  │ ○ Autônomo / MEI                │    │
│  │ ○ Investidor                    │    │
│  │ ○ Misto                         │    │
│  └─────────────────────────────────┘    │
│                                          │
│  Renda bruta anual aproximada?           │
│  ┌─────────────────────────────────┐    │
│  │  R$ ___________________________  │    │
│  └─────────────────────────────────┘    │
│                                          │
│  Tem dependentes?   [Sim]  [Não]         │
│  Plano de saúde?    [Sim]  [Não]         │
│  Despesas médicas?  [Sim]  [Não]         │
│                                          │
│  ┌─────────────────────────────────┐    │
│  │     Calcular minha economia     │    │
│  └─────────────────────────────────┘    │
└─────────────────────────────────────────┘
```

**Resultado — Aha Moment:**
```
┌─────────────────────────────────────────┐
│  ←  Seu resultado                        │
│                                          │
│  💰 Você pode economizar até             │
│                                          │
│         R$ 2.350,00                      │
│      em impostos este ano                │
│                                          │
│  Deduções identificadas:                 │
│  ✓ Dependente (filha)      + R$   900   │
│  ✓ Plano de saúde          + R$   600   │
│  ✓ Despesas médicas        + R$   450   │
│  ✓ Previdência (INSS)      + R$   400   │
│                                          │
│  ┌─────────────────────────────────┐    │
│  │   Começar minha declaração  →   │    │
│  └─────────────────────────────────┘    │
│  [Ver detalhes das deduções]             │
└─────────────────────────────────────────┘
```

---

### Tela 2 — Home (Dashboard Principal)

```
┌─────────────────────────────────────────┐
│  Olá, Clara ☀️              [🔔] [👤]   │
│                                          │
│  ┌───────────────────────────────────┐  │
│  │  Sua declaração 2026               │  │
│  │  ████████░░░░░░░░  45% completa   │  │
│  │  Prazo: 30 dias restantes          │  │
│  │  [Continuar declaração →]          │  │
│  └───────────────────────────────────┘  │
│                                          │
│  Economia estimada                       │
│  ┌──────────┐  ┌──────────┐            │
│  │R$ 2.350  │  │ 4 deduções│            │
│  │estimado  │  │ ativas    │            │
│  └──────────┘  └──────────┘            │
│                                          │
│  ⚠️  Pendências                          │
│  • Adicione comprovante de plano saúde  │
│  • Informe gastos com escola da Ana     │
│                                          │
│  Ações rápidas                           │
│  [📄 Add nota]  [💊 Add médico]          │
│  [📊 Ver deduções]  [📋 Declaração]     │
└─────────────────────────────────────────┘
```

---

### Tela 3 — Cofre de Documentos

```
┌─────────────────────────────────────────┐
│  ← Cofre de Documentos         [+ Add]  │
│                                          │
│  🔍 Buscar documentos...                │
│                                          │
│  Saúde                          R$ 2.100│
│  ├─ Plano de saúde anual      R$ 1.200 │
│  │   📄 Comprovante Jan-Dez      ✅    │
│  ├─ Consulta cardiologista      R$ 350  │
│  │   📄 Recibo 15/03             ✅    │
│  └─ Dentista                    R$ 550  │
│      ⚠️ Sem comprovante         [Add]   │
│                                          │
│  Educação                       R$ 900  │
│  └─ Escola Ana (dependente)     R$ 900  │
│      📄 Mensalidades Jan-Dez     ✅    │
│                                          │
│  ┌─────────────────────────────────┐    │
│  │  📷 Fotografar nota fiscal      │    │
│  │  📁 Importar arquivo            │    │
│  │  🏦 Importar do banco           │    │
│  └─────────────────────────────────┘    │
└─────────────────────────────────────────┘
```

---

### Tela 4 — Declaração Guiada

```
┌─────────────────────────────────────────┐
│  ← Declaração 2026       [2 de 7] ████░ │
│                                          │
│  Rendimentos do Trabalho                 │
│                                          │
│  Esses dados vêm do seu holerite de     │
│  dezembro. Confirme ou corrija:          │
│                                          │
│  Rendimento bruto anual                  │
│  ┌─────────────────────────────────┐    │
│  │  R$ 84.000,00       [importado] │    │
│  └─────────────────────────────────┘    │
│                                          │
│  IR retido na fonte                      │
│  ┌─────────────────────────────────┐    │
│  └─────────────────────────────────┘    │
│  ⓘ Veja no informe de rendimentos da    │
│    sua empresa (enviado em jan/fev)     │
│                                          │
│  INSS retido                             │
│  ┌─────────────────────────────────┐    │
│  │  R$ 7.560,00        [importado] │    │
│  └─────────────────────────────────┘    │
│                                          │
│  ┌──────────────┐  ┌───────────────┐    │
│  │   ← Voltar   │  │  Próximo →    │    │
│  └──────────────┘  └───────────────┘    │
└─────────────────────────────────────────┘
```

---

### Tela 5 — Resultado Final e Envio

```
┌─────────────────────────────────────────┐
│  ← Revisão Final                         │
│                                          │
│  ✅ Declaração pronta para envio         │
│                                          │
│  Resumo                                  │
│  ┌───────────────────────────────────┐  │
│  │  Rendimento tributável  R$ 84.000 │  │
│  │  Total de deduções      R$ 11.000 │  │
│  │  Base de cálculo        R$ 73.000 │  │
│  │  IR devido               R$ 7.200 │  │
│  │  IR retido na fonte      R$ 9.550 │  │
│  │                          ─────── │  │
│  │  💰 RESTITUIÇÃO         R$ 2.350 │  │
│  └───────────────────────────────────┘  │
│                                          │
│  GuIA encontrou R$ 2.350 a mais do que  │
│  você teria sem otimização. 🎉           │
│                                          │
│  ┌─────────────────────────────────┐    │
│  │  Enviar para a Receita Federal  │    │
│  └─────────────────────────────────┘    │
│  [Baixar PDF]  [Compartilhar resultado] │
└─────────────────────────────────────────┘
```

---

### Tela 6 — Pós-Declaração / Acompanhamento

```
┌─────────────────────────────────────────┐
│  GuIA                           [🔔][👤] │
│                                          │
│  🎉 Declaração enviada!                  │
│  Protocolo: 8811.22.333.444-55           │
│                                          │
│  Sua restituição                         │
│  ┌───────────────────────────────────┐  │
│  │  R$ 2.350,00                       │  │
│  │                                    │  │
│  │  Status: EM PROCESSAMENTO          │  │
│  │  ○────────────●────────────○       │  │
│  │  Enviada   Processando  Aprovada   │  │
│  │                                    │  │
│  │  Previsão: Lote 3 (agosto/2026)    │  │
│  └───────────────────────────────────┘  │
│                                          │
│  💡 Comece a guardar notas de 2026 já   │
│     para maximizar a próxima restituição │
│                                          │
│  [Planejar 2027]  [Indicar amigo]       │
└─────────────────────────────────────────┘
```

---

## Status dos Artefatos — Módulo 03

| # | Artefato | Status |
|---|---------|--------|
| 1 | User Story Map (39 stories mapeadas) | ✅ Concluído |
| 2 | Product Backlog priorizado (RICE) | ✅ Concluído |
| 3 | User Stories com critérios de aceite (BDD) | ✅ Concluído |
| 4 | Definition of Ready e Definition of Done | ✅ Concluído |
| 5 | Roadmap MVP → V1 → V2 (25 sprints) | ✅ Concluído |
| 6 | Pesquisa de APIs públicas (4 blocos) | ✅ Concluído |
| 7 | Descrição de telas e funcionalidades (6 telas) | ✅ Concluído |

**Próxima etapa:** Módulo 04 — Product Marketing (Go-to-Market, posicionamento, canais)
