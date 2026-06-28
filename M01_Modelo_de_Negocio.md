# GuIA — Artefatos do Módulo 01
**MBA Tera · Liderança e Estratégia de Produtos Digitais na Era da IA**
**Módulo 01 — Digital Strategy: Estratégia de Negócios e Gestão de Produtos Digitais**
**Produzido em:** Junho 2026

> **Escopo do produto:** Brasil exclusivamente. Foco em IRPF de pessoa física. Open Finance regulado pelo BCB. Legislação tributária brasileira (Lei 7.713/88, IN RFB). Apenas português BR. Expansão LATAM apenas no Ano 3+.

---

## Contexto do Produto

**GuIA** (Guia + IA) é um assistente financeiro pessoal com IA para brasileiros. Seu diferencial central é ser um assistente *anual* — não uma ferramenta pontual de abril.

**Visão:** "Ser o assistente financeiro pessoal que todo brasileiro merece ter — organizando sua vida financeira o ano todo, garantindo que você pague o menor imposto legal possível e transforme sua restituição em um passo rumo às suas metas de vida."

**Tamanho da oportunidade:**
- 41M+ declarações de IRPF por ano no Brasil
- ~R$ 40 bilhões em restituições pagas anualmente
- ~75% dos contribuintes cometem erros que geram multa ou perda de restituição

---

## Artefato 1 — Business Model Canvas (BMC)

> Framework: Business Model Canvas (Osterwalder) | 9 blocos aplicados ao GuIA

### OFERTA DE VALOR *(centro — O QUÊ?)*

**Para Clara (CLT):**
Declaração de IR sem medo — o GuIA encontra deduções que você esqueceria, calcula automaticamente e garante que você paga o menor imposto legal possível. Resultado: mais restituição, zero malha fina.

**Para Rafael (Autônomo/MEI):**
Controle PF/PJ sem confusão — separa despesas dedutíveis, orienta no regime tributário correto e avisa quando emitir DARF.

**Para Lucas (Investidor):**
Tributação de renda variável sem dor de cabeça — consolida ações, FIIs, cripto, Tesouro e calcula o imposto correto por classe de ativo.

**Proposta central:** Assistente financeiro pessoal com IA que organiza sua vida tributária o ano todo — não apenas em abril.

---

### SEGMENTOS DE CLIENTES *(direito — QUEM?)*

| Segmento | Perfil | Tamanho Est. |
|---------|--------|-------------|
| Assalariados CLT | Renda R$ 3k–15k/mês, plano de saúde, dependentes | ~25M declarantes |
| Autônomos/MEI | Renda variável R$ 5k–30k, emite NF | ~8M declarantes |
| Investidores Iniciantes | Renda R$ 10k+, ações/FIIs/cripto | ~4M declarantes |
| Famílias com Dependentes | Filhos, educação, saúde — múltiplas deduções | ~10M declarantes |

---

### CANAIS *(direito — QUEM?)*

- **Direto:** App mobile (iOS/Android) + Web app
- **Orgânico:** SEO / blog tributário / conteúdo no Instagram e YouTube
- **Performance:** Google Ads (search "declarar IR"), Meta Ads
- **Parcerias:** FinTechs (Nubank, C6), apps de finanças (Mobills), contadores parceiros
- **Viral:** Programa de indicação "Indique 3, ganhe 1 mês grátis"

---

### RELACIONAMENTO COM CLIENTES *(direito — QUEM?)*

- **Self-service automatizado:** onboarding guiado em <2 min, simulação imediata de economia
- **Comunidade:** fórum de dúvidas, webinars "Como investir sua restituição"
- **Notificações contextuais:** alertas de prazo, deduções não aproveitadas, DARF a pagar
- **Premium:** acesso a especialista tributário (chat/consultoria)
- **Gamificação:** badges, streaks de organização financeira

---

### FONTES DE RECEITA *(base — POR QUÊ?)*

| Tier | Preço | O que inclui |
|------|-------|-------------|
| **Básico (Freemium)** | Gratuito | Declaração simples, 1 fonte de renda |
| **Pro** | R$ 9,90/mês | Múltiplas fontes, importação bancária, simulador |
| **Premium** | R$ 29,90/mês | Investimentos, consultoria, planejamento anual |

