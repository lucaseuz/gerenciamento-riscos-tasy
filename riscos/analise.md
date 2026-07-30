# Etapa 2 — Análise Qualitativa dos Riscos

## 1. Introdução

Este documento apresenta a análise qualitativa dos riscos identificados na Etapa 1 do projeto **"Automatização da Auditoria de Contas Hospitalares para Prevenção de Inconsistências no Faturamento"**.

A análise foi conduzida com base nos seguintes critérios:

- **Probabilidade de ocorrência**: Baixa, Média ou Alta;
- **Impacto no projeto**: Baixo, Médio ou Alto;
- **Justificativa**: fundamentação técnica e contextual para a classificação atribuída.

As classificações seguem as diretrizes da **ISO 31000:2018** e do **PMBOK 7ª Edição**, aplicadas ao contexto específico de uma melhoria em ERP hospitalar.

---

## 2. Critérios de Classificação

### Probabilidade

| Nível  | Descrição                                                                                     |
|--------|-----------------------------------------------------------------------------------------------|
| Baixa  | Evento improvável nas condições normais do projeto; requer falha em múltiplos controles.      |
| Média  | Evento possível, considerando o histórico e as condições organizacionais e técnicas do cenário.|
| Alta   | Evento esperado ou muito provável, dadas as circunstâncias e experiências anteriores similares.|

### Impacto

| Nível  | Descrição                                                                                      |
|--------|------------------------------------------------------------------------------------------------|
| Baixo  | Impacto limitado, absorvido sem alteração significativa no cronograma, custo ou qualidade.     |
| Médio  | Impacto moderado, exigindo ações corretivas e possível replanejamento parcial.                 |
| Alto   | Impacto severo, comprometendo entregas críticas, integridade financeira ou a viabilidade do projeto. |

---

## 3. Análise Individual dos Riscos

### RSK-01 — Mapeamento incompleto das regras de repasse

| Campo                          | Descrição                                                                                                                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Descrição**                  | As regras que vinculam itens da conta hospitalar a repasses médicos podem não estar completamente documentadas ou mapeadas no banco de dados do ERP.                                            |
| **Possíveis Impactos**         | Exclusões indevidas de itens com repasse; persistência da vulnerabilidade financeira; falsa sensação de segurança após a implantação.                                                           |
| **Fatores que Influenciam**    | Complexidade das tabelas de repasse no Tasy; variação entre contratos médicos; ausência de documentação atualizada das regras customizadas.                                                     |
| **Probabilidade**              | **Alta**                                                                                                                                                                                        |
| **Impacto**                    | **Alto**                                                                                                                                                                                        |
| **Justificativa**              | Em ERPs hospitalares customizados, é comum que regras de repasse sejam implementadas de forma incremental ao longo dos anos, sem documentação centralizada. A probabilidade é alta porque a equipe pode não ter visibilidade de todas as variações. O impacto é alto porque uma validação incompleta anula o propósito do projeto. |

---

### RSK-02 — Incompatibilidade com customizações existentes no ERP

| Campo                          | Descrição                                                                                                                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Descrição**                  | A nova validação pode conflitar com triggers, stored procedures ou personalizações já implementadas nos módulos de auditoria e faturamento.                                                     |
| **Possíveis Impactos**         | Erros em cascata; travamento de funcionalidades existentes; comportamentos inesperados na interface do auditor.                                                                                  |
| **Fatores que Influenciam**    | Nível de customização acumulada no ambiente; ausência de documentação das customizações anteriores; acoplamento entre módulos.                                                                   |
| **Probabilidade**              | **Média**                                                                                                                                                                                       |
| **Impacto**                    | **Alto**                                                                                                                                                                                        |
| **Justificativa**              | Ambientes Tasy frequentemente possuem customizações acumuladas, mas a equipe de TI costuma ter conhecimento parcial dessas implementações. A probabilidade é média porque pode ser mitigada com análise prévia. O impacto é alto porque um conflito pode desestabilizar processos críticos de faturamento. |

---

### RSK-03 — Degradação de performance nas consultas ao banco

| Campo                          | Descrição                                                                                                                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Descrição**                  | A consulta em tempo real a tabelas de repasse a cada tentativa de exclusão pode gerar lentidão, especialmente em períodos de alta demanda.                                                      |
| **Possíveis Impactos**         | Aumento no tempo de resposta do sistema; queda de produtividade dos auditores; sobrecarga no servidor de banco de dados.                                                                        |
| **Fatores que Influenciam**    | Volume de registros nas tabelas de repasse; indexação adequada; concorrência de acessos; infraestrutura do servidor de banco de dados.                                                          |
| **Probabilidade**              | **Média**                                                                                                                                                                                       |
| **Impacto**                    | **Médio**                                                                                                                                                                                       |
| **Justificativa**              | Consultas a tabelas transacionais em ERPs hospitalares são operações rotineiras e, com indexação adequada, não costumam degradar a performance. A probabilidade é média por depender da volumetria e indexação. O impacto é médio porque afeta a usabilidade, mas não compromete a integridade dos dados. |

