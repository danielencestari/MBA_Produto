# GuIA — Artefatos do Módulo 02
**MBA Tera · Liderança e Estratégia de Produtos Digitais na Era da IA**
**Módulo 02 — Discovery e Validação**
**Produzido em:** Junho 2026

---

## Artefato 1 — Jobs to be Done (JTBD)

> Framework: JTBD (Christensen) — "As pessoas não compram produtos, elas contratam soluções para fazer um trabalho"
> Estrutura: **Quando** [situação] **quero** [motivação] **para** [resultado esperado]

---

### Clara, 32 — Assalariada CLT

**Job principal (funcional):**
> Quando chega março e o prazo do IR se aproxima, quero declarar tudo corretamente sem precisar entender de legislação tributária, para não cair na malha fina e receber minha restituição o mais rápido possível.

**Jobs secundários:**
- Quando pago uma consulta médica, quero saber na hora se posso deduzir, para não perder esse benefício por falta de organização
- Quando recebo meu holerite, quero entender quanto estou pagando de IR de fato, para saber se o desconto na fonte está correto
- Quando nasce um filho ou incluo dependente, quero saber o impacto tributário real, para tomar a decisão com base em dados

**Job emocional:**
> Quero sentir que estou fazendo a coisa certa — que não estou pagando mais do que devo, nem correndo risco de problema com a Receita.

**Job social:**
> Quero poder dizer "minha declaração já está feita e otimizada" sem precisar de contador como minha família sempre teve.

**Job secundário adicional (Open Finance):**
> Quando vejo meu extrato bancário cheio de gastos, quero saber automaticamente quais deles posso deduzir no IR, para não precisar guardar todos os comprovantes e ainda assim aproveitar cada dedução que tenho direito.

---

### Rafael, 41 — Autônomo/MEI

**Job principal (funcional):**
> Quando recebo de vários clientes ao mesmo tempo, quero separar automaticamente o que é despesa dedutível PF do que é custo do MEI, para não misturar as esferas e não pagar imposto a mais por confusão.

**Jobs secundários:**
- Quando emito uma NF de serviço, quero saber em tempo real qual será o impacto tributário naquele mês, para planejar o caixa
- Quando vence o DAS do MEI, quero ser lembrado com antecedência, para não acumular multas por esquecimento
- Quando fecho o ano, quero um resumo consolidado de toda a minha movimentação PF e PJ, para declarar o IR sem precisar contratar contador

**Job emocional:**
> Quero ter controle — sentir que sei exatamente quanto vou pagar de imposto e por quê, sem depender de ninguém para me explicar.

**Job social:**
> Quero gerir minha vida financeira como um profissional, mesmo sendo autônomo e não tendo time financeiro.

**Job secundário adicional (Open Finance):**
> Quando recebo pagamentos de vários clientes na mesma conta onde tenho despesas pessoais, quero que o app separe automaticamente o que é custo profissional e o que é gasto pessoal, para não misturar tudo e evitar erro na declaração.

---

### Lucas, 28 — Investidor Iniciante

**Job principal (funcional):**
> Quando faço operações na bolsa todo mês, quero saber automaticamente se devo pagar DARF, quanto e até quando, para não acumular multas e juros por desconhecimento.

**Jobs secundários:**
- Quando vendo uma ação com lucro, quero saber imediatamente se preciso recolher imposto aquele mês, para não ser pego de surpresa
- Quando chega a temporada do IR, quero importar todas as minhas operações de uma vez, para não precisar lançar manualmente cada trade
- Quando tenho cripto + ações + Tesouro, quero ver a tributação de cada classe de ativo separada, para entender onde estou pagando mais

**Job emocional:**
> Quero investir com confiança — sem medo de estar fazendo algo errado com o IR sem saber.

**Job social:**
> Quero ser o tipo de investidor que tem a vida tributária organizada — não o que descobre em abril que deve R$ 3k de DARF vencido.

