# GuIA — Projeto Final do MBA
### Capstone de Produto Digital | Síntese dos 7 Módulos

> **GuIA — Assistente financeiro pessoal com IA para brasileiros.**
> Declaração de IRPF + planejamento tributário anual, o ano todo (não só em abril).
>
> **Posicionamento:** *"Pare de temer o Leão. O GuIA cuida do seu IR o ano todo — não só em abril."*

> **Escopo:** Produto exclusivamente para o Brasil. Foco em IRPF de pessoa física. Open Finance regulado pelo BCB. Legislação tributária brasileira (Lei 7.713/88, IN RFB). Apenas português BR. Expansão LATAM apenas no Ano 3+ do roadmap.

---

## SEÇÃO 1 — Executive Summary

O GuIA nasce de uma constatação simples e brutal: **41 milhões de brasileiros declaram Imposto de Renda todos os anos, R$ 40 bilhões em restituições são liberados anualmente, e 75% dos declarantes cometem erros que geram multa, caem na malha fina ou perdem dinheiro de restituição.** O sistema tributário brasileiro é desenhado para o contribuinte perder — e a maioria perde.

O mercado atual oferece três respostas, todas insuficientes. O **Portal da Receita Federal** é gratuito, porém complexo e hostil ao leigo. Os **contadores** cobram R$ 300–800 por declaração, mas atuam de forma pontual — aparecem em abril e somem. Os **apps de IR pontuais** (Imposto.me e similares) resolvem o preenchimento de uma única declaração, mas tratam o IR como um evento anual de pânico, não como uma gestão contínua.

O GuIA rompe essa lógica. Somos o **único assistente tributário anual com IA** — cuidamos do imposto de renda o ano inteiro, transformando um momento de medo em uma gestão tranquila e proativa. Captamos rendimentos, despesas dedutíveis e eventos tributáveis ao longo dos 12 meses, antecipamos a economia possível, e na hora da declaração entregamos tudo pronto, otimizado e auditável.

Nossa **North Star Metric** é direta e alinhada ao valor real entregue: **"Reais economizados em impostos por usuário ativo por ano".** Não medimos vaidade — medimos dinheiro que volta ao bolso do brasileiro.

O modelo é **freemium em três tiers**: Básico (grátis), Pro (R$ 9,90/mês) e Premium (R$ 29,90/mês). A monetização acompanha o momento de maior percepção de valor — quando o usuário *vê* a economia projetada.

Nossos **OKRs de 12 meses** são ambiciosos e mensuráveis: **250 mil usuários cadastrados** e **R$ 500 mil de MRR**. O roadmap percorre quatro estágios — MVP (4 meses), V1 (5 meses), V2 (9 meses) e Plataforma (Ano 3).

A espinha dorsal técnica combina **Rules Engine determinístico + OCR + ML de classificação + LLM + RAG** sobre fontes oficiais (Instruções Normativas da RFB, jurisprudência do CARF e do STJ), governada por **5 Princípios de IA Responsável** — porque em matéria fiscal, alucinação não é bug: é multa.

As projeções financeiras detalhadas (Seção 10) mostram um negócio com **economia unitária saudável desde cedo**: payback de CAC em ~1 mês já no Mês 12, relação LTV/CAC superior a 16x no Ano 2, e uma curva de MRR que sai de R$ 596 no Mês 1 para **R$ 347 mil no Mês 24** — convergindo para o ARR superior a R$ 4 milhões.

Este documento sintetiza os 7 módulos do MBA em uma tese de produto coesa: o problema, o produto, a validação, o modelo de negócio, a estratégia de mercado, o roadmap, a camada de IA, as métricas, as projeções financeiras, a liderança, os riscos e os próximos passos.

---

## SEÇÃO 2 — O Problema

### 2.1 A dor estrutural

O Imposto de Renda da Pessoa Física brasileiro é um dos sistemas tributários mais complexos do mundo para o cidadão comum. A combinação de regras mutáveis a cada ano, formulários extensos, terminologia jurídico-fiscal e penalidades severas cria um ambiente de **medo e procrastinação**. O resultado é um padrão de comportamento previsível e custoso:

- **75% dos declarantes cometem erros** — desde omissão de rendimentos até deduções mal informadas, gerando malha fina, multas e perda de restituição.
- O brasileiro encara o IR como um **evento anual de pânico**, concentrado em abril, sem nenhuma gestão ao longo do ano.
- Quem poderia deduzir mais (saúde, educação, previdência, dependentes) **não o faz por desconhecimento**, deixando dinheiro na mesa.
- Autônomos e MEIs vivem em **insegurança permanente** sobre carnê-leão, DARF e a fronteira entre PF e PJ.

### 2.2 Dimensionamento da oportunidade

| Indicador | Valor | Implicação para o GuIA |
|---|---|---|
| Declarantes de IRPF/ano | 41 milhões+ | TAM massivo e recorrente |
| Restituições liberadas/ano | R$ 40 bilhões | Valor tangível a otimizar |
| Declarantes que erram | ~75% (≈30,7 mi) | Dor aguda e generalizada |
| Custo médio de contador | R$ 300–800/ano | Âncora de preço favorável |
| Sazonalidade da concorrência | 100% pontual (abril) | Janela de diferenciação anual |

### 2.3 Personas

