# GuIA — Artefatos do Módulo 06
**MBA Tera · Liderança e Estratégia de Produtos Digitais na Era da IA**
**Módulo 06 — Liderança Estratégica**
**Produzido em:** Junho 2026

---

## Artefato 1 — Mapa de Stakeholders

### Inventário de Stakeholders

| # | Stakeholder | Tipo | Papel | Interesse | Influência | Postura |
|---|------------|------|-------|-----------|-----------|---------|
| 1 | CEO / Founder | Interno | Define visão, aloca capital, decide pivôs | Crescimento, valuation, sobrevivência | **Alto** | Apoiador |
| 2 | Investidores / Board | Externo | Aportam capital, cobram métricas | ROI, MRR, retenção, defensibilidade | **Alto** | Apoiador condicional |
| 3 | Head de Produto | Interno | Lidera estratégia e roadmap | Sucesso do produto, PMF, NSM | **Alto** | Apoiador |
| 4 | Squad Engenharia / Tech Lead | Interno | Constrói a plataforma e a camada de IA | Viabilidade técnica, qualidade, débito controlado | **Alto** | Apoiador |
| 5 | Squad IA/Dados | Interno | Modelos, RAG, pipeline tributário | Acurácia, dados de qualidade, infra de ML | **Alto** | Apoiador |
| 6 | Squad Growth/Marketing | Interno | Aquisição, ativação, conversão | CAC, funil AARRR, brand | **Médio** | Apoiador |
| 7 | Time Jurídico/Tributário | Interno | Valida regras, compliance fiscal | Risco legal, conformidade com RFB | **Alto** | Neutro/Cauteloso |
| 8 | DPO / Encarregado LGPD | Interno | Garante conformidade de dados | Privacidade, consentimento, dados sensíveis | **Alto** | Cauteloso |
| 9 | Usuários (Clara, Rafael, Lucas, Família Silva) | Externo | Usam e pagam pelo produto | Economia de impostos, simplicidade, confiança | **Alto** | Neutro → Apoiador |
| 10 | Receita Federal (RFB) | Externo | Regulador — define IN, layout DIRPF, e-CAC | Conformidade, integridade dos dados declarados | **Alto** | Neutro (regulador) |
| 11 | Contadores / CRC | Externo | Profissão potencialmente parceira ou ameaçada | Modelo de negócio, parceria ou concorrência | **Médio** | Resistente → Parceiro |
| 12 | Concorrentes (app RFB, Serasa, IROnline) | Externo | Disputam o mesmo usuário | Market share | **Médio** | Resistente |
| 13 | Parceiros (Open Finance, B3, corretoras, bancos) | Externo | Fornecem dados financeiros via API | Tráfego, co-marketing, dados | **Médio** | Neutro |
| 14 | Fornecedores de IA (LLM, OCR, cloud) | Externo | Infra técnica crítica | Receita de consumo, SLA | **Médio** | Apoiador comercial |
| 15 | Imprensa / Influenciadores de finanças | Externo | Amplificam ou criticam | Pauta, audiência | **Baixo/Médio** | Neutro |
| 16 | Time de Suporte/CS | Interno | Atendimento e retenção | Volume de tickets, satisfação | **Médio** | Apoiador |
| 17 | PROCON / Defesa do Consumidor | Externo | Fiscaliza relação de consumo | Transparência de cobrança | **Baixo** | Neutro |
| 18 | BCB (Banco Central do Brasil) | Externo | Regulador do Open Finance | Conformidade com as regras do SBCD e consentimento do usuário | **Alto** | Neutro (regulador) |
| 19 | Pluggy / Belvo (agregadores Open Finance) | Externo | Parceiros técnicos críticos — fornecem SDK e infra de conexão bancária | Receita de parceria, adoção, estabilidade do produto | **Médio** | Apoiador comercial |
| 20 | Bancos participantes do Open Finance (Nubank, Itaú, BB, Bradesco, Santander, Inter, C6, XP) | Externo | Fonte dos dados bancários do usuário | Compliance e experiência do cliente | **Alto** | Neutra/Cautelosa |

