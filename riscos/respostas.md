# Etapa 3 — Estratégias de Resposta aos Riscos

## 1. Introdução

Este documento apresenta as estratégias de resposta para cada risco identificado e analisado nas Etapas 1 e 2 do projeto **"Automatização da Auditoria de Contas Hospitalares para Prevenção de Inconsistências no Faturamento"**.

Para cada risco, são apresentadas quatro estratégias possíveis conforme o **PMBOK 7ª Edição** e a **ISO 31000:2018**:

| Estratégia   | Descrição                                                                  |
|--------------|----------------------------------------------------------------------------|
| **Evitar**   | Eliminar a causa raiz ou alterar o plano para que o risco não ocorra.      |
| **Mitigar**  | Reduzir a probabilidade e/ou o impacto do risco a níveis aceitáveis.       |
| **Transferir** | Deslocar a responsabilidade ou o impacto do risco para um terceiro.      |
| **Aceitar**  | Reconhecer o risco sem ação proativa, com ou sem plano de contingência.     |

Ao final de cada análise, a **estratégia recomendada** é indicada com justificativa e ações práticas.

---

## 2. Respostas por Risco

---

### RSK-01 — Mapeamento incompleto das regras de repasse
**Criticidade: 🔴 Crítica**

| Estratégia       | Descrição da Resposta                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Evitar**       | Realizar um levantamento exaustivo de todas as regras de repasse junto ao setor financeiro e à equipe de TI antes de iniciar o desenvolvimento, bloqueando o avanço até a conclusão do mapeamento. |
| **Mitigar**      | Conduzir o levantamento em fases, começando pelos contratos de repasse mais representativos, e implementar a validação de forma incremental à medida que novas regras forem mapeadas.              |
| **Transferir**   | Contratar consultoria especializada no ERP Tasy para realizar o mapeamento das regras de repasse e garantir a completude do levantamento.                          |
| **Aceitar**      | Implantar a validação com o mapeamento disponível e aceitar que alguns cenários possam não estar cobertos inicialmente, tratando-os como melhorias futuras.         |

**✅ Estratégia Recomendada: Evitar**

**Justificativa:** Este é o risco mais crítico do projeto. Se o mapeamento for incompleto, a validação falhará silenciosamente, mantendo a vulnerabilidade que o projeto visa corrigir. A estratégia de evitar é a mais adequada porque garante que o pré-requisito fundamental da solução — conhecer todas as regras de repasse — seja atendido antes do desenvolvimento.

**Ações Práticas:**
1. Agendar reunião com o Gestor Financeiro e a Coordenação da Auditoria para mapear todos os contratos de repasse ativos.
2. Solicitar à equipe de TI a documentação das tabelas, views e procedures relacionadas a repasses no banco de dados.
3. Criar uma matriz de cobertura que liste todos os tipos de repasse × itens da conta hospitalar.
4. Validar a matriz com o Faturamento Hospitalar antes de iniciar a codificação.
5. Estabelecer como critério de aceite: 100% dos tipos de repasse documentados e validados.

---

### RSK-02 — Incompatibilidade com customizações existentes no ERP
**Criticidade: 🟠 Elevada**

| Estratégia       | Descrição da Resposta                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Evitar**       | Realizar auditoria técnica completa de todas as customizações existentes nos módulos de auditoria e faturamento antes do desenvolvimento.                           |
| **Mitigar**      | Desenvolver a validação de forma desacoplada, utilizando uma camada de abstração que minimize o impacto sobre triggers e procedures existentes.                     |
| **Transferir**   | Solicitar ao fornecedor do ERP (Philips) suporte técnico para análise de compatibilidade antes da implementação.                                                   |
| **Aceitar**      | Implementar a solução e tratar conflitos à medida que forem identificados durante os testes de homologação.                                                         |

**✅ Estratégia Recomendada: Mitigar**

**Justificativa:** Auditar todas as customizações existentes pode ser inviável pelo volume acumulado ao longo dos anos. A estratégia de mitigar é mais realista: ao desenvolver a validação de forma desacoplada (ex: function independente chamada antes da exclusão), minimiza-se o risco de conflito sem exigir um levantamento completo de todas as customizações anteriores.

**Ações Práticas:**
1. Implementar a validação como uma function ou procedure independente no banco de dados.
2. Utilizar chamada da validação no ponto de entrada da exclusão (antes das triggers existentes).
3. Documentar a arquitetura da solução para facilitar a identificação de conflitos futuros.
4. Executar testes de regressão nos fluxos de auditoria e faturamento após a implementação.

---

### RSK-03 — Degradação de performance nas consultas ao banco
**Criticidade: 🟡 Moderada**

