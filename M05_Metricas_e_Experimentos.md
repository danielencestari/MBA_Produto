# GuIA — Artefatos do Módulo 05
**MBA Tera · Liderança e Estratégia de Produtos Digitais na Era da IA**
**Módulo 05 — Analytics & Experimentação**
**Produzido em:** Junho 2026

---

## Artefato 1 — North Star Metric e Árvore de Métricas

### North Star Metric

> **"Reais economizados em impostos por usuário ativo por ano" (R$)**

**Por que esta e não outra:**

| Candidata | Por que não é a NSM |
|----------|-------------------|
| Usuários cadastrados | Vanity metric — não mede valor real entregue |
| MRR | Mede captura de valor, não criação de valor |
| Declarações enviadas | Sazonal, não reflete uso anual |
| DAU / MAU | Produto não é de uso diário — leva a decisões erradas |
| **Reais economizados por usuário ativo** ✅ | Alinha empresa, produto e usuário. Só cresce com produto melhor OU mais usuários engajados |

**Metas da NSM:**
- Mês 3: R$ 800 por usuário ativo
- Mês 6: R$ 1.500 por usuário ativo
- Mês 12: R$ 2.500 por usuário ativo

### Árvore de Métricas

```
┌─────────────────────────────────────────────────────────────────┐
│   NSM: Reais economizados em impostos por usuário ativo (R$)    │
└──────────────────────┬──────────────────────────────────────────┘
                       │
          ┌────────────┴─────────────┐
          │                          │
   Qtd de deduções             Valor médio por
   aproveitadas/usuário        dedução (R$)
          │                          │
    ┌─────┴──────┐            ┌──────┴──────┐
    │            │            │             │
  Taxa de     Cobertura    Qualidade     Perfil
  ativação    de perfil    do OCR/IA     tributário
  do cofre    fiscal       (precisão)    do usuário
    │            │
    │       ┌────┴────┐
    │       │         │
    │    Documentos  Integrações
    │    adicionados  ativas (Open
    │    por usuário  Finance, B3)
    │
    └─→ Engajamento fora de abril
           (% uso Jan–Fev + Maio–Dez)
```

**Input metrics** (o time controla):
- Nº de documentos adicionados por usuário por mês
- Taxa de conclusão do onboarding (%)
- Nº de integrações ativas (Open Finance, B3)
- Precisão do motor de IA (% deduções corretas)
- Nº de perguntas respondidas pelo chat por usuário
- **Contas bancárias conectadas por usuário ativo** ← nova (Open Finance / Pluggy)
- **Transações categorizadas automaticamente como dedutíveis por mês** ← nova

> **Conexão causal Open Finance → NSM:** mais contas conectadas → mais despesas capturadas automaticamente → maior cobertura de deduções sem esforço manual → maior economia identificada → NSM sobe

**Output metrics** (o mercado responde):
- Reais economizados por usuário (NSM)
- MRR · Churn · NPS
- Retenção D30, D90, D365
- Taxa de conversão freemium → pago

---

## Artefato 2 — Framework AARRR: KPIs por Camada do Funil

### A — Acquisition (Aquisição)

| KPI | Meta Mês 3 | Meta Mês 12 | Frequência |
|-----|-----------|------------|-----------|
| Visitantes únicos no site | 30.000 | 200.000 | Semanal |
| Taxa de conversão visitante → cadastro | 8% | 12% | Semanal |
| CAC blended | R$ 30 | R$ 18 | Mensal |
| Novos cadastros por semana | 1.500 | 8.000 | Semanal |
| % cadastros orgânicos | 30% | 50% | Mensal |

### A — Activation (Ativação)

| KPI | Meta Mês 3 | Meta Mês 12 | Frequência |
|-----|-----------|------------|-----------|
| Taxa de conclusão do onboarding | 60% | 75% | Diária |
| Tempo até o aha moment | < 2 min | < 90 seg | Semanal |
| % que viram a estimativa de economia | 55% | 70% | Diária |
| Taxa signup → 1º documento adicionado | 35% | 50% | Semanal |
| Taxa de ativação D1 | 40% | 55% | Diária |
| NPS de onboarding | > 7,5 | > 8,5 | Semanal |
| **Taxa de conexão bancária** (usuários que conectam ≥1 conta / cadastrados) | **25%** | **50%** | **Semanal** |
| **Deduções identificadas automaticamente no 1º extrato** (valor médio R$ na 1ª importação) | **R$ 300** | **R$ 600** | **Semanal** |

**Evento de ativação definido:** Usuário completou o simulador E viu a tela de estimativa de economia

**Versão alternativa (usuários com banco conectado):** Usuário conectou ≥1 conta bancária E viu ≥1 transação marcada como dedutível

### R — Retention (Retenção)