---

### RSK-04 — Resistência dos auditores à nova regra de bloqueio

| Campo                          | Descrição                                                                                                                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Descrição**                  | Auditores podem perceber o bloqueio como limitação à sua autonomia, resistindo à adoção e buscando caminhos alternativos.                                                                       |
| **Possíveis Impactos**         | Baixa adesão à funcionalidade; tentativas de contorno do bloqueio; abertura de chamados recorrentes; clima organizacional negativo.                                                             |
| **Fatores que Influenciam**    | Cultura organizacional; nível de participação dos auditores na definição da solução; qualidade do treinamento e comunicação prévia.                                                             |
| **Probabilidade**              | **Média**                                                                                                                                                                                       |
| **Impacto**                    | **Médio**                                                                                                                                                                                       |
| **Justificativa**              | Mudanças que restringem ações dos usuários frequentemente geram resistência inicial. A probabilidade é média porque pode ser reduzida com boa comunicação. O impacto é médio porque a resistência pode atrasar a adoção, mas não impede a entrega técnica. |

---

### RSK-05 — Mensagem de bloqueio inadequada ou confusa

| Campo                          | Descrição                                                                                                                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Descrição**                  | A mensagem exibida ao auditor pode ser técnica demais, genérica ou insuficiente para orientar a ação correta.                                                                                   |
| **Possíveis Impactos**         | Confusão do usuário; aumento de chamados ao suporte; percepção negativa da funcionalidade; necessidade de retrabalho na implementação.                                                          |
| **Fatores que Influenciam**    | Participação de usuários finais na validação da mensagem; revisão por equipe de UX ou comunicação; testes de usabilidade.                                                                       |
| **Probabilidade**              | **Baixa**                                                                                                                                                                                       |
| **Impacto**                    | **Baixo**                                                                                                                                                                                       |
| **Justificativa**              | A mensagem pode ser facilmente validada com os auditores antes da implantação. A probabilidade é baixa porque é um item simples de ajustar. O impacto é baixo porque, mesmo inadequada, a mensagem não compromete a função de bloqueio em si. |

---

### RSK-06 — Ausência de ambiente de homologação adequado

| Campo                          | Descrição                                                                                                                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Descrição**                  | A instituição pode não dispor de ambiente de testes com massa de dados representativa para validação completa antes da implantação.                                                              |
| **Possíveis Impactos**         | Testes incompletos; cenários não cobertos; implantação com defeitos não detectados; necessidade de correções emergenciais.                                                                       |
| **Fatores que Influenciam**    | Maturidade do processo de TI; disponibilidade de infraestrutura; política de gestão de ambientes da instituição.                                                                                |
| **Probabilidade**              | **Média**                                                                                                                                                                                       |
| **Impacto**                    | **Alto**                                                                                                                                                                                        |
| **Justificativa**              | Muitas instituições hospitalares operam com ambientes de homologação defasados ou sem massa de dados atualizada. A probabilidade é média por depender da maturidade da TI local. O impacto é alto porque testar em ambiente inadequado pode mascarar defeitos críticos. |

---

### RSK-07 — Priorização concorrente com outros projetos de TI

| Campo                          | Descrição                                                                                                                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Descrição**                  | Demandas emergenciais ou projetos de maior prioridade podem adiar a implementação ou reduzir os recursos dedicados.                                                                              |
| **Possíveis Impactos**         | Atrasos na entrega; redução do escopo; perda da janela de implantação; prolongamento da exposição ao risco financeiro.                                                                           |
| **Fatores que Influenciam**    | Volume de demandas de TI; nível de patrocínio da diretoria; criticidade percebida do projeto; planejamento de capacidade da equipe.                                                             |
| **Probabilidade**              | **Alta**                                                                                                                                                                                        |
| **Impacto**                    | **Médio**                                                                                                                                                                                       |
| **Justificativa**              | Equipes de TI hospitalares tipicamente operam com alta demanda e frequentes urgências. A probabilidade é alta porque a concorrência com outros projetos é recorrente. O impacto é médio porque o atraso não inviabiliza o projeto, mas prolonga a exposição ao risco. |

---

### RSK-08 — Falha na rastreabilidade dos registros de tentativa

| Campo                          | Descrição                                                                                                                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Descrição**                  | O registro de tentativas de exclusão bloqueadas pode não capturar informações suficientes para auditoria e conformidade regulatória.                                                            |
| **Possíveis Impactos**         | Perda de evidências para auditoria interna e externa; não conformidade com exigências regulatórias; comprometimento da rastreabilidade.                                                         |
| **Fatores que Influenciam**    | Definição dos campos a serem registrados; capacidade de armazenamento; requisitos regulatórios do setor de saúde; integração com o módulo de log do ERP.                                        |
| **Probabilidade**              | **Baixa**                                                                                                                                                                                       |
| **Impacto**                    | **Alto**                                                                                                                                                                                        |
| **Justificativa**              | O registro de logs é uma funcionalidade bem conhecida e relativamente simples de implementar. A probabilidade é baixa porque a equipe de TI possui experiência com este tipo de requisito. O impacto é alto porque a ausência de rastreabilidade pode ter consequências regulatórias sérias no setor de saúde. |

