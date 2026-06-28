# GuIA — Artefatos do Módulo 07
**MBA Tera · Liderança e Estratégia de Produtos Digitais na Era da IA**
**Módulo 07 — IA: Inovação e Eficiência**
**Produzido em:** Junho 2026

---

## Artefato 1 — Arquitetura da Camada de IA do GuIA

### Diagrama textual da arquitetura

```
┌──────────────────────────────────────────────────────────────────┐
│                     USUÁRIO (App / Web)                           │
│         Clara · Rafael · Lucas · Família Silva                    │
└────────────────────────┬─────────────────────────────────────────┘
                         │ uploads, perguntas, consentimento OF
          ┌──────────────▼──────────────┐
          │   ORQUESTRADOR DE IA        │
          │  roteamento · guardrails    │
          │  logging · audit trail      │
          └──┬──────┬──────┬──────┬─────┘
             │      │      │      │
   ┌─────────▼─┐ ┌──▼───┐ ┌▼──────────┐ ┌▼─────────────┐
   │ CAMADA 1  │ │CAM.2 │ │ CAMADA 3  │ │  CAMADA 4    │
   │ INGESTÃO  │ │CLASS.│ │RACIOCÍNIO │ │CONHECIMENTO  │
   ├───────────┤ ├──────┤ ├───────────┤ ├──────────────┤
   │ · OCR     │ │ · ML │ │ · Rules   │ │ · RAG        │
   │ informes  │ │ class│ │   Engine  │ │  (IN RFB,    │
   │ recibos   │ │ desp.│ │  (tabelas │ │  CARF, STJ,  │
   │ DARF      │ │ · NER│ │  IRPF,    │ │  PGFN, sol.  │
   │ notas de  │ │ trib.│ │  deduções,│ │  de consulta)│
   │ corretagem│ │      │ │  cenários)│ │ · Vector DB  │
   │ · Extração│ │      │ │ · LLM     │ │              │
   │ estrutur. │ │      │ │  (chat,   │ │              │
   └─────┬─────┘ └──┬───┘ │  explica) │ └──────┬───────┘
         │          │     └─────┬─────┘        │
         └──────────┴───────────┴──────────────┘
                               │
              ┌────────────────▼────────────────┐
              │        CATEGORIZADOR             │
              │  Open Finance (Pluggy) · regex   │
              │  XGBoost (MCC+CNPJ+descrição)    │
              │  fallback LLM · aprendizado ativo│
              └────────────────┬────────────────┘
                               │
              ┌────────────────▼────────────────┐
              │   CAMADA DE DADOS & FEATURES     │
              │  perfil fiscal · histórico IRPF  │
              │  Open Finance · B3 · feature     │
              │  store longitudinal              │
              └────────────────┬────────────────┘
                               │
              ┌────────────────▼────────────────┐
              │  SAÍDA: simulações · declaração  │
              │  DARF · alertas · NSM (economia) │
              └─────────────────────────────────┘

  GOVERNANÇA TRANSVERSAL:
  Guardrails · Human-in-the-loop · Audit log · PII masking
  LGPD/Art.11 · Comitê Jurídico · Observabilidade de modelos
```

### Componentes, contribuição à NSM e tecnologias