### Matriz Poder × Interesse

```
ALTA       │  MANTER SATISFEITO              │  GERENCIAR DE PERTO
INFLUÊNCIA │  · Receita Federal (RFB)        │  · CEO/Founder
           │  · DPO/LGPD                     │  · Investidores/Board
           │  · Time Jurídico/Tributário     │  · Head de Produto
           │  · BCB (Banco Central)          │  · Squad Eng + IA/Dados
           │  · Bancos (Open Finance)        │  · Usuários (personas)
           ├─────────────────────────────────┼──────────────────────────
BAIXA      │  MONITORAR                      │  MANTER INFORMADO
INFLUÊNCIA │  · PROCON                       │  · Growth/Marketing
           │  · Imprensa/Influencers         │  · Suporte/CS
           │  · Concorrentes                 │  · Contadores/CRC
           │                                 │  · Parceiros (OF/B3)
           │                                 │  · Pluggy/Belvo (agregadores)
           │                                 │  · Fornecedores de IA
           └─────────────────────────────────┴──────────────────────────
                 BAIXO INTERESSE                   ALTO INTERESSE
```

### Estratégia de Engajamento por Stakeholder

| Stakeholder | Quadrante | Estratégia | Cadência |
|------------|-----------|-----------|---------|
| CEO/Founder | Gerenciar de perto | 1:1 semanal, alinhamento de visão e trade-offs; co-decisão em pivôs | Semanal |
| Investidores/Board | Gerenciar de perto | Board deck com NSM, MRR, cohort de retenção; update de riscos regulatórios | Mensal + ad hoc |
| Squad Eng / IA/Dados | Gerenciar de perto | Refinamento contínuo, roadmap técnico compartilhado, definição de "acurácia mínima aceitável" | Diária/semanal |
| Usuários | Gerenciar de perto | Pesquisa contínua, CSAT/NPS, programa beta, comunidade; loop de feedback no produto | Contínuo |
| Receita Federal | Manter satisfeito | Conformidade rigorosa; posicionar o GuIA como "facilitador de conformidade", nunca como instrumento de evasão | A cada temporada IRPF |
| DPO/LGPD | Manter satisfeito | Privacy by design, DPIA, revisão de consentimento para dados financeiros sensíveis (Art. 11 LGPD) | A cada release sensível |
| Jurídico/Tributário | Manter satisfeito | Comitê de revisão de regras; aprovação antes de publicar simulações/sugestões | A cada mudança normativa |
| Growth/Marketing | Manter informado | Roadmap de features para campanhas sazonais; alinhamento de pricing e go-to-market | Quinzenal |
| Contadores/CRC | Manter informado | Programa GuIA for Accountants; posicionar como ferramenta complementar, não substituta | Trimestral |
| Parceiros (Open Finance/B3) | Manter informado | Co-marketing, roadmap de integrações, SLAs de API | Mensal |
| Concorrentes | Monitorar | Análise competitiva, monitoramento de pricing e features | Trimestral |
| Imprensa/Influencers | Monitorar | PR seletivo na temporada IRPF; conteúdo educativo | Sazonal |
| BCB (Banco Central) | Manter satisfeito | Conformidade rigorosa com as resoluções do Open Finance Brasil (JSR, FAPI); monitorar circulares do BCB sobre novas fases e escopos | A cada nova circular/fase |
| Pluggy/Belvo (agregadores) | Manter informado | Parceiro técnico estratégico; negociar SLA contratual de disponibilidade ≥ 99,5%; roadmap conjunto de novas integrações | Mensal |
| Bancos (Open Finance) | Monitorar | Não há relacionamento direto; monitorar mudanças na API de cada banco via Pluggy; manter plano de contingência para bancos com dados incompletos | Mensal |

---