| Estratégia       | Descrição da Resposta                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Evitar**       | Implementar cache local dos repasses vinculados ao abrir a conta hospitalar, eliminando a necessidade de consulta em tempo real a cada exclusão.                    |
| **Mitigar**      | Otimizar a query de validação com índices adequados e limitar o escopo da consulta ao estritamente necessário (item específico × repasse ativo).                    |
| **Transferir**   | Solicitar à equipe de infraestrutura a alocação de recursos adicionais de processamento para o servidor de banco de dados.                                         |
| **Aceitar**      | Aceitar uma eventual degradação mínima de performance, considerando que a segurança financeira proporcionada justifica um leve aumento no tempo de resposta.       |

**✅ Estratégia Recomendada: Mitigar**

**Justificativa:** A otimização da query é a abordagem mais equilibrada. A consulta envolve um item específico e seus repasses vinculados, o que naturalmente limita o volume de dados. Com indexação adequada, a consulta será executada em milissegundos, sem impacto perceptível ao usuário.

**Ações Práticas:**
1. Criar índices compostos nas tabelas de repasse para os campos utilizados na validação.
2. Limitar a query ao item específico sendo excluído (filtro por chave primária).
3. Utilizar `EXPLAIN PLAN` (ou equivalente) para validar o plano de execução da query.
4. Realizar teste de performance com volume de dados representativo do ambiente de produção.

---

### RSK-04 — Resistência dos auditores à nova regra de bloqueio
**Criticidade: 🟡 Moderada**

| Estratégia       | Descrição da Resposta                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Evitar**       | Envolver os auditores desde a fase de levantamento de requisitos, garantindo que a solução seja percebida como uma ferramenta de apoio e não como uma restrição.    |
| **Mitigar**      | Realizar treinamento prévio, apresentando o problema financeiro que a solução resolve e demonstrando os benefícios operacionais para o próprio auditor.             |
| **Transferir**   | Delegar à Coordenação da Auditoria a comunicação e o gerenciamento da mudança junto aos auditores.                                                                 |
| **Aceitar**      | Aceitar que haverá resistência inicial e confiar que a experiência de uso demonstrará o valor da funcionalidade ao longo do tempo.                                 |

**✅ Estratégia Recomendada: Mitigar**

**Justificativa:** A resistência à mudança é natural e previsível. A melhor abordagem é mitigá-la com comunicação clara e treinamento, explicando que o bloqueio protege o próprio auditor de erros que poderiam gerar retrabalho e questionamentos futuros.

**Ações Práticas:**
1. Elaborar material de treinamento focado no *por quê* da mudança (e não apenas no *como*).
2. Apresentar exemplos reais (anonimizados) de inconsistências causadas por exclusões indevidas.
3. Incluir os auditores na validação da mensagem de bloqueio.
4. Designar um auditor referência como ponto focal para dúvidas na fase inicial.

---

### RSK-05 — Mensagem de bloqueio inadequada ou confusa
**Criticidade: 🟢 Baixa**

| Estratégia       | Descrição da Resposta                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Evitar**       | Validar o texto da mensagem com os auditores e a Coordenação da Auditoria antes da implementação.                                                                  |
| **Mitigar**      | Criar a mensagem seguindo diretrizes de UX Writing: linguagem clara, ação sugerida e informação contextual (qual item, qual repasse).                               |
| **Transferir**   | Solicitar à equipe de comunicação ou UX da instituição a redação da mensagem.                                                                                       |
| **Aceitar**      | Aceitar a versão inicial e ajustá-la com base no feedback dos primeiros usuários após a implantação.                                                                |

**✅ Estratégia Recomendada: Evitar**

**Justificativa:** É um risco simples de eliminar completamente. Basta validar a mensagem com os usuários finais antes da implementação. O custo de prevenção é mínimo e evita retrabalho posterior.

**Ações Práticas:**
1. Redigir 2 a 3 versões da mensagem de bloqueio.
2. Apresentar as versões a um grupo de auditores para coleta de feedback.
3. Incluir na mensagem: identificação do item, informação do repasse vinculado e orientação do próximo passo.
4. Exemplo de mensagem validada: *"Não é possível excluir o item [Nome do Item]. Existe repasse médico vinculado (Nº [ID do Repasse]). Para prosseguir, consulte a Coordenação da Auditoria."*

---

### RSK-06 — Ausência de ambiente de homologação adequado
**Criticidade: 🟠 Elevada**

| Estratégia       | Descrição da Resposta                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Evitar**       | Provisionar um ambiente de homologação dedicado, com cópia recente da base de produção (anonimizada), antes do início dos testes.                                   |
| **Mitigar**      | Utilizar o ambiente disponível, mas complementar os testes com scripts automatizados que simulem cenários não cobertos pela massa de dados existente.               |
| **Transferir**   | Solicitar ao fornecedor do ERP ou à equipe de infraestrutura a preparação do ambiente de homologação.                                                               |
| **Aceitar**      | Utilizar o ambiente disponível e aceitar o risco de cenários não testados, tratando-os como correções após a implantação.                                           |

