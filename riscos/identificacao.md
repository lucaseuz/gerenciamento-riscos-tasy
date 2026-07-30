# Etapa 1 — Identificação dos Riscos

## 1. Introdução

Este documento apresenta a identificação dos riscos associados ao projeto **"Automatização da Auditoria de Contas Hospitalares para Prevenção de Inconsistências no Faturamento"**.

A identificação foi conduzida com base nas seguintes referências:

- **PMBOK 7ª Edição** — Domínio de Desempenho de Incerteza;
- **ISO 31000:2018** — Gestão de Riscos;
- **Boas práticas de Engenharia de Software** aplicadas ao contexto hospitalar.

O escopo do projeto consiste em uma melhoria no ERP hospitalar (Tasy) para validar automaticamente a existência de repasses financeiros vinculados a itens de contas hospitalares antes de permitir sua exclusão pelo auditor.

---

## 2. Metodologia de Identificação

A identificação dos riscos considerou:

- Análise do processo atual de auditoria de contas hospitalares;
- Mapeamento do fluxo de exclusão de itens e sua relação com repasses médicos;
- Entrevistas estruturadas (simuladas) com stakeholders;
- Revisão de cenários técnicos e organizacionais;
- Categorização conforme a **Estrutura Analítica de Riscos (EAR)**.

### Categorias utilizadas

| Categoria       | Descrição                                                                 |
|-----------------|---------------------------------------------------------------------------|
| Técnico         | Riscos relacionados à implementação, integração, banco de dados e testes |
| Operacional     | Riscos no processo de trabalho dos auditores e usuários do sistema        |
| Organizacional  | Riscos de gestão, priorização, governança e recursos humanos             |
| Negócio         | Riscos com impacto financeiro, regulatório ou de reputação               |

---

## 3. Registro de Riscos