**Modelo primário:** SaaS com assinatura mensal (MRR)
**Modelo secundário:** Comissão por indicação de contadores parceiros / afiliados

---

### RECURSOS-CHAVE *(esquerdo — COMO?)*

- **Tecnológicos:** motor de IA de otimização tributária, OCR de notas fiscais, integração com Receita Federal (e-CAC / PGFN)
- **Legais/Regulatórios:** base de conhecimento atualizada (Lei 7.713/88, IN RFB, CARF), equipe jurídico-tributária
- **Dados:** base de regras tributárias atualizadas em <24h após mudança da Receita Federal
- **Marca:** posicionamento de confiança e autoridade tributária
- **Humanos:** time de produto, engenharia e especialistas tributários
- **API de IA (Anthropic Claude):** motor de linguagem para chat tributário e categorização; haiku para tarefas em batch, sonnet para interações com o usuário
- **Open Finance via Pluggy:** acesso regulado a extratos, saldo e investimentos de todos os bancos participantes do BCB

---

### ATIVIDADES-CHAVE *(esquerdo — COMO?)*

- Desenvolvimento e manutenção do motor de IA tributário
- Atualização contínua da base legal (IN RFB, CARF, mudanças legislativas)
- Aquisição e ativação de usuários (growth loops)
- Conformidade LGPD e segurança de dados fiscais sensíveis
- Parcerias com FinTechs e contadores

---

### PARCERIAS-CHAVE *(esquerdo — COMO?)*

| Parceiro | Tipo | Valor |
|---------|------|-------|
| FinTechs (Nubank, C6, Inter) | Distribuição / co-marketing | Acesso à base de usuários |
| Receita Federal / GOV.BR | API pública (e-CAC) | Dados oficiais do contribuinte |
| Contadores e escritórios tributários | Canal + referência | Credibilidade + casos complexos |
| Apps de finanças pessoais (Mobills, Organizze) | Integração / API | Cross-sell |
| OpenAI / Anthropic / AWS | Infra de IA | Motor de otimização |
| **Pluggy** (agregador Open Finance) | Integração técnica regulada | SDK de conexão bancária regulada pelo BCB; cobre Mercado Pago, Nubank, Itaú, Bradesco, BB, Santander, Inter, C6, XP e 800+ instituições participantes do Open Finance Brasil |
| **Anthropic (Claude API)** | Infra de IA | LLM para chat tributário (claude-sonnet-4-6) e categorização de transações (claude-haiku-4-5) |
| **AWS Textract** | Infra de OCR | OCR para informes de rendimento e documentos fiscais |

---

### ESTRUTURA DE CUSTOS *(base — POR QUÊ?)*

**Custos fixos principais:**
- Time de engenharia e IA (maior custo)
- Infra cloud (AWS/GCP) + APIs de IA
- Equipe jurídico-tributária (atualização legislativa)
- Marketing de conteúdo

**Custos variáveis:**
- CAC (Performance marketing): R$ 12–18/usuário pago
- Custo de atendimento Premium (especialistas)

**Modelo:** orientado por escala — alto custo fixo inicial, margem crescente com volume de usuários pagantes.

---

## Artefato 2 — Padrões de Modelo de Negócio (BMC Navigator)

> Etapa Ideação: identificar padrões que o GuIA pode adotar/hibridizar

### Padrão 1 — FREEMIUM

**O que é:** versão gratuita que captura massa de usuários; monetiza via upgrade para planos pagos.

**Como se aplica ao GuIA:**
- Básico (grátis) → declaração simples, 1 fonte de renda → captura 41M declarantes
- Pro/Premium → ativa os que querem otimização real
- Alavanca natural: usuário vê "você poderia ter economizado R$ 2.500 — desbloqueie Pro"

**Por que funciona:** TAM enorme, produto sazonal com momento emocional forte (restituição), baixo custo marginal para servir o tier gratuito.

---

### Padrão 2 — LONG TAIL

**O que é:** atender nicho de alta variedade que plataformas grandes ignoram; lucro vem da cauda, não do blockbuster.