**✅ Estratégia Recomendada: Mitigar**

**Justificativa:** Provisionar um ambiente dedicado pode ser custoso e demorado. A estratégia de mitigar é mais pragmática: utilizar o ambiente disponível e complementar com scripts de teste que cubram cenários críticos (repasse ativo, cancelado, estornado, parcialmente pago, etc.).

**Ações Práticas:**
1. Solicitar à equipe de TI a atualização da massa de dados do ambiente de homologação.
2. Criar scripts de inserção de dados de teste que representem os cenários críticos de repasse.
3. Documentar a matriz de cenários de teste e evidenciar a cobertura alcançada.
4. Priorizar nos testes os cenários de maior criticidade: repasse ativo e repasse estornado.

---

### RSK-07 — Priorização concorrente com outros projetos de TI
**Criticidade: 🟠 Elevada**

| Estratégia       | Descrição da Resposta                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Evitar**       | Obter patrocínio formal da Diretoria Hospitalar e da Gestão Financeira, garantindo prioridade protegida para o projeto no backlog de TI.                           |
| **Mitigar**      | Dimensionar a implementação para que possa ser executada em um sprint curto (1-2 semanas), reduzindo a exposição a mudanças de prioridade.                         |
| **Transferir**   | Contratar desenvolvedor externo especializado em Tasy para executar a implementação, sem depender da equipe interna.                                               |
| **Aceitar**      | Aceitar que o projeto pode ser adiado e manter o risco financeiro da exclusão indevida até que haja janela de implementação.                                        |

**✅ Estratégia Recomendada: Mitigar**

**Justificativa:** Obter prioridade absoluta é difícil em ambientes de TI hospitalar com alta demanda. A estratégia mais eficaz é dimensionar o projeto para execução rápida, reduzindo a janela de exposição a mudanças de prioridade e facilitando o encaixe entre demandas.

**Ações Práticas:**
1. Estruturar a implementação em pacotes pequenos e independentes.
2. Documentar o escopo de forma clara para evitar expansões durante o desenvolvimento.
3. Apresentar à Diretoria o custo financeiro da não implementação (riscos de glosas e inconsistências).
4. Definir prazo máximo de entrega de 2 semanas para a implementação técnica.

---

### RSK-08 — Falha na rastreabilidade dos registros de tentativa
**Criticidade: 🟡 Moderada**

| Estratégia       | Descrição da Resposta                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Evitar**       | Definir antecipadamente, com a Coordenação da Auditoria, os campos obrigatórios do registro de tentativa (usuário, data/hora, item, repasse, motivo do bloqueio). |
| **Mitigar**      | Implementar o registro utilizando a estrutura de log já existente no ERP, adicionando apenas os campos específicos necessários.                                    |
| **Transferir**   | Delegar à equipe de compliance a definição dos requisitos de rastreabilidade e validação do formato do registro.                                                    |
| **Aceitar**      | Implementar o registro com os campos básicos e complementar após feedback da auditoria interna.                                                                     |

**✅ Estratégia Recomendada: Evitar**

**Justificativa:** A definição dos campos de registro é um requisito simples de especificar antecipadamente. Envolver a Coordenação da Auditoria na definição garante que o log atenda às necessidades de compliance desde a primeira versão, evitando retrabalho.

**Ações Práticas:**
1. Reunir-se com a Coordenação da Auditoria para definir os campos obrigatórios do log.
2. Campos mínimos sugeridos: data/hora, login do auditor, número da conta, item tentado, ID do repasse vinculado, ação realizada (bloqueio).
3. Implementar o registro na tabela de log do ERP ou em tabela dedicada.
4. Criar relatório de consulta dos bloqueios registrados para a Coordenação da Auditoria.

---

### RSK-09 — Impacto financeiro por bloqueios incorretos (falso positivo)
**Criticidade: 🟠 Elevada**

| Estratégia       | Descrição da Resposta                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Evitar**       | Mapear exaustivamente todos os status possíveis de repasse (ativo, cancelado, estornado, parcialmente pago) e incluir todos na lógica de validação.                 |
| **Mitigar**      | Considerar na validação apenas repasses com status "ativo" ou "parcialmente pago", ignorando repasses cancelados e estornados.                                     |
| **Transferir**   | Solicitar ao Gestor Financeiro a definição formal de quais status de repasse devem ser considerados "vinculados" para fins de bloqueio.                             |
| **Aceitar**      | Aceitar que falsos positivos podem ocorrer e disponibilizar um canal rápido de suporte para desbloqueio mediante justificativa.                                    |