| KPI | Meta Mês 3 | Meta Mês 12 | Frequência |
|-----|-----------|------------|-----------|
| Retenção D7 | 45% | 55% | Semanal |
| Retenção D30 | 30% | 45% | Mensal |
| Retenção D90 | 20% | 35% | Mensal |
| Retenção anual (D365) | — | 60% | Anual |
| Churn mensal (pagantes) | < 10% | < 5% | Mensal |
| **% uso fora de abril** ← métrica crítica | 25% | 45% | Mensal |
| **Retenção de usuários com conta conectada vs. sem conta** (delta D30 entre grupos) | **D30 ≥ 15pp maior (conectados vs. não conectados)** | **D30 ≥ 15pp maior** | **Mensal** |

> **"% uso fora de abril"** valida a hipótese H05 e o diferencial central do GuIA. Se não passar de 30% em 12 meses, revisar estratégia de produto anual.

> **"Retenção com conta conectada vs. sem conta"** valida se a conexão bancária via Open Finance aumenta o engajamento de longo prazo. Se o delta D30 for < 15pp, a feature de importação automática não está gerando valor percebido suficiente — revisar UX de categorização e notificações.

### R — Revenue (Receita)

| KPI | Meta Mês 3 | Meta Mês 12 | Frequência |
|-----|-----------|------------|-----------|
| MRR | R$ 25.000 | R$ 500.000 | Semanal |
| MRR Growth Rate | 25% | 15% | Mensal |
| Taxa de conversão freemium → pago | 8% | 15% | Mensal |
| ARPU | R$ 3,50 | R$ 8,00 | Mensal |
| ARPPU | R$ 12,50 | R$ 15,00 | Mensal |
| LTV | R$ 125 | R$ 300 | Mensal |
| LTV / CAC | 4x | 16x | Mensal |
| Mix de planos (Básico/Pro/Premium) | 75/20/5% | 60/28/12% | Mensal |

### R — Referral (Indicação)

| KPI | Meta Mês 3 | Meta Mês 12 | Frequência |
|-----|-----------|------------|-----------|
| K-factor (coeficiente viral) | 0,15 | 0,40 | Mensal |
| Taxa de convite | 10% | 20% | Mensal |
| Taxa de conversão convite → cadastro | 25% | 35% | Mensal |
| CAC via referral | R$ 8 | R$ 5 | Mensal |
| NPS geral | > 40 | > 55 | Mensal |

---

## Artefato 3 — Dashboard de Produto

### Visão Diária — "Saúde do produto"

| Métrica | Alerta Vermelho | Alerta Amarelo | Normal | Dono |
|--------|:--------------:|:--------------:|:------:|:----:|
| Novos cadastros (D-1) | < 50 | 50–100 | > 100 | Growth |
| Taxa conclusão onboarding | < 40% | 40–55% | > 55% | Produto |
| Erros críticos (Sentry) | > 0 P0 | > 5 P1 | 0 erros críticos | Eng |
| Pagamentos processados (D-1) | < R$ 500 | R$ 500–1k | > R$ 1k | Produto |
| Tempo médio até aha moment | > 5 min | 2–5 min | < 2 min | Produto |
| **Contas bancárias conectadas (D-1)** | **< 10 novas** | **10–50 novas** | **> 50 novas** | **Produto** |

### Visão Semanal — "Funil e crescimento"

| Métrica | Benchmark | Tendência |
|--------|----------|----------|
| Novos cadastros na semana | +15% semana a semana | Crescente |
| Taxa conversão visitante → cadastro | > 8% | Estável ou crescente |
| Taxa ativação (onboarding completo) | > 60% | Crescente |
| Retenção D7 do cohort da semana | > 45% | Estável |
| MRR semanal | +5% semana a semana | Crescente |
| Churn semanal | < 2% da base | Decrescente |
| NSM (R$ economizados / usuário ativo) | Crescente | Crescente |

### Visão Mensal — "Negócio e estratégia"

| Métrica | Meta Mês 6 | Meta Mês 12 |
|--------|-----------|------------|
| MAU | 80.000 | 250.000 |
| MRR | R$ 150.000 | R$ 500.000 |
| Churn mensal | < 8% | < 5% |
| LTV / CAC | > 3x | > 8x |
| NPS | > 45 | > 55 |
| % uso fora de abril | > 30% | > 45% |
| NSM | R$ 1.500 | R$ 2.500 |

### Tracking Plan — Eventos de Analytics