| Persona | Perfil | Dor central | O que o GuIA resolve |
|---|---|---|---|
| **Clara** | 32 anos, CLT assalariada | "Será que estou deduzindo tudo o que posso? Tenho medo de errar." | Importa informe de rendimentos, sugere deduções, prevê restituição |
| **Rafael** | 41 anos, Autônomo/MEI | Carnê-leão, DARF mensal, confusão PF/PJ | Gestão contínua de receitas/despesas, alertas de obrigações |
| **Lucas** | 28 anos, Investidor iniciante | Bolsa, cripto, FIIs — não sabe declarar nem calcular DARF | Integração B3, cálculo de ganho de capital, apuração mensal |
| **Família Silva** | Casal com dependentes | Otimizar quem declara o quê; saúde e educação dos filhos | Simulação conjunta x separada, maximização de deduções |

### 2.4 Por que agora

Três forças convergem. **(1) Maturidade técnica:** LLMs e RAG tornaram viável interpretar normas fiscais e conversar com o usuário em linguagem natural com custo aceitável. **(2) Abertura de dados:** SERPRO, Open Finance/Pluggy, B3 API e NFS-e Nacional permitem captar dados financeiros do usuário com consentimento, automatizando o que antes era digitação manual. **(3) Comportamento:** o brasileiro já confia em fintechs para sua vida financeira — falta apenas a camada tributária inteligente.

---

## SEÇÃO 3 — O Produto

### 3.1 Visão

O GuIA é um **copiloto tributário pessoal** que acompanha o usuário durante todo o ano fiscal, não apenas no período de declaração. Ele captura eventos financeiros, classifica-os, calcula impacto tributário, projeta economia e — na hora certa — gera a declaração otimizada e auditável.

### 3.2 Jornada do usuário

1. **Onboarding (aha moment < 2 min):** o usuário conecta seu informe de rendimentos ou autoriza Open Finance; o GuIA já mostra uma **primeira estimativa de restituição/economia**.
2. **Captura contínua:** ao longo do ano, despesas dedutíveis (saúde, educação, previdência), rendimentos e investimentos são importados automaticamente via APIs.
3. **Classificação inteligente:** OCR + ML categorizam notas, recibos e lançamentos.
4. **Projeção proativa:** o GuIA alerta — "você pode economizar R$ X declarando isso" — e orienta ações antes do fim do ano.
5. **Declaração assistida:** em abril, a declaração sai pronta, revisada pelo Rules Engine, com explicações em linguagem natural.
6. **Pós-declaração:** acompanhamento de restituição (SERPRO) e planejamento para o próximo ciclo.

### 3.3 Funcionalidades por tier

| Funcionalidade | Básico (Grátis) | Pro (R$ 9,90/mês) | Premium (R$ 29,90/mês) |
|---|---|---|---|
| Estimativa de restituição | ✓ | ✓ | ✓ |
| Importação de informe de rendimentos | ✓ | ✓ | ✓ |
| Chat tributário com IA | Limitado | Ilimitado | Ilimitado |
| Captura contínua (Open Finance) | — | ✓ | ✓ |
| Integração B3 / cripto / ganho de capital | — | ✓ | ✓ |
| Carnê-leão / DARF automatizado | — | Básico | Completo |
| Simulação conjunta x separada (família) | — | — | ✓ |
| Otimização proativa de deduções | — | ✓ | ✓ |
| Geração de declaração otimizada | — | ✓ | ✓ |
| Revisão anti-malha-fina | — | ✓ | ✓ |
| Suporte humano especializado | — | — | ✓ |

### 3.4 Open Finance e Conexão Bancária

O GuIA conecta às contas bancárias do usuário via **Open Finance Brasil** — o maior ecossistema de dados financeiros abertos do mundo, com 55M+ usuários ativos e regulado pelo Banco Central.

**Como funciona:**
1. Usuário clica "Conectar minha conta" → Pluggy Widget abre
2. Seleciona o banco (Mercado Pago, Nubank, Itaú, BB, Bradesco, Santander, Inter, C6, XP e 800+ bancos)
3. Autoriza via OAuth 2.0 — fluxo Open Finance (não compartilha senha)
4. GuIA importa extrato dos últimos 12 meses
5. IA categoriza cada transação como "DEDUTÍVEL" ou não
6. Dashboard mostra total de deduções identificadas automaticamente

**Integrador Open Finance:** Pluggy (pluggy.ai) — cobre todos os participantes obrigatórios do Open Finance, incluindo Mercado Pago (que participa das Fases 2 e 3). A API direta do Mercado Pago é focada em pagamentos — para leitura de dados financeiros pessoais, o caminho regulado é via Pluggy.

**Resultado imediato para o usuário:** "Encontramos R$ 1.847 em deduções de IR no seu extrato de 2025 — você não precisou guardar nenhum comprovante."

### 3.5 Diferencial competitivo

O GuIA é o **único assistente tributário anual com IA**. Enquanto os concorrentes operam no modelo "abril-e-some", nós operamos no modelo "gestão contínua". Essa diferença não é cosmética: ela muda a economia do usuário (mais deduções capturadas, menos erros) e muda a economia do negócio (relacionamento recorrente, churn baixo, monetização ancorada em valor percebido).

---

## SEÇÃO 4 — Validação e Hipóteses