## Artefato 2 — Roadmap Estratégico de Longo Prazo (3 anos)

> **Visão de longo prazo:** "Tornar-se o copiloto tributário-financeiro de todo brasileiro — do CLT ao investidor —, transformando a obrigação fiscal anual em economia recorrente e inteligência financeira contínua."

### Ano 1 — CONSOLIDAÇÃO (MVP → Product-Market Fit)

| Dimensão | Detalhe |
|----------|---------|
| **Foco estratégico** | Provar que o GuIA economiza imposto de verdade e gera confiança; atingir PMF na persona Clara (CLT) e iniciar Rafael (MEI/autônomo) |
| **Principais iniciativas** | (1) MVP de declaração IRPF guiada com importação de informes; (2) Motor de regras determinístico — tabelas IRPF, deduções legais; (3) OCR de informes e recibos médicos/educação; (4) Onboarding por persona; (5) Lançamento dos tiers Básico e Pro; (6) Integração inicial Open Finance; (7) Integração Open Finance via Pluggy — importação automática de extratos e categorização de gastos dedutíveis |
| **Métricas-alvo** | 250k usuários · R$ 500k MRR · ativação > 40% · retenção pós-temporada > 25% · NSM R$ 600/usuário/ano · NPS > 40 |
| **Riscos principais** | Acurácia insuficiente das regras (risco legal); sazonalidade extrema; CAC alto fora da temporada; dependência do layout DIRPF/RFB |

### Ano 2 — ESCALA (expansão de personas e funcionalidades)

| Dimensão | Detalhe |
|----------|---------|
| **Foco estratégico** | Quebrar a sazonalidade; escalar para Lucas (investidor) e Família Silva |
| **Principais iniciativas** | (1) Planejamento tributário proativo anual — carnê-leão, DARF, ganho de capital; (2) Módulo de investimentos (B3, ações, FIIs, cripto, exterior); (3) Chat tributário com LLM + RAG; (4) Lançamento Premium (R$ 29,90); (5) GuIA for Accountants (B2B2C); (6) ML de classificação de despesas; (7) Open Finance completo: investimentos, previdência, seguros; sync contínuo multi-conta |
| **Métricas-alvo** | 1,2M usuários · R$ 3M MRR · mix Premium > 15% da base paga · uso fora de temporada > 35% MAU · NSM R$ 1.100/usuário/ano · churn anual < 30% |
| **Riscos principais** | Complexidade tributária de investimentos; concorrência de bancos/corretoras; custo crescente de IA; manutenção de modelos frente a mudanças legislativas |

### Ano 3 — PLATAFORMA (ecossistema tributário-financeiro completo)

| Dimensão | Detalhe |
|----------|---------|
| **Foco estratégico** | IA agêntica que executa; marketplace de serviços tributários; dados como diferencial defensável |
| **Principais iniciativas** | (1) IA agêntica: gera/paga DARF e pré-preenche/transmite declaração via e-CAC; (2) Marketplace: contadores, consultoria, regularização de malha fina; (3) Open Finance completo com iniciação de pagamento; (4) PJ light (MEI → ME); (5) API GuIA para terceiros; (6) Predição de risco de malha fina |
| **Métricas-alvo** | 3M+ usuários · R$ 10M+ MRR · receita de ecossistema > 25% do total · LTV/CAC > 4 · NSM R$ 1.800/usuário/ano |
| **Riscos principais** | Risco regulatório da IA agêntica executando atos fiscais; RFB melhorando seu próprio app; fraude com poder de iniciar pagamentos |

### Linha do tempo

```
ANO 1 ──────────────► ANO 2 ──────────────► ANO 3
CONSOLIDAÇÃO           ESCALA               PLATAFORMA
MVP → PMF             Personas + Anual      Ecossistema + Agêntica
250k / R$ 500k MRR    1,2M / R$ 3M MRR      3M+ / R$ 10M+ MRR
Regras + OCR          LLM + RAG + ML        IA Agêntica + Marketplace
NSM: R$ 600/usr       NSM: R$ 1.100/usr     NSM: R$ 1.800/usr
```