---

### RSK-09 — Impacto financeiro por bloqueios incorretos (falso positivo)

| Campo                          | Descrição                                                                                                                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Descrição**                  | A validação pode bloquear exclusões legítimas ao identificar erroneamente repasses que já foram estornados ou cancelados.                                                                       |
| **Possíveis Impactos**         | Atraso no fechamento de contas; retrabalho do auditor; necessidade de intervenção da TI; perda de credibilidade da solução.                                                                     |
| **Fatores que Influenciam**    | Tratamento adequado de status do repasse (ativo, cancelado, estornado); qualidade da query de validação; cobertura de cenários nos testes.                                                      |
| **Probabilidade**              | **Média**                                                                                                                                                                                       |
| **Impacto**                    | **Alto**                                                                                                                                                                                        |
| **Justificativa**              | Repasses podem ter ciclos de vida complexos (ativo, parcialmente pago, estornado, cancelado). A probabilidade é média porque a query deve considerar múltiplos status. O impacto é alto porque bloqueios indevidos prejudicam o fluxo de trabalho e a credibilidade da solução. |

---

### RSK-10 — Falta de alinhamento entre stakeholders sobre o escopo

| Campo                          | Descrição                                                                                                                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Descrição**                  | Stakeholders podem ter expectativas divergentes sobre a abrangência da solução, solicitando funcionalidades não previstas.                                                                      |
| **Possíveis Impactos**         | Escopo não controlado (*scope creep*); retrabalho; conflitos entre áreas; atraso na entrega; solução que não atende plenamente a nenhum grupo.                                                  |
| **Fatores que Influenciam**    | Clareza da documentação de escopo; frequência de comunicação; envolvimento dos stakeholders desde o início; existência de termo de abertura do projeto.                                         |
| **Probabilidade**              | **Média**                                                                                                                                                                                       |
| **Impacto**                    | **Médio**                                                                                                                                                                                       |
| **Justificativa**              | A multiplicidade de stakeholders (auditores, TI, faturamento, diretoria) naturalmente gera expectativas diferentes. A probabilidade é média porque pode ser mitigada com comunicação estruturada. O impacto é médio porque divergências de escopo são gerenciáveis com governança adequada. |

---

## 4. Matriz Qualitativa de Probabilidade × Impacto

A matriz abaixo consolida a classificação de todos os riscos identificados:

|                    | **Impacto Baixo**  | **Impacto Médio**    | **Impacto Alto**          |
|--------------------|--------------------|-----------------------|---------------------------|
| **Prob. Alta**     |                    | RSK-07                | RSK-01                    |
| **Prob. Média**    |                    | RSK-03, RSK-04, RSK-10 | RSK-02, RSK-06, RSK-09   |
| **Prob. Baixa**    | RSK-05             |                       | RSK-08                    |

### Legenda de Criticidade

| Zona                | Criticidade | Ação Recomendada                                      |
|---------------------|-------------|-------------------------------------------------------|
| 🔴 Vermelho (Alta × Alto) | **Crítica**     | Resposta imediata obrigatória; monitoramento contínuo |
| 🟠 Laranja (Alta × Médio / Média × Alto) | **Elevada** | Plano de resposta prioritário; acompanhamento frequente |
| 🟡 Amarelo (Média × Médio / Baixa × Alto / Alta × Baixo) | **Moderada** | Plano de contingência; monitoramento periódico |
| 🟢 Verde (Baixa × Baixo / Baixa × Médio) | **Baixa** | Aceitar e monitorar |

### Classificação por Criticidade

| Criticidade  | Riscos                         |
|--------------|--------------------------------|
| 🔴 Crítica   | RSK-01                         |
| 🟠 Elevada   | RSK-02, RSK-06, RSK-07, RSK-09 |
| 🟡 Moderada  | RSK-03, RSK-04, RSK-08, RSK-10 |
| 🟢 Baixa     | RSK-05                         |

---

## 5. Considerações

- O risco **RSK-01 (Mapeamento incompleto das regras de repasse)** é o mais crítico do projeto, pois compromete diretamente o objetivo central da solução.
- Os riscos de criticidade elevada (RSK-02, RSK-06, RSK-07, RSK-09) exigem planos de resposta estruturados antes do início da implementação.
- A análise reforça a importância de um levantamento exaustivo das regras de repasse e de um ambiente de testes representativo.
- A Etapa 3 (Estratégias de Resposta) definirá as ações concretas para tratar cada risco identificado e analisado.

---

## 6. Referências

- PMI. *Um Guia do Conhecimento em Gerenciamento de Projetos (Guia PMBOK)*. 7ª Edição. Project Management Institute, 2021.
- ABNT. *NBR ISO 31000:2018 — Gestão de riscos — Diretrizes*. Associação Brasileira de Normas Técnicas, 2018.

---

*Documento gerado com apoio de Inteligência Artificial Generativa e revisado para adequação ao contexto do projeto.*