### 4.1 Assumption Map e hipóteses críticas

Todo produto é uma pilha de apostas. Mapeamos as hipóteses em um Assumption Map (eixos: impacto x incerteza) e priorizamos as de **alto impacto + alta incerteza** para teste imediato.

| ID | Hipótese | Por que é crítica | Como validar | Critério de sucesso |
|---|---|---|---|---|
| **H08** | O usuário atinge o "aha moment" em < 2 min | Define ativação e retenção | Teste de onboarding com cohort; medir time-to-value | ≥ 60% dos novos veem estimativa em < 2 min |
| **H07** | O usuário paga ao *ver* a economia projetada | Define conversão freemium→pago | A/B do paywall acionado pós-projeção | Conversão ≥ 8% no Ano 1 |
| **H05** | Existe dor tributária *anual* (não só em abril) | Justifica todo o posicionamento | Entrevistas + engajamento fora de abril | ≥ 30% dos ativos retornam fora do pico |
| **H09** | CLT engaja com o produto fora de abril | Sustenta retenção da maior persona | Cohort de retenção mensal de CLTs | Retenção M3 ≥ 35% para CLTs |
| **H16** | Usuário converte após receber a restituição | Janela de monetização pós-valor | Campanha pós-restituição (SERPRO) | Uplift de conversão ≥ 20% no período |

### 4.2 Estratégia de validação

Adotamos **descoberta contínua (continuous discovery)** combinada com experimentação quantitativa:

- **Qualitativo:** entrevistas semanais com as 4 personas, testes de usabilidade no onboarding, análise de objeções no paywall.
- **Quantitativo:** A/B testing de onboarding e paywall, análise de cohort de retenção, funil de ativação instrumentado.
- **Smoke tests / fake door:** medir intenção de pagamento antes de construir features Premium completas.

### 4.3 Riscos de invalidação

Se **H05 falhar** (não há dor anual), todo o posicionamento desmorona e voltamos a ser "mais um app de abril" — risco existencial. Se **H07 falhar** (não pagam ao ver economia), precisamos repensar o gatilho de monetização. Por isso, ambas são testadas já no MVP.

---

## SEÇÃO 5 — Modelo de Negócio

### 5.1 Lógica freemium

O GuIA usa freemium porque o IR é universal mas a disposição a pagar só aparece **depois** que o usuário percebe valor — ver a economia projetada. O tier Básico tem duas funções: (1) reduzir o atrito de entrada a zero, maximizando topo de funil; (2) entregar o "aha moment" que aciona o desejo de upgrade.

### 5.2 Tiers e ARPU

| Tier | Preço | Proposta de valor | Mix Ano 1 | Mix Ano 2 |
|---|---|---|---|---|
| Básico | Grátis | Estimativa + chat limitado | — | — |
| Pro | R$ 9,90/mês | Gestão contínua + declaração otimizada | 75% | 65% |
| Premium | R$ 29,90/mês | Família + DARF completo + suporte humano | 25% | 35% |

**ARPU dos pagantes:**
- **Ano 1:** 0,75 × R$ 9,90 + 0,25 × R$ 29,90 = **R$ 14,90/mês**
- **Ano 2:** 0,65 × R$ 9,90 + 0,35 × R$ 29,90 = **R$ 16,90/mês**

O deslocamento do mix para Premium no Ano 2 (de 25% → 35%) reflete a maturação da base e a entrega de features de maior valor (família, suporte).

### 5.3 LTV por tier

LTV = receita mensal / churn mensal. Com a queda de churn ao longo do tempo (12% → 7% no M12 → 5% no M24), o LTV cresce de forma composta:

| Tier | LTV @ churn 7% (M12) | LTV @ churn 5% (M24) |
|---|---|---|
| Básico | R$ 0 (monetização indireta / funil) | R$ 0 |
| Pro (R$ 9,90) | **R$ 141** | **R$ 198** |
| Premium (R$ 29,90) | **R$ 427** | **R$ 598** |

### 5.4 Unit economics

| Métrica | Ano 1 (M12) | Ano 2 (M24) |
|---|---|---|
| ARPU pagante/mês | R$ 14,90 | R$ 16,90 |
| CAC blended | R$ 15 | R$ 12 |
| Payback (CAC/ARPU) | ~1,0 mês | ~0,7 mês |
| LTV/CAC (Pro) | 9,4x | 16,5x |
| LTV/CAC (Premium) | 28,5x | 49,8x |
| COGS | 18% da receita | 18% da receita |

O payback inferior a 1 mês e LTV/CAC muito acima do benchmark saudável (3x) indicam um motor de aquisição altamente eficiente — desde que a base de conversão e churn se confirme.

### 5.5 Fontes de receita futuras (Plataforma — Ano 3)

Além da assinatura, o roadmap de longo prazo abre receitas adjacentes: **marketplace de contadores parceiros** (lead generation), **API B2B** para fintechs embutirem o motor tributário, e **produtos financeiros contextuais** (previdência, investimentos otimizados por imposto) via parcerias.

---

## SEÇÃO 6 — Estratégia de Mercado

### 6.1 Posicionamento

> *"Pare de temer o Leão. O GuIA cuida do seu IR o ano todo — não só em abril."*