**✅ Estratégia Recomendada: Evitar**

**Justificativa:** Falsos positivos comprometem a credibilidade da solução e geram retrabalho. A estratégia de evitar é viável porque exige apenas a definição clara de quais status de repasse são considerados "ativos" para fins de bloqueio — uma informação que o setor financeiro pode fornecer com precisão.

**Ações Práticas:**
1. Solicitar ao Gestor Financeiro a lista completa de status de repasse e seus significados.
2. Definir formalmente quais status devem acionar o bloqueio (ex: apenas "Ativo" e "Parcialmente Pago").
3. Incluir os status na lógica da query de validação como filtro explícito.
4. Criar cenários de teste para cada status de repasse, validando que estornados e cancelados não geram bloqueio.

---

### RSK-10 — Falta de alinhamento entre stakeholders sobre o escopo
**Criticidade: 🟡 Moderada**

| Estratégia       | Descrição da Resposta                                                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Evitar**       | Documentar o escopo de forma detalhada (incluindo o que está fora do escopo) e obter aceite formal de todos os stakeholders antes do desenvolvimento.               |
| **Mitigar**      | Realizar reuniões periódicas de alinhamento com representantes de cada área stakeholder para acompanhamento e gestão de expectativas.                               |
| **Transferir**   | Delegar ao Analista de Sistemas a responsabilidade de comunicar e alinhar o escopo com todas as áreas envolvidas.                                                  |
| **Aceitar**      | Aceitar que poderão surgir solicitações fora do escopo e avaliá-las individualmente para inclusão em versões futuras.                                               |

**✅ Estratégia Recomendada: Evitar**

**Justificativa:** O desalinhamento de escopo é uma das causas mais comuns de fracasso em projetos. A estratégia de evitar é a mais eficiente: documentar explicitamente o escopo e o não-escopo, com aceite formal, elimina a ambiguidade e protege a equipe de solicitações não previstas.

**Ações Práticas:**
1. Criar documento de escopo com seção explícita de "Não faz parte do escopo".
2. Apresentar o documento em reunião de kick-off com todos os stakeholders.
3. Obter assinatura ou aceite formal (e-mail) de cada representante de área.
4. Registrar solicitações adicionais em um backlog de melhorias futuras, sem incluí-las na versão atual.

---

## 3. Resumo das Estratégias Recomendadas

| ID     | Risco                                             | Estratégia Recomendada | Criticidade  |
|--------|---------------------------------------------------|------------------------|--------------|
| RSK-01 | Mapeamento incompleto das regras de repasse       | Evitar                 | 🔴 Crítica    |
| RSK-02 | Incompatibilidade com customizações do ERP        | Mitigar                | 🟠 Elevada    |
| RSK-03 | Degradação de performance                         | Mitigar                | 🟡 Moderada   |
| RSK-04 | Resistência dos auditores                         | Mitigar                | 🟡 Moderada   |
| RSK-05 | Mensagem de bloqueio inadequada                   | Evitar                 | 🟢 Baixa      |
| RSK-06 | Ausência de ambiente de homologação               | Mitigar                | 🟠 Elevada    |
| RSK-07 | Priorização concorrente                           | Mitigar                | 🟠 Elevada    |
| RSK-08 | Falha na rastreabilidade                          | Evitar                 | 🟡 Moderada   |
| RSK-09 | Bloqueios incorretos (falso positivo)             | Evitar                 | 🟠 Elevada    |
| RSK-10 | Falta de alinhamento de escopo                    | Evitar                 | 🟡 Moderada   |

---

## 4. Considerações

- **5 riscos** receberam a estratégia de **Evitar**, indicando que ações preventivas simples e de baixo custo podem eliminar ameaças significativas ao projeto.
- **4 riscos** receberam a estratégia de **Mitigar**, aplicada em cenários onde a eliminação total do risco não é viável, mas a redução da probabilidade ou impacto é possível.
- **Nenhum risco** recebeu a estratégia de **Aceitar** ou **Transferir** como recomendação principal, refletindo a criticidade do contexto hospitalar e a necessidade de controle ativo.
- As ações práticas foram definidas considerando a realidade operacional de instituições hospitalares que utilizam ERP Tasy.

---

## 5. Referências

- PMI. *Um Guia do Conhecimento em Gerenciamento de Projetos (Guia PMBOK)*. 7ª Edição. Project Management Institute, 2021.
- ABNT. *NBR ISO 31000:2018 — Gestão de riscos — Diretrizes*. Associação Brasileira de Normas Técnicas, 2018.

---

*Documento gerado com apoio de Inteligência Artificial Generativa e revisado para adequação ao contexto do projeto.*