**Job secundário adicional (Open Finance):**
> Quando faço aportes e resgates de investimentos todo mês, quero que o app acompanhe automaticamente minha posição tributária em cada ativo, para nunca ser pego de surpresa com imposto a pagar que não calculei.

---

### Família Silva — Casal com Dependentes

**Job principal (funcional):**
> Quando é época de declarar IR, queremos decidir se declaramos em conjunto ou separado, para pagar menos imposto e receber mais restituição.

**Jobs secundários:**
- Quando pagamos escola e plano de saúde dos filhos, queremos saber qual cônjuge deve deduzir para maximizar o benefício fiscal
- Quando um dos cônjuges é CLT e outro é autônomo, queremos consolidar tudo em uma única visão, para não perder deduções por falta de organização

**Job emocional:**
> Queremos sentir que estamos aproveitando todos os benefícios que a lei nos dá como família — não deixando dinheiro na mesa.

**Job secundário adicional (Open Finance):**
> Quando pagamos escola e plano de saúde dos filhos com cartões de diferentes titulares, queremos que o app consolide tudo automaticamente, para sabermos exatamente quanto cada cônjuge pode deduzir sem precisar juntar recibo por recibo.

---

## Artefato 2 — Mapeamento de Hipóteses (Assumption Map)

> Framework: Assumption Mapping (Teresa Torres / Jeff Gothelf)
> Classificação: **Certeza** (o quanto acreditamos) × **Importância** (impacto no negócio se errarmos)
> Quadrantes: 🔴 Crítica (testar primeiro) · 🟡 Importante · 🟢 Segura · ⚪ Irrelevante

### Hipóteses sobre o PROBLEMA

| # | Hipótese | Certeza | Importância | Prioridade |
|---|---------|:-------:|:-----------:|:----------:|
| H01 | Os declarantes perdem deduções por não saber que têm direito a elas | Alta | Alta | 🟢 Segura |
| H02 | O medo de malha fina é a principal emoção negativa associada ao IR | Alta | Alta | 🟢 Segura |
| H03 | Autônomos e MEI têm dificuldade real em separar despesas PF/PJ | Alta | Alta | 🟢 Segura |
| H04 | Investidores iniciantes não sabem quando/quanto pagar de DARF | Média | Alta | 🔴 Crítica |
| H05 | A dor tributária existe 12 meses, não só em abril | Média | **Altíssima** | 🔴 Crítica |
| H06 | A maioria das pessoas perde notas fiscais que poderiam usar para dedução | Alta | Média | 🟡 Importante |

### Hipóteses sobre o COMPORTAMENTO DO USUÁRIO

| # | Hipótese | Certeza | Importância | Prioridade |
|---|---------|:-------:|:-----------:|:----------:|
| H07 | Usuários pagariam por um assistente tributário se vissem a economia antes de assinar | Baixa | **Altíssima** | 🔴 Crítica |
| H08 | O "aha moment" acontece quando o usuário vê a estimativa de economia em <2 min | Baixa | **Altíssima** | 🔴 Crítica |
| H09 | Usuários CLT não vão interagir com o app fora do período de IR | Baixa | Alta | 🔴 Crítica |
| H10 | Usuários confiam em um app para guardar documentos fiscais sensíveis | Baixa | Alta | 🔴 Crítica |
| H11 | Indicação de amigos é o canal de aquisição com maior conversão | Baixa | Alta | 🔴 Crítica |
| H12 | Usuários comparam o preço do GuIA com o custo do contador, não com zero | Média | Alta | 🟡 Importante |

### Hipóteses sobre o MODELO DE NEGÓCIO

| # | Hipótese | Certeza | Importância | Prioridade |
|---|---------|:-------:|:-----------:|:----------:|
| H13 | R$ 9,90/mês é o preço ideal para o tier Pro | Baixa | Alta | 🔴 Crítica |
| H14 | Assinatura anual tem maior LTV que mensal neste produto | Média | Alta | 🟡 Importante |
| H15 | Contadores parceiros pagarão comissão por leads qualificadas do GuIA | Baixa | Média | 🟡 Importante |
| H16 | Usuários freemium se convertem para pago após ver 1ª restituição otimizada | Baixa | **Altíssima** | 🔴 Crítica |