| Componente | O que faz | Contribuição à NSM | Tecnologia recomendada | Justificativa |
|------------|-----------|-------------------|------------------------|---------------|
| **OCR** | Lê informes de rendimento, recibos médicos/educação, DARF, notas de corretagem | Captura despesas dedutíveis que o usuário esqueceria → mais deduções = menos imposto | AWS Textract / Google Document AI + pós-processamento LLM | Document AI tem alta acurácia em documentos PT-BR; LLM corrige campos ambíguos |
| **ML de Classificação** | Categoriza despesas (médica, educação, previdência, dependente) e identifica dedutibilidade | Garante que cada despesa caia na rubrica correta, maximizando a dedução legal | XGBoost/LightGBM + BERTimbau para texto livre | BERTimbau pré-treinado em PT-BR; gradient boosting robusto para features mistas |
| **Rules Engine** | Aplica tabelas progressivas IRPF, limites de dedução, carnê-leão, ganho de capital, isenções | Núcleo da economia: calcula o imposto correto e o cenário ótimo (completa vs. simplificada) | Drools / json-rules-engine + tabelas parametrizadas por exercício | Determinístico, auditável e versionável — essencial para conformidade legal |
| **RAG** | Recupera legislação (IN RFB, CARF, STJ, PGFN) para fundamentar respostas | Segurança jurídica nas sugestões; embasa otimizações menos óbvias | pgvector / Pinecone + embeddings multilingual-e5 + reranker cross-encoder | RAG ancora o LLM em fontes oficiais, reduzindo alucinação em tema de alto risco |
| **LLM** | Chat tributário, explica decisões, sugere proativamente | Traduz complexidade tributária em ação concreta; identifica oportunidades personalizadas | Claude / GPT-4 para raciocínio complexo + modelo menor para tarefas simples | Roteamento reduz custo; modelo forte garante qualidade em questões tributárias |
| **Orquestrador + Guardrails** | Roteia entre componentes, aplica políticas, valida saídas, registra auditoria | Garante que a economia sugerida seja **legal e verificável** — nunca evasão | LangGraph + guardrails de schema + checagem de citação obrigatória | Controle agêntico com checkpoints de segurança e human-in-the-loop |
| **Categorizador de Transações Bancárias** | Processa transações do Open Finance (Pluggy), classifica por categoria tributária (saúde, educação, previdência, investimento, etc.) e marca se é dedutível no IR, com qual limite e em qual ficha da DIRPF | Captura automaticamente 100% das despesas dedutíveis que o usuário pagou mas não lançaria manualmente — maior cobertura = maior economia | Pipeline híbrido — (1) regex/keywords para casos óbvios; (2) XGBoost com features: descrição, valor, MCC code, CNPJ do estabelecimento; (3) fallback LLM para casos ambíguos + aprendizado ativo | A combinação regex+ML+LLM garante velocidade e custo baixo para 90% dos casos (regex/ML) e qualidade para os 10% ambíguos (LLM). O MCC code (Merchant Category Code) das transações Open Finance é o feature mais preditivo para categoria tributária |
| **Feature Store / Dados** | Perfil fiscal longitudinal, dados Open Finance, B3 | Quanto mais dados históricos, maior a economia a cada ciclo — fonte de defensibilidade | Feast + BigQuery / DWH analítico | Dados longitudinais alimentam personalização crescente — aumentam NSM ano a ano |

---

## Artefato 2 — Casos de Uso de IA por Persona

### Clara (32, CLT)

| # | Caso de uso | Entrada | Processamento de IA | Saída para o usuário | Métrica de sucesso |
|---|------------|---------|--------------------|-----------------------|--------------------|
| C1 | **Importação automática do informe de rendimentos** | Foto/PDF do informe do empregador | OCR + NER tributário extrai CNPJ, rendimento bruto, IRRF retido, INSS | Campos pré-preenchidos na declaração, sem digitação | ≥ 95% de campos corretos sem edição manual |
| C2 | **Captura de despesas médicas ao longo do ano** | Fotos de recibos/notas enviadas mensalmente | OCR + ML classifica como "saúde dedutível" | Dedução médica acumulada + projeção do impacto na restituição | R$ de dedução médica capturada vs. baseline sem uso do GuIA |
| C3 | **Escolha ótima: completa vs. simplificada** | Todos os dados já lançados | Rules Engine simula os dois cenários com os dados reais | "Usando o modelo completo você economiza R$ 1.240 a mais" | Δ restituição entre cenário recomendado e default |
| C4 | **Identificação automática de deduções no extrato** | Extrato bancário importado via Open Finance | Categorizador analisa cada transação, marca "Drogaria São Paulo — R$ 85 — Saúde DEDUTÍVEL" | Lista mensal de deduções identificadas automaticamente + projeção de restituição atualizada em tempo real | R$ de deduções médicas capturadas automaticamente vs. baseline manual |

### Rafael (41, Autônomo/MEI)