O posicionamento ataca diretamente a sazonalidade dos concorrentes e o medo do contribuinte. Não competimos no eixo "preencher declaração" — competimos no eixo "tranquilidade tributária contínua".

> **Escopo de mercado:** Brasil exclusivamente. Expansão LATAM apenas no Ano 3+ mediante avaliação estratégica separada.

### 6.2 Mapa competitivo

| Concorrente | Modelo | Força | Fraqueza | Como ganhamos |
|---|---|---|---|---|
| Portal Receita Federal | Gratuito | Oficial, confiável | Complexo, hostil, pontual | UX + IA + gestão anual |
| Contadores | R$ 300–800/ano | Confiança, personalização | Caro, pontual, não escala | Preço, escala, continuidade |
| Apps IR pontuais (Imposto.me) | App/assinatura | Foco em declaração | Apenas abril, sem IA proativa | IA anual + integrações |

### 6.3 Estratégia de canais (mix de aquisição)

| Canal | % do mix | Lógica |
|---|---|---|
| SEO / orgânico | 40% | IR gera busca massiva; conteúdo educacional captura intenção o ano todo |
| Google / Meta Ads | 30% | Performance em picos sazonais e retargeting do funil freemium |
| Parcerias FinTechs | 15% | Distribuição embutida em apps financeiros (co-aquisição barata) |
| Referral | 10% | Restituição é evento compartilhável; programa de indicação |
| PR / Influencers | 5% | Autoridade e topo de funil em finanças pessoais |

### 6.4 Go-to-market por fase

- **MVP:** foco em Clara (CLT) — maior volume, dor mais simples de resolver, validação de H08/H07.
- **V1:** expansão para Lucas (investidor) e Rafael (autônomo) via integrações B3 e carnê-leão.
- **V2:** Família Silva e features de otimização avançada; ativação de parcerias FinTech.

### 6.5 APIs estratégicas como vantagem de distribuição e produto

| API | Uso | Impacto estratégico |
|---|---|---|
| SERPRO (Consulta Renda, CPF, Restituição) | Validação e acompanhamento de restituição | Confiança + gatilho de conversão pós-restituição (H16) |
| Open Finance / Pluggy | Captura contínua de movimentações | Automação da gestão anual |
| B3 API | Investimentos e ganho de capital | Persona Lucas |
| NFS-e Nacional | Notas de serviço (autônomos) | Persona Rafael |
| BCB PTAX / SGS | Câmbio e indexadores | Cripto e rendimentos no exterior |
| ViaCEP | Cadastro e UX | Redução de atrito |

---

## SEÇÃO 7 — Roadmap de Produto

| Fase | Duração | Objetivo | Entregáveis-chave | Hipóteses testadas |
|---|---|---|---|---|
| **MVP** | 4 meses | Validar aha moment e disposição a pagar | Onboarding < 2 min, estimativa de restituição, chat IA limitado, paywall Pro | H08, H07 |
| **V1** | 5 meses | Gestão contínua + integrações | Open Finance, B3, carnê-leão básico, captura contínua | H05, H09 |
| **V2** | 9 meses | Otimização avançada + família | Simulação conjunta x separada, DARF completo, suporte Premium, revisão anti-malha | H16, expansão de ARPU |
| **Plataforma** | Ano 3 | Ecossistema e B2B | Marketplace de contadores, API B2B, produtos financeiros contextuais | Novas linhas de receita |

### 7.1 Priorização

Usamos **RICE** (Reach, Impact, Confidence, Effort) para sequenciar o backlog. No MVP, tudo que não serve para testar H08 e H07 é cortado — disciplina de escopo é o que garante o prazo de 4 meses. As integrações (Open Finance, B3) entram em V1 porque dependem de homologação e parcerias, com lead time próprio.

### 7.2 Marcos de OKR no roadmap

- **Fim do MVP (~M4):** primeiros pagantes, validação de conversão ≥ 8%.
- **Fim do V1 (~M9):** base ativa em escala, retenção fora de abril comprovada.
- **M12:** 250 mil cadastros e R$ 500 mil MRR como meta-teto; projeção base aponta MRR de ~R$ 36 mil com base conservadora de churn — o gap entre meta e base define a agressividade necessária em aquisição e conversão (ver Seção 10).

---

## SEÇÃO 8 — Camada de IA

### 8.1 Como a IA funciona de fato no GuIA

O nome GuIA (Guia + IA) não é apenas posicionamento — cada feature é alimentada por uma camada específica de IA:

| Nível | Feature | Tecnologia | Custo MVP | Release |
|-------|---------|-----------|----------|---------|
| **L1 — Regras** | Cálculo de IR, DARF, escolha completa vs. simplificada | Python puro + tabelas IRPF em JSON | Zero | MVP |
| **L2 — ML** | Categorização de transações bancárias como dedutíveis | Regex → XGBoost → Claude Haiku (fallback) | Baixo | MVP |
| **L3 — LLM** | Chat tributário ("posso deduzir academia?") | Claude Sonnet API — persona de especialista tributário BR | Médio | MVP simplificado |
| **L4 — RAG** | Respostas fundamentadas em IN RFB, CARF e STJ | LangChain + pgvector + Claude + embeddings | Médio-alto | V1 |