### Hipóteses sobre a SOLUÇÃO

| # | Hipótese | Certeza | Importância | Prioridade |
|---|---------|:-------:|:-----------:|:----------:|
| H17 | IA consegue identificar deduções elegíveis com >90% de precisão | Baixa | **Altíssima** | 🔴 Crítica |
| H18 | OCR de notas fiscais reduz friction suficiente para criar hábito | Baixa | Alta | 🔴 Crítica |
| H19 | Open Finance elimina a barreira de onboarding de dados financeiros | Média | Alta | 🟡 Importante |
| H20 | Usuário prefere ver "você pode economizar R$ 2.500" a ver a alíquota | Alta | Alta | 🟢 Segura |

### Hipóteses sobre OPEN FINANCE e DADOS BANCÁRIOS

| # | Hipótese | Certeza | Importância | Prioridade |
|---|---------|:-------:|:-----------:|:----------:|
| H21 | Usuários conectam a conta bancária quando entendem o benefício antes de autorizar | Baixa | **Altíssima** | 🔴 Crítica |
| H22 | A categorização automática de transações tem precisão ≥ 85% sem edição do usuário | Média | **Altíssima** | 🔴 Crítica |
| H23 | Ver transações categorizadas como "dedutíveis" aumenta o engajamento fora da temporada de IR | Baixa | Alta | 🔴 Crítica |
| H24 | Usuários com conta bancária conectada têm retenção D30 significativamente maior do que sem conta | Baixa | **Altíssima** | 🔴 Crítica |
| H25 | O principal bloqueio para conectar a conta é desconfiança, não inconveniência técnica | Média | Alta | 🟡 Importante |

**Fundamentos:**
- **H21** — Usuários relutam em dar acesso a dados bancários sem ver o benefício imediato. Mostrar preview das deduções identificadas antes de pedir autorização pode dobrar a taxa de conexão.
- **H22** — Se a IA errar categorias tributárias frequentemente, o usuário perde confiança e abandona a feature. Precisão abaixo de 85% exige revisão manual obrigatória (pior experiência).
- **H23** — Este é o principal mecanismo de retenção anual — se o usuário vê todo mês "você tem R$ X em deduções novas", ele não abandona o app em maio.
- **H24** — A conexão bancária cria um "hábito passivo" — o app funciona mesmo sem o usuário fazer nada. Isso é o principal antídoto para o churn pós-temporada.
- **H25** — O fluxo de OAuth com Pluggy é simples (2-3 taps). Se a taxa de conexão for baixa, o problema é confiança (dados bancários), não UX.

### Ranking de hipóteses críticas a validar primeiro

| Rank | Hipótese | Por quê validar primeiro |
|:----:|---------|------------------------|
| 1 | **H08** — Aha moment em <2 min | Se não funcionar, a estratégia de ativação toda colapsa |
| 2 | **H21** — Conexão com benefício visível | Gatilho de adoção do Open Finance: sem conversão aqui, o canal não existe |
| 3 | **H07** — Usuários pagam ao ver economia antes | É o pilar da conversão freemium→pago |
| 4 | **H05** — Dor existe 12 meses | É o fundamento da estratégia de produto anual |
| 5 | **H09** — CLT não usa fora de abril | Ameaça direta ao modelo de assinatura |
| 6 | **H10** — Confiança em guardar documentos | Barreira de adoção crítica para o cofre de notas |
| 7 | **H16** — Conversão após 1ª restituição | Define o ciclo de vida central do produto |
| 8 | **H24** — Retenção com conta conectada | Valida o "hábito passivo" como antídoto ao churn off-season |
| 9 | **H17** — Precisão da IA >90% | Risco de produto: se a IA errar, o produto é inútil |
| 10 | **H22** — Precisão da categorização ≥ 85% | Extensão direta de H17 para transações bancárias importadas |

---

## Artefato 3 — Roteiro de Entrevistas com Usuários