**Como se aplica ao GuIA:**
- O mercado de IR é dominado por contadores e pelo portal da Receita — nenhum atende bem o autônomo com 5 fontes de renda + cripto + dependente + previdência privada
- GuIA entra pela cauda: casos complexos que contadores cobrariam R$ 300–800 para resolver
- Cada nicho (MEI, investidor, artista, influencer) tem regras tributárias específicas → GuIA cobre todos com IA

---

### Padrão 3 — SUBSCRIPTION (SaaS recorrente)

**O que é:** receita previsível via assinatura mensal/anual.

**Como se aplica ao GuIA:**
- O grande insight é que o IR *parece* sazonal, mas o planejamento tributário legal é anual
- Assinatura anual (vs. mensal) muda o comportamento: usuário mantém o app ativo o ano todo para maximizar deduções ao longo dos meses
- Vantagem competitiva: concorrentes como Imposto.me cobram por declaração (uso pontual); GuIA cobra por planejamento contínuo

---

### Padrão 4 — PLATFORM / TWO-SIDED MARKET

**O que é:** conectar dois grupos que se beneficiam mutuamente (efeito de rede entre eles).

**Como se aplica ao GuIA:**
- Lado 1: Contribuintes (usuários do GuIA)
- Lado 2: Contadores parceiros e consultores tributários
- Modelo: casos que ultrapassam a capacidade da IA são roteados para contador parceiro (marketplace de contadores dentro do app)
- GuIA cobra comissão do contador pela lead qualificada; usuário recebe atendimento humano sem sair da plataforma

---

## Artefato 3 — Avaliação NABC

> Framework: Need · Approach · Benefit · Competition
> Aplicado ao modelo híbrido principal do GuIA: **Freemium + Subscription + Long Tail**

### N — Need (Necessidade)

75% dos 41M declarantes de IR no Brasil cometem erros que resultam em multa ou perda de restituição. Nenhuma solução atual resolve o problema de forma contínua e acessível: o portal da Receita Federal é complexo, contadores são caros (R$ 300–800/declaração) e apps existentes são pontuais (só funcionam em março/abril). A dor existe 12 meses por ano — renda variável, DARF mensal, deduções médicas que precisam ser guardadas ao longo do ano — mas nenhum produto acompanha o contribuinte durante toda essa jornada.

### A — Approach (Abordagem)

GuIA adota modelo **Freemium + SaaS anual + Long Tail:**
1. Entrada gratuita via declaração simples (captura massa)
2. Upsell para Pro/Premium baseado em "economia potencial calculada em tempo real" (aha moment)
3. Cobertura de casos complexos (autônomos, investidores, múltiplas fontes) que concorrentes ignoram
4. Engajamento anual — não só em abril — via controle financeiro contínuo, alertas de DARF, cofre de notas fiscais e planejamento de deduções futuras
5. Marketplace de contadores para casos que ultrapassam a IA (receita adicional + confiança)

### B — Benefit (Benefício)

| Para o usuário | Para o GuIA |
|---------------|-----------|
| Economia média estimada de R$ 1.500–3.000/ano em impostos | MRR previsível e crescente |
| Tranquilidade tributária durante 12 meses | LTV alto: usuário que experimenta uma restituição maior renova |
| Onboarding em <2 min com resultado visível imediato | CAC baixo via viral loop (usuário compartilha economia obtida) |
| Redução de risco de malha fina | Margem crescente com escala (custo marginal baixo) |

### C — Competition (Competição)

| Alternativa | Fraqueza principal | Diferencial do GuIA |
|------------|-------------------|-------------------|
| Portal Receita Federal (gratuito) | Complexo, sem inteligência, sem sugestões | GuIA é intuitivo e proativo |
| Contador (R$ 300–800) | Caro, só em abril, sem educação contínua | GuIA é 10x mais barato e está disponível 24/7 |
| Imposto.me / Minha Declaração | Pontual, sem planejamento anual, sem IA de otimização | GuIA é assistente anual com IA |
| Apps de finanças (Mobills, Organizze) | Não tratam de tributação | GuIA integra finanças + IR em um só lugar |