**API de IA:** Anthropic Claude
- `claude-haiku-4-5` → categorização de transações em batch (rápido, barato)
- `claude-sonnet-4-6` → chat tributário com usuário (qualidade máxima em português)
- Custo estimado no MVP: R$ 50–200/mês para os primeiros 1.000 usuários ativos

**O que o usuário vê como "IA":**
- Badge **DEDUTÍVEL** em cada transação do extrato bancário (L2)
- Chat **"Pergunte ao GuIA"** que responde dúvidas tributárias em linguagem natural (L3)
- Estimativa de restituição atualizada em tempo real (L1 + L2)
- Alertas: "Você gastou R$ 850 em saúde este mês — adicionar ao cofre?" (L1 + L2)
- Simulador: "Se eu investir R$ 5k em PGBL, economizo R$ 1.200 em IR" (L1)

**Diferencial vs. concorrentes:** nenhum app de IR brasileiro usa LLM para chat tributário personalizado. O GuIA é o primeiro.

### 8.2 Arquitetura híbrida

Em matéria fiscal, **errar tem custo legal**. Por isso o GuIA não delega cálculo tributário a um LLM. A arquitetura é deliberadamente híbrida, com cada componente fazendo o que faz melhor:

| Camada | Tecnologia | Função | Por que existe |
|---|---|---|---|
| **Rules Engine** | Determinístico (código + tabelas oficiais) | Cálculo de imposto, alíquotas, limites de dedução | Precisão não-negociável; auditável |
| **OCR** | Visão computacional | Extrair dados de informes, recibos, notas | Eliminar digitação manual |
| **ML de classificação** | Modelos supervisionados | Categorizar despesas/rendimentos | Escala e automação |
| **LLM** | Modelo de linguagem | Conversa, explicação, orientação | Tornar o tributário compreensível |
| **RAG** | Retrieval sobre base oficial | Fundamentar respostas em IN RFB, CARF, STJ | Evitar alucinação; citar fonte |

### 8.3 RAG sobre fontes oficiais

O conhecimento do LLM é ancorado em uma base curada e versionada: **Instruções Normativas da Receita Federal, jurisprudência do CARF e decisões do STJ.** Toda resposta tributária do chat cita a fonte normativa. Isso transforma o LLM de "gerador plausível" em "consultor fundamentado" — e protege o usuário e a empresa de orientações incorretas.

### 8.4 Divisão de responsabilidades (regra de ouro)

- **Números e cálculo fiscal → Rules Engine** (nunca o LLM).
- **Interpretação e linguagem → LLM + RAG** (sempre com citação).
- **Extração de dados → OCR + ML** (com revisão do usuário em casos de baixa confiança).

### 8.5 Cinco Princípios de IA Responsável

1. **Precisão fiscal acima de fluência** — cálculo é determinístico; o LLM nunca inventa números.
2. **Transparência e rastreabilidade** — toda recomendação cita a norma de origem (IN/CARF/STJ).
3. **Privacidade e consentimento** — dados financeiros sensíveis tratados sob consentimento explícito (Open Finance, LGPD).
4. **Supervisão humana onde importa** — Premium oferece revisão humana; casos de baixa confiança escalam.
5. **Não-prejuízo ao contribuinte** — em caso de ambiguidade normativa, o GuIA recomenda a opção mais conservadora e sinaliza o risco.

### 8.6 Custo de IA como COGS

As APIs de IA representam ~8% da receita dentro do COGS de 18% (cloud 5% + IA 8% + suporte 5%). A arquitetura híbrida ajuda a conter esse custo: o Rules Engine resolve o trabalho pesado de cálculo sem tokens de LLM, e o RAG reduz a necessidade de prompts longos e caros.

### 8.7 LGPD e Proteção de Dados

Dados bancários e fiscais são os mais sensíveis de uma pessoa física. O GuIA aplica:

**Princípios inegociáveis:**
1. **Dados brutos nunca persistem** — extratos bancários são processados, categorizados e descartados. O servidor guarda apenas "Farmácia — R$ 85 — Saúde — Dedutível", nunca o dado bruto.
2. **Declarações cifradas** — a declaração completa de IR é cifrada com chave derivada da senha do usuário. Nem o servidor GuIA consegue ler sem autenticação.
3. **Masking antes do LLM** — CPF, nome e valores são mascarados antes de qualquer dado sair para a Claude API.
4. **Consentimento Open Finance granular** — usuário escolhe banco por banco, dado por dado. Revogável a qualquer momento. Prazo máximo: 12 meses (Resolução BCB nº 86/2021).
5. **Sem venda de dados** — modelo de negócio é assinatura. Dados nunca são o produto.

**Bases legais:** Art. 7º, I LGPD (consentimento) para dados bancários e cadastro; Art. 7º, V (execução de contrato) para cálculo de IR.

**DPO:** Designado obrigatoriamente dado o volume e natureza dos dados. Canal: privacidade@guia.com.br

---

## SEÇÃO 9 — Analytics e Métricas

### 9.1 North Star Metric

**"Reais economizados em impostos por usuário ativo por ano".** Essa métrica é superior a proxies de vaidade (downloads, MAU isolado) porque captura o valor econômico real entregue — e está diretamente correlacionada com disposição a pagar e retenção. Quanto mais reais o GuIA economiza, mais o usuário paga e fica.

### 9.2 Árvore de métricas (NSM → drivers)