> Objetivo: validar hipóteses críticas H05, H07, H08, H09, H10
> Método: entrevista qualitativa (não-diretiva), 45–60 min, remota ou presencial
> Quantidade alvo: 5 entrevistas por persona = 15 entrevistas totais

### Estrutura geral

| Fase | Tempo | Objetivo |
|------|------:|---------|
| Aquecimento | 5 min | Rapport, contexto da pessoa |
| Exploração do passado | 15 min | Como ela *realmente* resolve hoje |
| Dores e emoções | 15 min | O que incomoda de verdade |
| Comportamento digital | 10 min | Hábitos com apps financeiros |
| Encerramento | 5 min | O que mais pesa na decisão |

**Regras de ouro:**
- Nunca mencionar o GuIA ou apresentar a solução durante a entrevista
- Perguntar sobre comportamento passado, não intenção futura
- Ficar em silêncio após a resposta — deixar a pessoa preencher o silêncio
- Perguntar "por quê?" pelo menos 3 vezes em cada tema relevante

---

### Roteiro A — Clara (Assalariada CLT)

**Aquecimento**
1. Me conta um pouco sobre você — o que você faz, como é sua rotina financeira no dia a dia?
2. Você costuma acompanhar sua vida financeira com algum app ou ferramenta?

**Exploração do IR**
3. Me conta como foi sua última declaração de IR. Por onde você começou?
4. Você fez sozinha ou pediu ajuda de alguém? Como foi essa decisão?
5. Teve algum momento em que ficou travada ou com dúvida? O que aconteceu?
6. Como você se sentiu quando submeteu a declaração? Por quê?

**Deduções e documentos**
7. Você guarda comprovantes médicos, notas fiscais, recibos de escola? Como você faz isso?
8. Já aconteceu de você descobrir depois que podia ter deduzido algo mas não deduziu? Me conta.
9. Como você sabe o que pode ou não deduzir? De onde vem essa informação?

**Fora de abril**
10. Você pensa em IR em algum outro momento do ano além de março/abril? Me conta.
11. Se você soubesse hoje que está pagando mais imposto do que deveria, o que você faria com essa informação?

**Confiança e pagamento**
12. Você já usou algum app que guarda dados financeiros seus? Como foi a experiência de confiar seus dados a ele?
13. Se existisse algo que calculasse automaticamente quanto de imposto você poderia economizar, o quanto isso valeria para você?

**Dados bancários e confiança (5 min)**
- Você usa algum app que tem acesso à sua conta bancária? Como foi a decisão de conectar?
- Se um app pudesse ver seu extrato e te mostrar automaticamente quais gastos você pode deduzir no IR, você conectaria? O que te impediria?
- O que precisaria ter (segurança, marca, garantia) para você se sentir confortável em dar esse acesso?

---

### Roteiro B — Rafael (Autônomo/MEI)

**Aquecimento**
1. Me conta como é sua rotina de trabalho — você emite NF, tem vários clientes, como organiza isso?
2. Você usa alguma ferramenta para controlar suas finanças de autônomo?

**Exploração do IR e MEI**
3. Me conta como foi sua última declaração de IR. Você fez junto com a do MEI ou separado?
4. Como você separa o que é gasto pessoal do que é gasto do negócio? Tem um método?
5. Já teve alguma situação em que você não soube se deduzia ou não uma despesa? O que aconteceu?
6. Você já pagou DARF? Me conta como foi descobrir que precisava pagar.

**Organização tributária**
7. Quando você emite uma NF, você pensa no imposto que vai pagar? Ou só vê isso depois?
8. Você já teve surpresa ruim com imposto — algo que não esperava pagar? Me conta.
9. O que você faria diferente se tivesse mais clareza sobre o impacto tributário de cada decisão financeira?

**Confiança e pagamento**
10. Você já contratou contador? Como foi a experiência — o que foi bom, o que foi ruim?
11. O que precisaria acontecer para você confiar suas informações financeiras a um app?
12. Quanto você pagou de contador no último ano? Você achou que valeu?