---

## Artefato 3 — Comunicação Estratégica (Vision Doc / 6-Pager)

**1. Problema**

Todo ano, cerca de 45 milhões de brasileiros enfrentam a declaração de Imposto de Renda como um ritual de ansiedade: medo da malha fina, dúvidas sobre o que é dedutível e a sensação de estar "pagando imposto demais" sem saber como economizar legalmente. O conhecimento tributário é caro (contadores cobram de R$ 200 a R$ 2.000), fragmentado e pontual — concentrado nos meses de março a maio. Resultado: pessoas deixam de aproveitar deduções legítimas, cometem erros que resultam em malha, e o planejamento tributário — que poderia gerar economia ao longo de todo o ano — simplesmente não existe para a pessoa física comum.

**2. Solução**

O GuIA é um assistente financeiro pessoal com IA que combina motor de regras tributárias atualizado, OCR de documentos, classificação inteligente de despesas e copiloto conversacional (LLM + RAG sobre legislação da RFB) para guiar o usuário **o ano todo** — não só na declaração. Ele importa informes, identifica deduções, simula cenários, calcula DARF e alerta proativamente sobre riscos de malha fina e oportunidades de economia. A métrica-norte é simples e tangível: **reais efetivamente economizados em impostos por usuário ativo por ano.**

**3. Por que agora**

Convergência de três forças: (a) **maturidade da IA generativa** torna viável um copiloto tributário confiável pela primeira vez; (b) **Open Finance** regulado pelo BCB permite acesso estruturado e consentido aos dados financeiros; (c) **digitalização da RFB** — declaração pré-preenchida, e-CAC, DIRPF importável — cria os trilhos para automação real. A janela está aberta antes que grandes bancos ou a própria Receita Federal ocupem o espaço.

**4. Por que nós**

Somos o **único assistente tributário verdadeiramente anual.** Nosso diferencial defensável: (a) base de conhecimento tributário curada e versionada — IN RFB, CARF, STJ — alimentando o RAG; (b) dados longitudinais do usuário que melhoram a economia a cada ciclo; (c) NSM orientada a resultado financeiro real. Quanto mais o usuário usa, mais economiza, mais difícil é sair — defensibilidade por dados e custo de troca.

**5. O que precisamos**

- **Capital:** runway de 18 meses para squad de IA/Dados, engenharia, jurídico e aquisição
- **Decisões:** (a) aval do Board para o modelo freemium 3-tiers; (b) aprovação do Comitê Jurídico para o escopo de "sugestão tributária"; (c) priorização de Open Finance como integração estratégica de Ano 1
- **Recursos:** squad de IA/Dados dedicado; consultoria tributária in-house; orçamento de cloud/LLM; DPO para conformidade LGPD

**6. Próximos 90 dias**

| Semanas | Entrega |
|---------|---------|
| 1–4 | Fechar Comitê Jurídico/regras; DPIA LGPD aprovada; contratar Lead de IA/Dados |
| 5–8 | MVP do motor determinístico (tabelas IRPF + deduções) + OCR de informes de rendimento |
| 9–12 | Beta fechado com 1.000 usuários (persona Clara); medir NSM real e ativação |
| **Gate** | Economia média ≥ R$ 400/usuário no beta + ativação ≥ 35% → libera investimento em aquisição |

---

## Artefato 4 — OKRs Hierárquicos

### Nível 1 — OKRs de Empresa (anual)

**Objetivo E1 — Tornar o GuIA financeiramente sustentável com PMF comprovado**
- KR1: 250.000 usuários cadastrados e ativos no ciclo IRPF
- KR2: R$ 500.000 de MRR ao fim do Ano 1
- KR3: Retenção anual da base paga ≥ 70%
- KR4: NSM ≥ R$ 600 economizados/usuário/ano