| Evento | Propriedades | Usado em |
|--------|------------|---------|
| `user_signed_up` | source, canal_utm, persona_detectada | Aquisição, cohort |
| `onboarding_completed` | tempo_segundos, campos_preenchidos | Ativação |
| `aha_moment_reached` | valor_estimado_R$, deducoes_encontradas | Ativação, NSM |
| `document_added` | tipo_doc, metodo (ocr/manual/api), categoria | Engajamento |
| `declaration_submitted` | valor_restituicao_R$, deducoes_aproveitadas | NSM |
| `upgrade_triggered` | trigger_evento, plano_origem, plano_destino | Receita |
| `subscription_started` | plano, ciclo (mensal/anual), valor_R$ | Receita |
| `subscription_cancelled` | motivo, dias_como_cliente | Churn |
| `referral_sent` | canal (whatsapp/email/link) | Referral |
| `referral_converted` | indicador_id | K-factor |
| `ai_query_rated` | avaliacao (1–5), foi_util | Qualidade IA |
| `bank_account_connected` | instituicao, tipo_conta, num_transacoes_importadas | Ativação, NSM |
| `transaction_categorized` | categoria_ir, dedutivel (bool), valor_R$, metodo (regex/ml/llm/manual) | NSM, qualidade IA |
| `deduction_identified_from_bank` | categoria, valor_R$, transacao_id | NSM, engajamento |

---

## Artefato 4 — Plano de Experimentação (Roadmap de Testes A/B)

> ICE Score: Impact × Confidence × Ease (1–10 cada)

### Backlog de Experimentos Priorizados

| # | Experimento | Impact | Conf. | Ease | ICE | Sprint |
|---|------------|:------:|:-----:|:----:|:---:|:------:|
| E01 | Onboarding: 3 campos vs. 5 campos | 9 | 8 | 9 | **648** | S1 |
| E02 | Aha moment: valor absoluto vs. % de economia | 9 | 7 | 9 | **567** | S1 |
| E04 | Pricing: Pro destacado vs. Premium destacado | 9 | 7 | 7 | **441** | S2 |
| E08 | Notificação: "Faltam X dias" vs. "Prazo: data" | 7 | 7 | 9 | **441** | S4 |
| E06 | Email D3: dedução personalizada vs. genérica | 8 | 8 | 7 | **448** | S3 |
| E03 | CTA pós-aha: "Começar declaração" vs. "Ver deduções" | 8 | 6 | 9 | **432** | S2 |
| E10 | Declaração: guiada passo a passo vs. formulário livre | 9 | 8 | 6 | **432** | S5 |
| E05 | Upsell no cofre: modal imediato vs. banner persistente | 7 | 6 | 8 | **336** | S3 |
| E09 | Referral: incentivo para quem indica vs. indicado | 8 | 6 | 7 | **336** | S5 |
| E07 | Preço anual: desconto 17% vs. 30% | 8 | 5 | 8 | **320** | S4 |
| **E11** | **Momento de oferecer conexão bancária: no onboarding vs. após aha moment** | **9** | **7** | **8** | **504** | **S2** |
| **E12** | **Notificação de dedução identificada: push imediato vs. resumo semanal** | **8** | **7** | **8** | **448** | **S3** |

### Detalhamento dos 3 Experimentos Prioritários

#### E01 — Onboarding: 3 campos vs. 5 campos (ICE 648)

**Hipótese HDD:**
> Acreditamos que reduzir o onboarding de 5 para 3 campos resultará em maior taxa de conclusão. Saberemos que tivemos sucesso quando a taxa de conclusão do grupo de tratamento for ≥10pp maior com valor de estimativa equivalente.

| | Variante A (Controle) | Variante B (Tratamento) |
|--|----------------------|------------------------|
| Campos | Fonte de renda · Renda bruta · Dependentes · Plano de saúde · Despesas médicas | Fonte de renda · Renda bruta · Tem deduções? (pergunta única) |

- **Métricas primárias:** Taxa de conclusão do onboarding · Tempo até aha moment
- **Métrica de guarda:** Valor médio da estimativa (não pode cair > 15%)
- **Duração:** 2 semanas · **Amostra mínima:** 500 por variante · **Critério:** p < 0,05

#### E02 — Aha Moment: Valor Absoluto vs. Percentual (ICE 567)

**Hipótese HDD:**
> Acreditamos que mostrar o valor em reais converte mais do que mostrar percentual de economia. Saberemos que tivemos sucesso quando CTR do CTA for ≥15% maior na variante de valor absoluto.

| | Variante A | Variante B | Variante C |
|--|-----------|-----------|-----------|
| Copy | "Você pode economizar R$ 2.350" | "Você economiza 28% a mais" | "R$ 2.350 a mais — 28% acima do que teria sem o GuIA" |

- **Duração:** 1 semana · **Amostra:** 300 por variante

#### E06 — Email D3: Personalizado vs. Genérico (ICE 448)

**Variante A:** Assunto genérico: "Uma dica para aumentar sua restituição"