**Dados bancários e confiança (5 min)**
- Você usa algum app que tem acesso à sua conta bancária? Como foi a decisão de conectar?
- Se um app pudesse ver seu extrato e te mostrar automaticamente quais gastos você pode deduzir no IR, você conectaria? O que te impediria?
- O que precisaria ter (segurança, marca, garantia) para você se sentir confortável em dar esse acesso?

---

### Roteiro C — Lucas (Investidor Iniciante)

**Aquecimento**
1. Me conta há quanto tempo você investe e o que você tem na carteira hoje.
2. Você acompanha a parte tributária dos seus investimentos ou deixa isso para o IR de abril?

**Exploração do DARF e renda variável**
3. Você já pagou DARF? Me conta como você descobriu que precisava pagar.
4. Já teve algum mês em que você vendeu ações com lucro e depois ficou sem saber o que fazer com o imposto? O que aconteceu?
5. Como você calcula hoje se deve ou não pagar DARF num determinado mês?

**Declaração de IR com investimentos**
6. Na última declaração, como você lançou seus investimentos? Usou o informe da corretora? Como foi?
7. Você tem cripto? Como você declarou? Foi difícil?
8. Já aconteceu de você lançar algo errado na declaração? Como descobriu?

**Fora de abril**
9. Em algum momento do ano você pensa "preciso organizar isso antes do IR"? O que dispara esse pensamento?
10. Se existisse algo que avisasse você no momento da venda se há imposto a pagar e quanto, isso mudaria seu comportamento? Por quê?

**Confiança e pagamento**
11. Você usa algum app para acompanhar sua carteira? Quais dados você já compartilhou com apps financeiros?
12. Quanto você estaria disposto a pagar por algo que eliminasse totalmente o stress tributário dos seus investimentos?

**Dados bancários e confiança (5 min)**
- Você usa algum app que tem acesso à sua conta bancária? Como foi a decisão de conectar?
- Se um app pudesse ver seu extrato e te mostrar automaticamente quais gastos você pode deduzir no IR, você conectaria? O que te impediria?
- O que precisaria ter (segurança, marca, garantia) para você se sentir confortável em dar esse acesso?

---

## Artefato 4 — Plano de Validação das Hipóteses

| Hipótese | Método de Validação | Critério de Sucesso | Falso = pivotar para |
|---------|-------------------|--------------------|--------------------|
| **H05** — Dor existe 12 meses | Entrevistas qualitativas (Roteiros A/B/C) | ≥7/10 relatam episódio tributário fora de abril | Produto sazonal — focar só na temporada de IR |
| **H07** — Pagam ao ver economia antes | Smoke test: landing page com calculadora → CTA "Assine por R$ 9,90" | ≥5% de conversão visitante→pagamento | Preço maior; testar gratuito com upsell posterior |
| **H08** — Aha moment em <2 min | Teste de usabilidade com protótipo cronometrado | ≥70% concluem em <2 min; NPS do momento ≥8 | Redesenhar onboarding; reduzir campos obrigatórios |
| **H09** — CLT não usa fora de abril | Entrevistas (Roteiro A) | ≥6/10 CLTs relatam zero ação tributária fora de abril | Redesenhar proposta de valor anual |
| **H10** — Confiança em dados | Entrevistas — seção "confiança e pagamento" | ≥6/10 confiariam com ao menos 1 condição superável | Enfatizar segurança no onboarding; parceria com marca de confiança |
| **H13** — R$ 9,90 é o preço ideal | Teste A/B em landing page: R$ 7,90 / R$ 9,90 / R$ 14,90 | Maior receita por visitante (não maior conversão) | Ajustar tier Pro |
| **H16** — Conversão após 1ª restituição | Cohort analysis: taxa de renovação no ano seguinte | ≥60% renovam para o ano seguinte | Criar programa de fidelidade; melhorar engajamento off-season |
| **H17** — Precisão da IA >90% | Backtesting com 50 declarantes reais | Erro <10% nas deduções sugeridas | Restringir escopo para CLT simples; ampliar gradualmente |