```
NSM: R$ economizados por usuário ativo/ano
 ├── Cobertura de deduções capturadas (% do potencial)
 │     ├── Integrações conectadas por usuário
 │     └── Despesas classificadas corretamente (ML)
 ├── Usuários ativos
 │     ├── Ativação (aha moment < 2 min) — H08
 │     ├── Retenção fora de abril — H05/H09
 │     └── Churn mensal
 └── Conversão freemium → pago — H07/H16
```

### 9.3 Métricas por estágio do funil (AARRR)

| Estágio | Métrica primária | Meta de referência |
|---|---|---|
| Aquisição | CAC blended | R$ 25 → R$ 15 (M12) → R$ 12 (Ano 2) |
| Ativação | % com aha moment < 2 min | ≥ 60% |
| Retenção | Retenção M3 (CLT) | ≥ 35% |
| Receita | Conversão freemium→pago | 8% (Ano 1) → 12% (Ano 2) |
| Indicação | Coeficiente de referral | Suportar 10% do mix |

### 9.4 Instrumentação

Eventos-chave instrumentados desde o MVP: `onboarding_started`, `first_estimate_shown` (aha moment), `integration_connected`, `paywall_viewed`, `subscription_started`, `refund_tracked`. Dashboards de cohort de retenção e funil de conversão guiam a iteração semanal. A NSM é calculada comparando o imposto efetivamente devido com um baseline "sem GuIA".

---

## SEÇÃO 10 — Projeções Financeiras

> Premissas: conversão freemium→pago de 8% (Ano 1) e 12% (Ano 2); churn mensal de 12% (M1) → 7% (M12) → 5% (M24), interpolado linearmente; ARPU de R$ 14,90 (Ano 1) e R$ 16,90 (Ano 2); COGS de 18% da receita; CAC de R$ 25 (M1) → R$ 15 (M12) → R$ 12 (Ano 2); time de R$ 80k/mês (Ano 1) e R$ 180k/mês (Ano 2); marketing de aquisição = novos cadastros × CAC. Base ativa calculada com churn composto sobre a base anterior + novos cadastros.

### 10.1 Crescimento de cadastros e base ativa (24 meses)

| Mês | Novos cadastros | Churn % | Base ativa | Conv. % | Pagantes | ARPU | MRR (R$) |
|---|---|---|---|---|---|---|---|
| M1 | 500 | 12,0% | 500 | 8% | 40 | 14,90 | 596 |
| M2 | 650 | 11,5% | 1.092 | 8% | 87 | 14,90 | 1.302 |
| M3 | 845 | 11,1% | 1.816 | 8% | 145 | 14,90 | 2.165 |
| M4 | 1.099 | 10,6% | 2.722 | 8% | 218 | 14,90 | 3.245 |
| M5 | 1.428 | 10,2% | 3.873 | 8% | 310 | 14,90 | 4.616 |
| M6 | 1.857 | 9,7% | 5.353 | 8% | 428 | 14,90 | 6.381 |
| M7 | 2.414 | 9,3% | 7.271 | 8% | 582 | 14,90 | 8.667 |
| M8 | 3.138 | 8,8% | 9.768 | 8% | 781 | 14,90 | 11.643 |
| M9 | 4.080 | 8,4% | 13.031 | 8% | 1.042 | 14,90 | 15.533 |
| M10 | 5.304 | 7,9% | 17.304 | 8% | 1.384 | 14,90 | 20.626 |
| M11 | 6.895 | 7,5% | 22.909 | 8% | 1.833 | 14,90 | 27.308 |
| **M12** | **8.964** | **7,0%** | **30.269** | **8%** | **2.422** | **14,90** | **36.081** |
| M13 | 11.200 | 6,8% | 39.401 | 12% | 4.728 | 16,90 | 79.905 |
| M14 | 12.500 | 6,7% | 49.274 | 12% | 5.913 | 16,90 | 99.928 |
| M15 | 13.800 | 6,5% | 59.871 | 12% | 7.185 | 16,90 | 121.419 |
| M16 | 15.000 | 6,3% | 71.080 | 12% | 8.530 | 16,90 | 144.149 |
| M17 | 16.200 | 6,2% | 82.896 | 12% | 9.948 | 16,90 | 168.114 |
| M18 | 17.300 | 6,0% | 95.223 | 12% | 11.427 | 16,90 | 193.111 |
| M19 | 18.300 | 5,8% | 107.968 | 12% | 12.956 | 16,90 | 218.959 |
| M20 | 19.100 | 5,7% | 120.950 | 12% | 14.514 | 16,90 | 245.286 |
| M21 | 19.600 | 5,5% | 133.898 | 12% | 16.068 | 16,90 | 271.544 |
| M22 | 19.900 | 5,3% | 146.656 | 12% | 17.599 | 16,90 | 297.419 |
| M23 | 20.000 | 5,2% | 159.079 | 12% | 19.089 | 16,90 | 322.612 |
| **M24** | **20.000** | **5,0%** | **171.125** | **12%** | **20.535** | **16,90** | **347.042** |

### 10.2 Demonstrativo de resultado mensal (DRE simplificada)

> Opex fixo = time (R$ 80k Ano 1 / R$ 180k Ano 2) + marketing de aquisição (novos × CAC). COGS = 18% da receita.