| # | Caso de uso | Entrada | Processamento de IA | Saída para o usuário | Métrica de sucesso |
|---|------------|---------|--------------------|-----------------------|--------------------|
| R1 | **Carnê-leão mensal automatizado** | Recebimentos de PF (Open Finance + lançamento manual) | Rules Engine calcula base de cálculo, alíquota progressiva, dedução de despesas profissionais | DARF mensal pronto para pagamento + alerta de vencimento | % de meses com DARF pago no prazo (evita multa 0,33%/dia) |
| R2 | **Separação de despesa pessoal × profissional** | Extratos bancários (Open Finance) + notas fiscais | ML classifica despesas dedutíveis do autônomo: aluguel proporcional, internet, materiais, cursos | Livro-caixa organizado + economia estimada em imposto anual | Precisão ≥ 90%; redução do IRPF anual |
| R3 | **Alerta de aproximação do limite MEI (R$ 81k)** | Faturamento acumulado | ML projeta estouro com base na sazonalidade + Rules Engine simula impacto se migrar para ME | Alerta proativo com X meses de antecedência + simulação dos regimes | Antecedência do alerta; evita penalidades por estouro retroativo |
| R4 | **Separação automática de despesas pessoais e profissionais** | Extrato da conta pessoal e conta MEI via Open Finance | ML classifica transação como "pessoal", "profissional dedutível" ou "profissional não dedutível" com base no CNPJ, MCC e descrição | Livro-caixa pré-preenchido + alertas de despesas profissionais não categorizadas | % de transações classificadas corretamente sem edição manual ≥ 90% |

### Lucas (28, Investidor)

| # | Caso de uso | Entrada | Processamento de IA | Saída para o usuário | Métrica de sucesso |
|---|------------|---------|--------------------|-----------------------|--------------------|
| L1 | **Cálculo de ganho de capital e DARF mensal de renda variável** | Notas de corretagem / integração B3 | Rules Engine aplica isenção de R$ 20k/mês, alíquota 15%/20%, compensação de prejuízos | DARF de renda variável + apuração mensal consolidada por ativo | Acurácia vs. cálculo manual auditado; zero DARF em atraso |
| L2 | **Rastreamento e compensação de prejuízos** | Histórico de operações do exercício | Rules Engine rastreia saldo de prejuízos compensáveis mês a mês por mercado | "Você tem R$ 3.420 de prejuízo acumulado em FIIs para abater neste mês" | Imposto evitado pela compensação correta |
| L3 | **Tributação de cripto e investimentos no exterior** | Operações em exchanges/corretoras estrangeiras | RAG sobre IN RFB 1.888/2019, IN 2.180/2024 (cripto) + Rules Engine para variação cambial | Cálculo do imposto + checklist de obrigações acessórias (GCAP, Ficha Bens e Direitos) | Conformidade total — zero pendências na RFB |
| L4 | **Rastreamento automático de aportes e resgates de investimentos** | Movimentações de conta investimento via Open Finance (renda fixa, fundos) + extratos de corretora | ML identifica aportes/resgates, cruza com tabela regressiva de IR de fundos, calcula IOF proporcional | Posição tributária de cada investimento + alerta quando resgate teria tributação menor aguardando X dias | Precisão do cálculo de IR de fundos ≥ 95% |

### Família Silva (casal com dependentes)

| # | Caso de uso | Entrada | Processamento de IA | Saída para o usuário | Métrica de sucesso |
|---|------------|---------|--------------------|-----------------------|--------------------|
| FS1 | **Otimização: declarar conjunta vs. separada** | Renda, deduções e despesas de ambos os cônjuges | Rules Engine simula as duas opções com os dados reais do casal | "Declarando separadamente o casal economiza R$ 2.100 neste exercício" | Δ imposto total; adoção da recomendação |
| FS2 | **Alocação ótima de dependentes e deduções** | Dados dos filhos, escolas, planos de saúde | Rules Engine testa todas as combinações de alocação de dependentes entre os cônjuges | "Coloque o Filho 2 como dependente do cônjuge B e economize R$ 680" | Economia gerada pela alocação ótima vs. default |
| FS3 | **Planejamento de aporte em PGBL** | Renda bruta tributável de cada cônjuge | LLM + Rules Engine calcula dedução de até 12% da renda bruta | "Aplicando R$ 4.800/ano em PGBL, você economiza R$ 1.056 em imposto" | Adesão à sugestão + economia tributária realizada |
| FS4 | **Consolidação automática de gastos familiares para IR** | Extratos de ambos os cônjuges conectados via Open Finance | Categorizador consolida gastos de saúde e educação de toda a família, identifica qual cônjuge deve declarar cada despesa para maximizar dedução | Rateio ótimo de deduções por cônjuge + projeção comparativa conjunto vs. separado atualizada mensalmente | Δ restituição familiar com rateio ótimo vs. rateio padrão |