**Objetivo E2 — Construir confiança e defensibilidade no mercado tributário**
- KR1: Acurácia tributária ≥ 98% em auditoria por amostragem
- KR2: NPS ≥ 40 e CSAT ≥ 4,3/5 ao fim da temporada IRPF
- KR3: Zero incidentes graves de LGPD ou conformidade com a RFB

### Nível 2 — OKRs de Produto (trimestral)

#### Q1 — Pré-temporada e prontidão para o pico IRPF

**P1.Q1 — Declaração que gera economia comprovada**
- KR1: Motor de regras cobrindo 100% das deduções legais do exercício
- KR2: OCR de informes com acurácia ≥ 95% por campo
- KR3: ≥ 35% dos usuários que iniciam concluem a declaração no GuIA

**P2.Q1 — Maximizar ativação no início da temporada**
- KR1: Ativação (importar 1º informe) ≥ 40% em até 7 dias após cadastro
- KR2: Time-to-value (1ª simulação de restituição) < 10 minutos
- KR3: Conversão Básico → Pro ≥ 6%

**P3.Q1 — Conformidade e confiança**
- KR1: 100% das regras tributárias revisadas pelo Comitê Jurídico antes do release
- KR2: DPIA LGPD aprovada e consentimento de dados sensíveis implementado (Art. 11)
- KR3: Taxa de erro reportado pelo usuário < 1% das declarações

#### Q2 — Pico, fechamento da temporada e início do pós-sazonal

**P1.Q2 — Sustentar o pico com qualidade e disponibilidade**
- KR1: Disponibilidade da plataforma ≥ 99,9% no período abr–mai
- KR2: Latência do chat tributário (RAG) < 5s p95
- KR3: ≥ 80% das declarações enviadas sem cair em malha fina

**P2.Q2 — Iniciar a transição para uso anual**
- KR1: Módulo de planejamento pós-declaração disponível para 100% dos usuários Pro
- KR2: ≥ 25% dos usuários ativos retornam ao app em junho (fora do pico)
- KR3: Conversão Pro → Premium ≥ 4%
- KR4: ≥ 30% dos usuários ativos têm ao menos 1 conta bancária conectada via Open Finance ao final do Q2

**P3.Q2 — Ampliar a economia gerada por usuário**
- KR1: NSM do trimestre ≥ R$ 650 economizados/usuário
- KR2: ML de classificação com precisão ≥ 90%
- KR3: Reduzir tickets de suporte relacionados à declaração em 20% vs. Q1

### Nível 3 — OKRs de Time

| Squad | Objetivo | KRs principais |
|-------|---------|---------------|
| **Growth** | Funil de aquisição eficiente e sazonalmente resiliente | CAC ≤ R$ 15 na temporada · 40% aquisições via orgânico · Referral ≥ 15% · LTV/CAC ≥ 3 |
| **Core Product** | Melhor experiência de declaração e planejamento do mercado | Declaração < 20 min · Cobertura de cenários ≥ 95% · CSAT ≥ 4,5/5 · Taxa de conclusão ≥ 35% · KR5: Taxa de conclusão do fluxo de conexão bancária (Pluggy widget → conta conectada) ≥ 70% |
| **IA/Dados** | IA tributária precisa, atualizada e confiável | Acurácia Rules Engine ≥ 98% · OCR ≥ 95% · Latência RAG < 5s p95 · SLA ingestão ≤ 5 dias úteis |

---

## Status dos Artefatos — Módulo 06

| # | Artefato | Status |
|---|---------|--------|
| 1 | Mapa de Stakeholders (20 stakeholders + Matriz + Estratégia) | ✅ Concluído |
| 2 | Roadmap Estratégico 3 anos | ✅ Concluído |
| 3 | Vision Doc / 6-Pager | ✅ Concluído |
| 4 | OKRs Hierárquicos (Empresa → Produto → Time) | ✅ Concluído |

**Próxima etapa:** Módulo 07 — IA: Inovação e Eficiência