| Mês | Receita (MRR) | COGS (18%) | Margem bruta | Time | Mkt aquisição | Resultado op. |
|---|---|---|---|---|---|---|
| M1 | 596 | 107 | 489 | 80.000 | 12.500 | -92.011 |
| M3 | 2.165 | 390 | 1.775 | 80.000 | 19.589 | -97.814 |
| M6 | 6.381 | 1.149 | 5.232 | 80.000 | 37.984 | -112.752 |
| M9 | 15.533 | 2.796 | 12.737 | 80.000 | 72.327 | -139.590 |
| **M12** | **36.081** | **6.495** | **29.586** | **80.000** | **134.460** | **-184.874** |
| M15 | 121.419 | 21.855 | 99.564 | 180.000 | 165.600 | -246.036 |
| M18 | 193.111 | 34.760 | 158.351 | 180.000 | 207.600 | -229.249 |
| M21 | 271.544 | 48.878 | 222.666 | 180.000 | 235.200 | -192.534 |
| **M24** | **347.042** | **62.468** | **284.574** | **180.000** | **240.000** | **-135.426** |

> Observação: o resultado operacional é negativo durante todo o horizonte de 24 meses porque a empresa está em **fase de crescimento agressivo** — reinvestindo fortemente em aquisição (marketing escala com cadastros). A trajetória importa: a perda mensal *atinge o pico* por volta do M15 (-R$ 246k) e **começa a estreitar a partir daí** (-R$ 135k no M24), à medida que a margem bruta cresce mais rápido que o opex. O ponto de equilíbrio operacional ocorre além do M24, quando a base ativa madura e o churn de 5% sustentam a base de pagantes com menos dependência de aquisição.

### 10.3 Métricas-resumo

| Indicador | M12 | M24 |
|---|---|---|
| Cadastros acumulados | 37.174 | 240.074 |
| Base ativa | 30.269 | 171.125 |
| Pagantes | 2.422 | 20.535 |
| MRR | R$ 36.081 | R$ 347.042 |
| ARR (anualizado) | R$ 432.972 | R$ 4.164.501 |
| Churn mensal | 7,0% | 5,0% |
| CAC | R$ 15 | R$ 12 |
| Payback | ~1,0 mês | ~0,7 mês |
| LTV/CAC (Pro) | 9,4x | 16,5x |

### 10.4 Leitura crítica vs. OKRs

A meta de OKR de **250 mil usuários** é praticamente atingida pela curva de cadastros (240 mil acumulados já no M24, e 250 mil pouco depois). Já a meta de **R$ 500 mil de MRR no M12** não é alcançada pela projeção base (R$ 36 mil no M12), pois a meta foi ancorada num cenário muito mais otimista de conversão e/ou ARPU. **Isso é uma constatação honesta, não um erro:** o gap revela onde a execução precisa ser excepcional — acelerar conversão acima de 8%, deslocar mix para Premium mais cedo, e reduzir churn mais rápido. A projeção base é o **piso conservador**; o OKR é o **teto ambicioso**. A gestão do negócio vive no intervalo entre os dois.

---

## SEÇÃO 11 — Liderança e Execução

### 11.1 Filosofia de execução

Produto de IA em domínio regulado exige uma cultura que equilibra **velocidade de iteração** com **rigor de correção**. Erramos rápido em UX e marketing; nunca erramos em cálculo fiscal. Essa assimetria define a organização.

### 11.2 Time mínimo viável (Ano 1, ~R$ 80k/mês)

| Função | Responsabilidade |
|---|---|
| Product Lead (founder) | Visão, priorização, descoberta contínua |
| Eng. Backend / IA | Rules Engine, RAG, integrações de API |
| Eng. Full-stack | App, onboarding, paywall |
| Especialista tributário | Curadoria da base normativa, validação fiscal |
| Growth / Marketing | SEO, performance, conversão |

### 11.3 Evolução para o Ano 2 (~R$ 180k/mês)

Com a base crescendo para 170 mil ativos, o time dobra: mais engenharia (escala e integrações), data/analytics dedicado (NSM e cohort), suporte (Premium), e expansão de growth para parcerias FinTech.

### 11.4 Rituais e cadência

- **Semanal:** revisão de funil, cohort de retenção, entrevistas de descoberta.
- **Mensal:** check de OKR, revisão de unit economics, repriorização do roadmap (RICE).
- **Trimestral:** revisão estratégica, ajuste de premissas financeiras, planejamento de fase.

### 11.5 Decisões de liderança críticas

A liderança será cobrada em três decisões recorrentes: **(1) quando investir mais em aquisição vs. preservar caixa** (o resultado operacional é negativo todo o horizonte); **(2) quando escalar o mix Premium** (acelera ARPU mas exige features e suporte); **(3) onde colocar a fronteira humano-IA** (suporte humano é caro mas é diferencial de confiança).

---

## SEÇÃO 12 — Riscos e Mitigações