---

## Artefato 3 — Plano de Treinamento e Atualização do Modelo

### Fontes oficiais monitoradas

| Fonte | O que monitorar | Mecanismo |
|-------|-----------------|-----------|
| **Receita Federal (RFB)** | Instruções Normativas, layout DIRPF, tabela progressiva, perguntão IRPF | Monitor do DOU + site RFB com alerta por webhook |
| **CARF** | Acórdãos e súmulas sobre dedutibilidade | Ingestão de acórdãos publicados na base CARF |
| **STJ / STF** | Jurisprudência tributária vinculante, teses de repercussão geral | Monitor de pautas e julgados publicados |
| **PGFN** | Pareceres, programas de regularização (PERT, Refis), dívida ativa | Boletins e portarias PGFN |
| **e-CAC / DIRPF** | Mudanças no programa, layout de importação, pré-preenchida | Diff do layout a cada exercício |
| **PGDAS-D / Simples** | Regras MEI/ME — Comitê Gestor do Simples (CGSN) | Resoluções CGSN no DOU |
| **B3 / CVM** | Regras de tributação de renda variável, FIIs, debêntures | Circulares CVM + boletins B3 |

### Pipeline de atualização

```
[Fontes oficiais: DOU, RFB, CARF, STJ]
        │
        ▼
[Coletor / Monitor automatizado]  ──► [Fila de revisão]
        │
        ▼
[Curadoria jurídica humana]  ──► [Validação de relevância e interpretação]
        │
        ▼
[Estruturação + versionamento semântico por exercício]
        │
        ├──► [Atualização Rules Engine] ──► [Testes de regressão (golden cases)]
        │
        └──► [Re-indexação RAG] ──► [Avaliação de recuperação (precision@k)]
                     │
                     ▼
        [Aprovação Comitê Jurídico]
                     │
                     ▼
        [Deploy versionado com rollback]
```

| Etapa | Frequência | Validação |
|-------|-----------|-----------|
| Coleta de atos normativos | Diária | Automática — flag de relevância tributária |
| Curadoria jurídica | Semanal + ad hoc | Humana (especialista tributário) |
| Atualização de tabelas/regras | A cada mudança normativa | Testes de regressão em golden cases |
| Re-indexação do RAG | A cada novo documento curado | Avaliação de recuperação (precision@k ≥ 0,85) |
| Atualização anual da DIRPF | Anual (jan–fev) | Suite completa de testes + auditoria jurídica |
| **SLA máximo de ingestão** | **≤ 5 dias úteis** após publicação | Aprovação do Comitê antes do deploy |

### Como lidar com erros da IA

| Mecanismo | Descrição |
|-----------|-----------|
| **Fallback determinístico** | Em cálculo tributário, o Rules Engine é a fonte de verdade; o LLM nunca calcula imposto sozinho |
| **Confiança e abstenção** | Abaixo de limiar configurável, o sistema pede confirmação ao usuário em vez de assumir o valor |
| **Human-in-the-loop** | Casos complexos roteados para revisão humana ou parceiro contador antes da entrega |
| **Citação obrigatória** | Toda afirmação tributária cita a fonte oficial. Sem fonte verificada = sem afirmação |
| **Feedback loop ativo** | Usuário marca "isso está errado" → correções viram dados rotulados para re-treino |
| **Disclaimer e revisão final** | Antes de transmitir, resumo claro + opção de revisar com contador parceiro |

### Métricas de qualidade do modelo