**Vantagem defensável:** quanto mais dados o usuário alimenta ao longo do ano, melhor a IA fica para aquele contribuinte específico — criando switching cost natural.

---

## Artefato 4 — Curva de Valor

> Framework: Blue Ocean Strategy — mapear atributos do setor e posicionar o GuIA

**Concorrentes mapeados:**
- A: Portal da Receita Federal (gratuito, oficial)
- B: Contador tradicional
- C: Apps pontuais de IR (Imposto.me, Minha Declaração)
- D: **GuIA** (posicionamento proposto)

### Tabela de atributos *(escala 1–5)*

| Atributo | Receita Federal | Contador | Apps IR | GuIA |
|---------|:--------------:|:-------:|:-------:|:----:|
| Preço acessível | 5 | 1 | 3 | 4 |
| Facilidade de uso | 1 | 4 | 3 | 5 |
| Sugestão de deduções | 1 | 4 | 2 | 5 |
| Otimização tributária com IA | 1 | 3 | 1 | 5 |
| Disponibilidade 12 meses/ano | 2 | 2 | 1 | 5 |
| Controle financeiro contínuo | 1 | 1 | 1 | 4 |
| Cofre de documentos/notas fiscais | 1 | 2 | 1 | 5 |
| Cobertura de casos complexos | 3 | 5 | 1 | 4 |
| Integração com bancos/corretoras | 1 | 1 | 2 | 4 |
| Integração bancária automática (Open Finance) | 1 | 1 | 1 | **5** |
| Conformidade legal garantida | 5 | 5 | 3 | 5 |
| Velocidade (resultado imediato) | 2 | 3 | 4 | 5 |
| Consultoria humana disponível | 1 | 5 | 1 | 3 |

### Leitura estratégica (Framework ERRC)

| Ação | O que |
|------|-------|
| **Eliminar** | Complexidade do processo de declaração; dependência de agenda/disponibilidade do profissional |
| **Reduzir** | Custo (vs. contador); curva de aprendizagem técnica |
| **Aumentar** | Facilidade de uso; velocidade de resultado; conformidade legal |
| **Criar** | Engajamento tributário anual; motor de IA de otimização com sugestões proativas; cofre inteligente de documentos com OCR; integração financeira completa; **Chat tributário com IA** (LLM com persona de especialista — responde dúvidas do usuário em linguagem natural, citando legislação) |

> Esta é a curva Blue Ocean do GuIA: alta facilidade + baixo custo + inteligência anual — nenhum concorrente atual ocupa este espaço.

---

## Artefato 5 — Análise SWOT

> Síntese estratégica — interno (S/W) vs. externo (O/T)

### FORÇAS *(Strengths — interno)*

**S1. Proposta única de valor anual**
Único assistente tributário que acompanha o contribuinte 12 meses — não apenas em abril. Isso cria engajamento e diferenciação que nenhum concorrente tem.

**S2. Motor de IA proprietário**
IA treinada em legislação brasileira (Lei 7.713/88, IN RFB, CARF) com atualização em <24h após mudanças — expertise difícil de replicar rapidamente.

**S3. Modelo de negócio escalável**
Freemium + SaaS: alto custo fixo inicial mas margem crescente exponencialmente com escala. CAC se reduz com o viral loop (compartilhamento de economia obtida).

**S4. TAM enorme e captivo**
41M declarantes obrigatórios por lei — mercado cativo que *precisa* resolver o problema todo ano.

**S5. Dados como ativo defensável**
Quanto mais o usuário usa, mais dados tributários acumula — cria switching cost natural e melhora a IA individualmente para cada contribuinte.

---

### FRAQUEZAS *(Weaknesses — interno)*

**W1. Complexidade regulatória alta**
Legislação tributária muda frequentemente (IN RFB, CARF, STJ). Custo de manutenção legal é permanente e não escalável sozinho.

**W2. Produto novo sem prova de credibilidade**
Tributação envolve confiança. Usuário hesita em confiar dados fiscais sensíveis a um app desconhecido. Construção de marca leva tempo.