### Sequência de execução (Hypothesis Testing Sprint)

```
Semana 1–2:   Entrevistas qualitativas (15 entrevistas — H05, H09, H10)
Semana 3:     Síntese e atualização do Assumption Map
Semana 4:     Protótipo navegável do onboarding (Figma)
Semana 5:     Teste de usabilidade com 5 usuários (H08)
Semana 6:     Landing page com calculadora de economia
Semana 7–8:   Smoke test de conversão / A/B de preço (H07, H13)
Semana 9:     Síntese final → decisão de Problem-Solution Fit
```

---

## Artefato 5 — Problem-Solution Fit Canvas

### Problema confirmado

| Dimensão | Evidência / Hipótese |
|---------|---------------------|
| **Quem sofre** | 41M declarantes, com intensidade maior em autônomos, investidores e famílias com dependentes |
| **Qual a dor** | Perde deduções por desconhecimento + medo de malha fina + confusão tributária ao longo do ano |
| **Frequência** | A dor de *acúmulo* é anual; o *pânico* é sazonal (março-abril) |
| **Alternativas atuais** | Portal da Receita (complexo), contador (caro e pontual), apps de IR (superficiais) |
| **Por que as alternativas falham** | Nenhuma acompanha o contribuinte o ano todo nem usa IA para otimizar proativamente |

### Solução proposta

| Dimensão | GuIA |
|---------|------|
| **Job resolvido** | Pagar o menor imposto legal possível, com segurança, sem esforço e o ano todo |
| **Mecanismo central** | Motor de IA que identifica deduções elegíveis em tempo real + cofre de documentos + alertas proativos + Importação automática de extratos via Open Finance (Pluggy) com categorização tributária automática de cada transação |
| **Aha moment** | Usuário vê "você pode economizar R$ X" em menos de 2 minutos após o cadastro |
| **Diferencial defensável** | Dados acumulados ao longo do ano → IA fica mais precisa por contribuinte → switching cost natural. Dados bancários reais acumulados ao longo do ano (não declarados pelo usuário) tornam o perfil fiscal progressivamente mais completo e preciso |
| **Forma de entrega** | App mobile + web; freemium com upsell baseado em economia demonstrada |

### Critério de Problem-Solution Fit alcançado

O GuIA atingiu Problem-Solution Fit quando:

1. ≥40% dos entrevistados dizem que ficariam "muito desapontados" se o produto deixasse de existir *(Sean Ellis Test)*
2. ≥70% conseguem completar o onboarding e chegar ao aha moment em <2 min sem assistência
3. ≥5% de conversão orgânica visitante→pagante no smoke test de landing page
4. ≥60% dos usuários que fizeram a declaração via GuIA renovam no ano seguinte

### Riscos de invalidação

| Risco | Sinal de alerta | Resposta |
|-------|----------------|---------|
| Usuários não percebem valor fora de abril | <20% usam o app entre maio e janeiro | Pivotar para produto sazonal premium |
| Confiança em dados é barreira intransponível | <50% dispostos a compartilhar dados bancários | Focar em dados manuais; adiar Open Finance |
| IA não é precisa o suficiente | Erros relatados por ≥20% dos usuários | Restringir escopo para CLT simples; ampliar gradualmente |
| Preço não sustenta o CAC | LTV/CAC < 3x após 6 meses | Revisar tiers; testar modelo anual |

---

## Status dos Artefatos — Módulo 02

| # | Artefato | Status |
|---|---------|--------|
| 1 | Jobs to be Done (JTBD) por persona | ✅ Concluído |
| 2 | Mapeamento de Hipóteses (Assumption Map) | ✅ Concluído |
| 3 | Roteiro de Entrevistas (3 personas) | ✅ Concluído |
| 4 | Plano de Validação das Hipóteses | ✅ Concluído |
| 5 | Problem-Solution Fit Canvas | ✅ Concluído |

**Próxima etapa:** Módulo 03 — Design & Delivery (Backlog, User Stories, critérios de aceite)