| ID     | Nome do Risco                                           | Descrição                                                                                                                                                  | Contexto de Ocorrência                                                                                               | Categoria      | Consequência Caso Ocorra                                                                                                                           |
|--------|---------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| RSK-01 | Mapeamento incompleto das regras de repasse             | As regras de negócio que vinculam itens da conta hospitalar a repasses médicos podem não estar completamente documentadas ou mapeadas no sistema.          | Durante a fase de levantamento de requisitos, ao identificar quais tabelas e campos do banco de dados devem ser consultados pela validação.            | Técnico        | A validação pode falhar silenciosamente para determinados itens, permitindo exclusões indevidas e mantendo a vulnerabilidade que o projeto visa corrigir. |
| RSK-02 | Incompatibilidade com customizações existentes no ERP   | O ERP Tasy permite customizações por instituição. A nova funcionalidade pode conflitar com triggers, procedures ou validações já implementadas.            | Durante a integração da validação de repasse com os módulos de auditoria e faturamento já customizados.               | Técnico        | Erros em cascata no processo de auditoria, travamento de telas ou comportamentos inesperados na exclusão de itens.                                   |
| RSK-03 | Degradação de performance nas consultas ao banco        | A validação em tempo real exige consulta a tabelas de repasse a cada tentativa de exclusão, podendo gerar lentidão se as queries não forem otimizadas.     | Em ambiente de produção, durante períodos de alta demanda, como fechamento mensal de contas ou picos de atendimento.   | Técnico        | Lentidão perceptível no processo de auditoria, impactando a produtividade dos auditores e gerando insatisfação com a ferramenta.                     |
| RSK-04 | Resistência dos auditores à nova regra de bloqueio      | Os auditores podem interpretar o bloqueio como uma limitação à sua autonomia profissional, resistindo à adoção da funcionalidade.                          | Após a implantação, quando o auditor tentar excluir um item e receber a mensagem de bloqueio pela primeira vez.        | Operacional    | Tentativas de contornar a validação por caminhos alternativos, abertura de chamados recorrentes ou baixa adesão à funcionalidade.                    |
| RSK-05 | Mensagem de bloqueio inadequada ou confusa              | A mensagem apresentada ao auditor pode ser técnica demais, ambígua ou insuficiente para explicar o motivo do impedimento e orientar o próximo passo.       | No momento em que o sistema exibe o alerta de bloqueio durante a tentativa de exclusão de um item com repasse.         | Operacional    | Confusão do usuário, aumento de chamados ao suporte técnico, percepção negativa da funcionalidade e possível rejeição da melhoria.                   |
| RSK-06 | Ausência de ambiente de homologação adequado            | A instituição pode não dispor de um ambiente de testes com massa de dados representativa para validação completa da funcionalidade antes da implantação.    | Durante a fase de testes e homologação, ao tentar simular cenários reais de exclusão de itens com repasse vinculado.   | Organizacional | Testes incompletos ou não representativos, levando à implantação de uma solução com falhas não detectadas previamente.                               |
| RSK-07 | Priorização concorrente com outros projetos de TI       | A equipe de TI pode ter demandas simultâneas mais urgentes, levando ao adiamento ou redução do escopo da implementação.                                    | Durante o planejamento do sprint ou ciclo de desenvolvimento, quando a demanda compete com correções emergenciais.     | Organizacional | Atrasos na entrega, perda da janela de implantação e prolongamento da exposição ao risco financeiro que a solução visa eliminar.                     |
| RSK-08 | Falha na rastreabilidade dos registros de tentativa     | O log de tentativas de exclusão bloqueadas pode não registrar informações suficientes (usuário, data, item, motivo) para fins de auditoria e compliance.   | Quando a coordenação da auditoria ou o setor financeiro necessitar consultar o histórico de bloqueios para investigação. | Negócio        | Perda de evidências para auditoria interna ou externa, comprometendo a rastreabilidade exigida por normas regulatórias do setor de saúde.            |
| RSK-09 | Impacto financeiro por bloqueios incorretos (falso positivo) | A validação pode identificar erroneamente um repasse vinculado a um item que, na verdade, já foi estornado ou cancelado, bloqueando exclusões legítimas. | Quando o auditor tenta excluir um item cujo repasse foi cancelado, mas o registro permanece ativo no banco de dados.   | Negócio        | Atraso no fechamento de contas, retrabalho do auditor, necessidade de intervenção manual da TI e insatisfação com a solução.                        |
| RSK-10 | Falta de alinhamento entre stakeholders sobre o escopo  | Stakeholders podem ter expectativas divergentes sobre o que a solução irá ou não cobrir, gerando solicitações de escopo não previstas.                     | Durante as reuniões de validação e homologação, quando stakeholders solicitam funcionalidades fora do escopo definido. | Organizacional | Retrabalho na definição de requisitos, atraso no cronograma, conflitos entre áreas e risco de entrega de uma solução que não atende a todos.         |

---

## 4. Considerações

- Foram identificados **10 riscos** distribuídos entre as categorias técnica (3), operacional (2), organizacional (3) e de negócio (2).
- Cada risco foi contextualizado dentro do fluxo real de auditoria de contas hospitalares.
- Riscos genéricos (como "falta de orçamento" ou "saída de membros da equipe") foram evitados, priorizando riscos específicos e aderentes ao cenário descrito.
- A identificação considerou tanto a fase de desenvolvimento quanto a fase de implantação e operação da funcionalidade.

---

## 5. Referências

- PMI. *Um Guia do Conhecimento em Gerenciamento de Projetos (Guia PMBOK)*. 7ª Edição. Project Management Institute, 2021.
- ABNT. *NBR ISO 31000:2018 — Gestão de riscos — Diretrizes*. Associação Brasileira de Normas Técnicas, 2018.
- Philips Tasy. *Documentação técnica do ERP Tasy*. Referência geral de funcionalidades de auditoria e faturamento.

---

*Documento gerado com apoio de Inteligência Artificial Generativa e revisado para adequação ao contexto do projeto.*