| # | Risco | Categoria | Prob. | Impacto | Mitigação |
|---|---|---|---|---|---|
| R1 | Erro de cálculo fiscal gera multa ao usuário | Produto/Legal | Média | Crítico | Rules Engine determinístico + revisão por especialista + recomendação conservadora |
| R2 | LLM alucina orientação tributária | IA | Média | Alto | RAG sobre fontes oficiais + citação obrigatória + LLM nunca calcula |
| R3 | Conversão fica abaixo de 8% (H07 falha) | Negócio | Média | Alto | A/B do paywall, ancoragem no aha moment, gatilho pós-restituição (H16) |
| R4 | Dor anual não se confirma (H05 falha) | Estratégia | Baixa | Crítico | Validar cedo no MVP; pivô para captura contínua mais agressiva |
| R5 | Churn não cai conforme premissa | Negócio | Média | Alto | Engajamento fora de abril, notificações de economia, features Premium pegajosas |
| R6 | Mudança regulatória da Receita | Externo | Alta | Médio | Base normativa versionada; especialista monitora IN/CARF/STJ |
| R7 | Dependência de APIs externas (SERPRO, Open Finance) | Técnico | Média | Médio | Contratos de SLA, fallbacks, importação manual como degradação graciosa |
| R8 | Custo de IA (COGS) escala acima de 8% | Financeiro | Média | Médio | Arquitetura híbrida, caching de RAG, modelos menores para classificação |
| R9 | Vazamento de dados financeiros sensíveis | Segurança/LGPD | Baixa | Crítico | Criptografia, consentimento explícito, conformidade LGPD, mínimo de retenção |
| R10 | Concorrente grande copia o anual | Competitivo | Média | Médio | Velocidade, base normativa proprietária, integrações e marca |

### 12.1 Riscos existenciais

R1 (erro fiscal) e R4 (dor anual inexistente) são os dois riscos que matam o negócio. O primeiro é mitigado por arquitetura (determinismo + supervisão humana); o segundo, por validação antecipada no MVP. Tudo o mais é gerenciável.

---

## SEÇÃO 13 — Next Steps

### 13.1 Próximos 90 dias (rumo ao MVP)

1. **Construir o onboarding com aha moment < 2 min** — importação de informe + primeira estimativa. Testar H08.
2. **Implementar Rules Engine v0** — cálculo de restituição para o caso CLT (persona Clara).
3. **Subir paywall Pro e instrumentar A/B** — testar H07 (pagam ao ver economia).
4. **Curar base normativa inicial** — IN RFB relevantes para CLT, com RAG funcional.
5. **Rodar 20+ entrevistas de descoberta** — validar H05 (dor anual) qualitativamente.

### 13.2 Próximos 6 meses (rumo ao V1)

6. Homologar integrações Open Finance/Pluggy e B3.
7. Lançar captura contínua e carnê-leão básico (personas Rafael e Lucas).
8. Estruturar motor de SEO/conteúdo (40% do mix de aquisição).
9. Validar retenção fora de abril (H09) com cohort de CLTs.

### 13.3 Próximos 12 meses (rumo aos OKRs)

10. Campanha de conversão pós-restituição via SERPRO (H16).
11. Ativar primeiras parcerias FinTech (15% do mix).
12. Revisar premissas financeiras com dados reais e recalibrar a meta de MRR.

### 13.4 Decisões pendentes para o board

- Nível de queima de caixa aceitável dado o resultado operacional negativo no horizonte de 24 meses.
- Antecipar ou não o tier Premium para acelerar ARPU.
- Tamanho do investimento inicial em SEO (payback longo, mas barato no longo prazo).

---

## SEÇÃO 14 — Conclusão

O GuIA é uma resposta de produto a uma dor estrutural, massiva e recorrente: **41 milhões de brasileiros temem e erram o Imposto de Renda, deixando bilhões na mesa.** A oportunidade não está em fazer "mais um app de abril" — está em redefinir a categoria, transformando o IR de evento anual de pânico em **gestão tributária contínua assistida por IA**.

A tese se sustenta em quatro pilares que este documento percorreu:

1. **Diferencial defensável:** somos o único assistente tributário *anual* com IA, com uma base normativa proprietária (IN RFB, CARF, STJ) e integrações estratégicas que automatizam a captura de valor.
2. **Arquitetura responsável:** a combinação Rules Engine determinístico + OCR + ML + LLM + RAG, governada por 5 Princípios de IA Responsável, resolve o paradoxo de usar IA em um domínio onde errar é multa.
3. **Economia unitária saudável:** payback de CAC em ~1 mês, LTV/CAC acima de 16x no Ano 2, e uma curva de MRR que cresce de R$ 596 para R$ 347 mil em 24 meses — sobre uma base que se aproxima da meta de 250 mil usuários.
4. **Foco em valor real:** a North Star Metric — reais economizados por usuário ativo por ano — mantém o produto, o negócio e o usuário alinhados no mesmo norte.

As projeções foram apresentadas com honestidade: o resultado operacional é negativo durante os 24 meses de crescimento agressivo, e a meta de MRR do OKR está acima da projeção base — um *gap* que define exatamente onde a execução precisa ser excepcional. Essa transparência é, ela própria, parte da tese: **gerimos o negócio no intervalo entre o piso conservador e o teto ambicioso.**

O Leão sempre foi inevitável. O medo dele não precisa ser. O GuIA existe para que o brasileiro, pela primeira vez, encare o Imposto de Renda com tranquilidade — o ano todo, não só em abril.

---

*Documento produzido como Projeto Final (capstone) do MBA, sintetizando os 7 módulos do curso aplicados ao produto GuIA.*