| Métrica | Componente | Meta |
|---------|-----------|------|
| Acurácia do cálculo tributário | Rules Engine | ≥ 98% (auditoria jurídica por amostragem) |
| Acurácia de extração por campo | OCR | ≥ 95% |
| Precisão / recall de classificação | ML de despesas | ≥ 90% / ≥ 88% |
| Taxa de alucinação verificada | LLM / RAG | < 2% em respostas tributárias auditadas |
| Precision@k de recuperação | RAG | ≥ 0,85 |
| Latência p95 do chat | RAG + LLM | < 5s |
| Taxa de declarações em malha fina | End-to-end | < 2% das declarações transmitidas |
| Drift de modelo | ML / OCR | Alerta se queda > 3 p.p. vs. baseline mensal |
| Precisão do categorizador (keyword+ML) | Categorizador bancário | ≥ 90% por categoria |
| Taxa de transações que precisaram de LLM (fallback) | Categorizador | < 15% do total (maioria deve ser resolvida por regex/ML) |

---

## Artefato 4 — Riscos de IA e Mitigações (AI Safety)

### Matriz de Riscos

| # | Risco | Prob. | Impacto | Mitigação | Responsável |
|---|-------|-------|---------|-----------|-------------|
| 1 | **Cálculo tributário incorreto** | Média | Crítico | Rules Engine determinístico + golden cases + auditoria jurídica trimestral | Lead IA/Dados + Jurídico |
| 2 | **Alucinação do LLM** | Média | Alto | RAG com citação obrigatória; guardrail que rejeita resposta sem fonte verificável | Lead IA/Dados |
| 3 | **Sugestão de evasão fiscal** | Baixa | Crítico | Política "somente elisão lícita"; Comitê Jurídico revisa todas as categorias de sugestão | Jurídico/Tributário |
| 4 | **Erro de OCR em valor numérico** | Média | Alto | Limiar de confiança + confirmação do usuário + checagem de consistência cruzada | Eng + IA/Dados |
| 5 | **Viés / iniquidade do modelo** | Baixa | Médio | Avaliação de fairness por segmento; dataset balanceado; monitoramento por coorte | IA/Dados |
| 6 | **Vazamento de dados sensíveis (LGPD)** | Baixa | Crítico | PII masking em logs, criptografia em repouso e trânsito, DPIA, base legal Art. 11 LGPD | DPO + Eng |
| 7 | **Mudança legislativa não capturada** | Média | Alto | Pipeline com SLA ≤ 5 dias úteis + versionamento por exercício + alerta automático | IA/Dados + Jurídico |
| 8 | **Prompt injection via documento** | Baixa | Alto | Sanitização de inputs, separação instrução/dados, sandbox de OCR, validação de schema | Seg + Eng |
| 9 | **Responsabilidade por ato agêntico** | Baixa | Crítico | Confirmação humana obrigatória antes de ato irreversível; trilha de auditoria completa | Produto + Jurídico |
| 10 | **Excesso de confiança do usuário** | Média | Médio | Resumo pré-envio com destaque de itens que precisam de atenção; disclaimer claro | Produto |
| 11 | **Dados bancários incompletos ou inconsistentes** | Alta | Médio | Banco de dados de CNPJs e MCC codes para enriquecer dados pobres; fallback LLM; opção de edição manual pelo usuário | IA/Dados |
| 12 | **Falso positivo de dedução** | Média | Alto | Disclaimer "sugestão — confirme antes de incluir na declaração"; revisão obrigatória antes do envio; feedback loop ativo para correção | Produto + Jurídico |

### Política de IA Responsável do GuIA — 5 Princípios

**Princípio 1 — Determinismo onde importa.**
Todo cálculo de imposto vem de um motor de regras auditável, versionado e aprovado pelo Comitê Jurídico. A IA generativa explica, sugere e conversa — nunca é a fonte de verdade do valor devido ou da dedução permitida.

**Princípio 2 — Fundamentação obrigatória: sem fonte, sem afirmação.**
Nenhuma afirmação tributária é feita sem citar explicitamente a fonte oficial. Se o sistema não encontrar fundamento verificável, ele se abstém e orienta o usuário a consultar um especialista.

**Princípio 3 — Humano no comando em atos irreversíveis.**
Transmissão de declaração, geração e pagamento de DARF, ou qualquer ato com efeito legal exigem confirmação humana explícita e ficam registrados em trilha de auditoria imutável.