**W3. Sazonalidade concentrada (risco de churn)**
Apesar da proposta anual, o pico de uso é março-abril. Risco de usuários cancelarem após a declaração se não perceberem valor fora da temporada.

**W4. Dependência de integrações externas**
Integração com bancos, corretoras e e-CAC depende de APIs de terceiros — vulnerabilidade a mudanças de política dessas plataformas.

---

### OPORTUNIDADES *(Opportunities — externo)*

**O1. Open Finance Brasil**
Regulação do Banco Central permite integração automática de dados bancários e de investimentos — reduz fricção de onboarding e enriquece a análise tributária.

**O2. Crescimento de MEI e autônomos**
Brasil tem >15M de MEIs e cresce 10%/ano. Segmento com alta dor tributária e pouca solução específica disponível.

**O3. Educação financeira em ascensão**
Geração Z e Millennials buscam ferramentas digitais para finanças pessoais — abertura cultural para pagar por app de gestão financeira/tributária.

**O4. Reforma Tributária (2025–2027)**
A transição para o novo sistema tributário (IBS, CBS, Imposto Seletivo) vai gerar confusão massiva — janela de oportunidade para GuIA posicionar-se como guia de transição.

**O5. Mercado de IA em maturação**
Modelos de linguagem cada vez mais capazes e baratos permitem construir motor tributário mais sofisticado com custo decrescente.

---

### AMEAÇAS *(Threats — externo)*

**T1. Entrada de big techs**
Nubank, Mercado Pago ou PicPay podem lançar funcionalidade de IR integrada ao seu app financeiro — distribuição massiva já consolidada.

**T2. Concorrência de contadores digitalizados**
Plataformas de contabilidade online (Contabilizei, Agilize) podem expandir para o segmento PF com declaração de IR.

**T3. Mudanças regulatórias adversas**
Receita Federal pode restringir acesso a dados via e-CAC ou criar barreiras à integração de terceiros com seus sistemas.

**T4. Resistência cultural ao dado fiscal**
Brasileiro historicamente desconfia de compartilhar dados com o governo ou com terceiros — barreira de adoção, especialmente para os dados mais sensíveis (renda, patrimônio).

**T5. Declaração pré-preenchida avançando**
Receita Federal está expandindo a declaração pré-preenchida — se evoluir bem, pode reduzir a percepção de necessidade de ferramenta externa.

---

### Cruzamentos estratégicos

| | Oportunidades | Ameaças |
|--|--------------|--------|
| **Forças** | **S1+O4:** Posicionar GuIA como o guia da Reforma Tributária — lançar campanha educativa antes da confusão começar. **S5+O1:** Open Finance + dados proprietários = vantagem de dado impossível de replicar rapidamente por big techs. | **S2+T5:** Motor de IA de *otimização* vai além da declaração pré-preenchida — não são concorrentes diretos. **S4+T1:** Ser referência de nicho (IR) antes das big techs chegarem — construir marca tributária antes que elas expandam. |
| **Fraquezas** | **W2+O3:** Geração educada financeiramente é mais propensa a confiar em novo app — focar aquisição neste segmento primeiro para construir credibilidade. | **W1+T3:** Montar parceria com escritório tributário de referência para blindar risco regulatório e acelerar credibilidade. |

---

## Status dos Artefatos — Módulo 01

| # | Artefato | Status |
|---|---------|--------|
| — | Product Vision Document | Concluído (anterior) |
| — | Personas (Clara, Rafael, Família Silva, Lucas) | Concluído (anterior) |
| — | Balanced Scorecard (4 perspectivas) | Concluído (anterior) |
| — | Growth Strategy (6 camadas) | Concluído (anterior) |
| 1 | Business Model Canvas (9 blocos) | ✅ Concluído |
| 2 | Padrões de modelo de negócio (BMC Navigator) | ✅ Concluído |
| 3 | Avaliação NABC | ✅ Concluído |
| 4 | Curva de Valor (GuIA vs 3 concorrentes) | ✅ Concluído |
| 5 | Análise SWOT com cruzamentos estratégicos | ✅ Concluído |

**Próxima etapa:** Módulo 02 — Discovery e Validação (pesquisa com usuários, hipóteses de produto)