**Variante B:** Assunto personalizado: "Clara, encontramos R$ 600 no seu plano de saúde"

- **Métricas:** Open rate · CTR · Taxa de retorno ao app em 24h
- **Amostra:** 1.000 por variante (usuários D3 sem upgrade)

#### E11 — Momento de oferecer conexão bancária: no onboarding vs. após aha moment (ICE 504)

**Hipótese HDD:**
> Acreditamos que oferecer a conexão bancária APÓS o usuário ver a estimativa de economia (pós-aha moment) resultará em maior taxa de conexão do que oferecer no onboarding. Saberemos que tivemos sucesso quando a taxa de conexão do grupo pós-aha moment for significativamente maior que a do grupo onboarding.

| | Variante A (Controle) | Variante B (Tratamento) |
|--|----------------------|------------------------|
| Momento | Oferta de conexão bancária durante o onboarding (step 3) | Oferta de conexão bancária após ver a estimativa de economia (pós-aha moment) |

- **Métricas primárias:** Taxa de conexão bancária · Tempo até conexão
- **Métrica de guarda:** Taxa de conclusão do onboarding (não pode cair > 10%)
- **Duração:** 2 semanas · **Amostra mínima:** 400 por variante · **Critério:** p < 0,05

#### E12 — Notificação de dedução identificada: push imediato vs. resumo semanal (ICE 448)

**Hipótese HDD:**
> Acreditamos que a notificação push imediata "Encontramos uma dedução de R$ 85 no seu extrato" converte mais retorno ao app do que o resumo semanal. Saberemos que tivemos sucesso quando a taxa de reabertura do app em 24h for ≥20% maior na variante de push imediato.

| | Variante A (Controle) | Variante B (Tratamento) |
|--|----------------------|------------------------|
| Notificação | Resumo semanal: "Resumo de deduções da semana: R$ 340 identificados" | Push imediato: "Encontramos uma dedução de R$ 85 no seu extrato. Toque para confirmar." |

- **Métricas primárias:** Taxa de reabertura do app em 24h · Taxa de confirmação da dedução
- **Métrica de guarda:** Taxa de opt-out de notificações (não pode aumentar > 5pp)
- **Duração:** 3 semanas · **Amostra mínima:** 600 por variante

---

## Artefato 5 — Hypothesis-Driven Development (HDD)

### Ciclo HDD do GuIA

```
HIPÓTESE → EXPERIMENTO → DADOS → DECISÃO (Perseverar / Pivotar / Parar)
```

### HDD aplicado às hipóteses críticas

| Hipótese | Experimento | Critério de sucesso | Se falso: pivotar para |
|---------|------------|--------------------|-----------------------|
| **H08** — Aha moment < 2 min | Protótipo Figma com 5 usuários cronometrados | ≥70% chegam ao resultado em < 120s | Calculadora em 1 pergunta |
| **H07** — Pagam ao ver economia | Landing page com Stripe real | ≥5% completam pagamento | Trial de 7 dias → paywall |
| **H09** — CLT não usa fora de abril | Cohort D90: % sessões fora de fev-abr | < 20% sessões fora de abril | Push de reengajamento off-season |
| **H05** — Dor existe 12 meses | Entrevistas: episódio tributário espontâneo | ≥7/10 relatam episódio | Reposicionar como produto sazonal premium |
| **H16** — Conversão pós-1ª restituição | Cohort Ano 1 → taxa renovação Ano 2 | ≥60% renovam | Loyalty program; oferta anual no D300 |
| **H21** — Usuários conectam conta quando veem o benefício primeiro | Mostrar preview de deduções estimadas ANTES de pedir autorização Open Finance | ≥50% conectam com preview vs. ≤30% sem preview | Reformular o momento e o contexto do pedido de conexão bancária |
| **H22** — Categorização automática tem precisão ≥ 85% | Auditoria de 500 transações categorizadas — usuário valida se a categoria está correta | ≥85% sem correção manual | Adicionar etapa de revisão obrigatória para categorias tributárias de alto risco (saúde, educação) |

---

## Status dos Artefatos — Módulo 05

| # | Artefato | Status |
|---|---------|--------|
| 1 | North Star Metric + Árvore de Métricas | ✅ Concluído |
| 2 | Framework AARRR completo (40+ KPIs) | ✅ Concluído |
| 3 | Dashboard de produto (diário/semanal/mensal + tracking plan) | ✅ Concluído |
| 4 | Plano de Experimentação (10 testes A/B priorizados por ICE) | ✅ Concluído |
| 5 | Hypothesis-Driven Development aplicado ao GuIA | ✅ Concluído |

**Próxima etapa:** Módulo 06 — Liderança Estratégica (Stakeholders, Roadmap 3 anos, OKRs hierárquicos)