**Princípio 4 — Privacidade e legalidade por design.**
Dados financeiros são dados sensíveis (Art. 11 LGPD): coleta minimizada, consentimento granular e revogável, criptografia em repouso e trânsito, masking de PII em todos os logs. O GuIA pratica apenas elisão fiscal lícita — jamais orienta evasão.

**Princípio 5 — Transparência e melhoria contínua.**
O usuário sempre entende o porquê de cada sugestão, pode corrigir a IA a qualquer momento, e cada correção realimenta os testes de regressão. As métricas de qualidade são medidas, monitoradas e reportadas internamente com cadência mensal.

---

## Artefato 5 — Roadmap de IA (MVP → Avançado)

| Nível | Fase | Capacidade de IA | Componentes ativos | Casos de uso entregues | Risco |
|-------|------|-----------------|--------------------|-----------------------|-------|
| **L1** | MVP — Ano 1 Q1–Q2 | **Determinística** — regras + tabelas | Rules Engine + OCR básico | Declaração IRPF guiada, escolha completa vs. simplificada, cálculo de restituição, deduções principais | Baixo |
| **L2** | V1 — Ano 1 Q3 → Ano 2 Q1 | **Machine Learning** — classificação, OCR avançado | + ML de classificação, OCR robusto, NER tributário, feature store | Captura automática de dedutíveis, carnê-leão, livro-caixa do autônomo, simulações de cenários · Categorização automática de transações bancárias Open Finance · Identificação de deduções no extrato em tempo real · Livro-caixa automático para MEI/autônomo | Médio |
| **L3** | V2 — Ano 2 | **LLM + RAG** — chat fundamentado, sugestões proativas | + LLM com roteamento, RAG sobre IN RFB/CARF/STJ, guardrails, human-in-the-loop | Chat tributário 24/7, alertas proativos de economia anual, DARF de ganho de capital e exterior | Alto |
| **L4** | V3 — Ano 3 | **IA Agêntica** — executa com aprovação humana | + Orquestração agêntica (LangGraph), integração e-CAC, checkpoints obrigatórios | Gera e paga DARF automaticamente, pré-preenche e transmite declaração via e-CAC, prediz risco de malha fina | Crítico (controlado) |

### Evolução da capacidade

```
L1               L2              L3                  L4
Determinístico   ML              LLM + RAG           Agêntica
Regras+Tabelas ─► +OCR+Classif ─► +Chat+Proativo ─► +Executa/Transmite
"Calcula certo"  "Captura tudo"  "Explica e sugere"  "Faz por você"
Risco: Baixo     Risco: Médio    Risco: Alto         Risco: Crítico (controlado)
```

### Gates de go/no-go entre níveis

| Transição | Gate de entrada | Gate de saída |
|-----------|-----------------|---------------|
| L1 → L2 | Acurácia Rules Engine ≥ 98%; zero incidentes LGPD | NSM ≥ R$ 600/usuário validado no beta; ativação ≥ 35% |
| L2 → L3 | Precisão ML ≥ 90%; OCR ≥ 95%; churn pago < 30% | NPS ≥ 45; uso fora de temporada ≥ 25% MAU |
| L3 → L4 | Taxa de alucinação < 2%; citação em 100% das respostas tributárias | Aprovação jurídica completa do escopo agêntico; infra de auditoria imutável em produção |

---

## Status dos Artefatos — Módulo 07

| # | Artefato | Status |
|---|---------|--------|
| 1 | Arquitetura da Camada de IA (4 camadas + tabela por componente) | ✅ Concluído |
| 2 | Casos de Uso de IA por Persona (16 casos — 4 por persona, incluindo Open Finance) | ✅ Concluído |
| 3 | Plano de Treinamento e Atualização do Modelo | ✅ Concluído |
| 4 | Riscos de IA e Mitigações (12 riscos + 5 princípios de IA Responsável) | ✅ Concluído |
| 5 | Roadmap de IA — 4 níveis com gates de go/no-go | ✅ Concluído |

**Próxima etapa:** Projeto Final — Apresentação completa do GuIA
