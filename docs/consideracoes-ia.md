# Etapa 7 — Uso da Inteligência Artificial Generativa no Projeto

## 1. Introdução

Este documento descreve como a **Inteligência Artificial Generativa (IAG)** foi utilizada como ferramenta de apoio no desenvolvimento do projeto acadêmico **"Automatização da Auditoria de Contas Hospitalares para Prevenção de Inconsistências no Faturamento"**.

O uso da IA seguiu uma abordagem de **coprodução**: a IA atuou como assistente especializado na geração de conteúdo estruturado, enquanto o profissional atuou como validador, revisor e tomador de decisões.

---

## 2. Como a IA Apoiou Cada Etapa

### Etapa 1 — Identificação dos Riscos

| Aspecto                | Descrição                                                                                                                                         |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| **Contribuição da IA** | Geração de riscos específicos ao cenário, categorizados (técnico, operacional, organizacional, negócio), com descrição, contexto e consequência. |
| **Entrada humana**     | Definição do cenário, escopo, contexto técnico (ERP Tasy, fluxo de auditoria, repasses), validação da relevância de cada risco.                   |
| **Valor agregado**     | Aceleração do processo de brainstorming estruturado; cobertura de categorias que poderiam ser negligenciadas em uma análise individual.            |

### Etapa 2 — Análise Qualitativa dos Riscos

| Aspecto                | Descrição                                                                                                                                       |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Contribuição da IA** | Classificação de probabilidade e impacto com justificativas fundamentadas; geração da matriz qualitativa de Probabilidade × Impacto.            |
| **Entrada humana**     | Validação das classificações com base na experiência profissional e no conhecimento do ambiente hospitalar específico.                           |
| **Valor agregado**     | Consistência nas justificativas; formatação profissional da matriz; análise de criticidade consolidada.                                          |

### Etapa 3 — Estratégias de Resposta

| Aspecto                | Descrição                                                                                                                                       |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Contribuição da IA** | Elaboração de quatro estratégias (evitar, mitigar, transferir, aceitar) para cada risco, com recomendação justificada e ações práticas.          |
| **Entrada humana**     | Avaliação da viabilidade das estratégias no contexto organizacional; ajuste das ações práticas à realidade operacional da instituição.           |
| **Valor agregado**     | Abordagem sistemática garantindo que todas as opções fossem consideradas antes da recomendação final.                                            |

### Etapa 4 — Comunicação com Stakeholders

| Aspecto                | Descrição                                                                                                                                       |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Contribuição da IA** | Redação do comunicado executivo em linguagem acessível para público não técnico (Diretoria Hospitalar).                                         |
| **Entrada humana**     | Validação do tom, adequação institucional, revisão de informações sensíveis e garantia de anonimização.                                         |
| **Valor agregado**     | Tradução eficiente de conteúdo técnico para linguagem executiva; estruturação profissional do documento.                                         |

### Etapa 5 — README e Estrutura do Repositório

| Aspecto                | Descrição                                                                                                                                       |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Contribuição da IA** | Geração da estrutura de pastas, README completo e organização dos artefatos seguindo padrões de repositórios profissionais no GitHub.            |
| **Entrada humana**     | Definição das preferências de organização; revisão da descrição do projeto; validação da estrutura proposta.                                     |
| **Valor agregado**     | Padronização automática; inclusão de elementos frequentemente esquecidos (LICENSE, prompts, documentação de uso da IA).                           |

---

## 3. Limitações Encontradas

| Limitação                                                    | Descrição                                                                                                                                                         |
|--------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Desconhecimento do ambiente específico**                   | A IA não possui acesso ao banco de dados, às customizações ou à configuração específica do ERP Tasy da instituição. Os riscos e estratégias foram baseados em conhecimento geral do sistema. |
| **Incapacidade de validar dados reais**                      | A IA não pode consultar tabelas de repasse, verificar status de registros ou validar a existência de triggers e procedures específicas.                           |
| **Risco de generalização**                                   | Sem orientação precisa do contexto, a IA poderia gerar riscos genéricos (ex: "falta de orçamento") que não agregam valor ao projeto específico.                   |
| **Viés de otimismo na classificação**                        | A IA pode subestimar a probabilidade ou impacto de riscos se o contexto fornecido não incluir informações sobre problemas históricos da instituição.               |
| **Ausência de conhecimento tácito**                          | Experiências anteriores da equipe, cultura organizacional e dinâmicas interpessoais não são capturáveis pela IA, mas influenciam diretamente a análise de riscos.  |

---

## 4. Informações que Necessitaram de Validação Humana

As seguintes informações geradas pela IA **exigiram revisão e validação por profissionais** com conhecimento do contexto:

1. **Relevância dos riscos identificados** — Verificar se cada risco realmente se aplica ao cenário específico da instituição e não é apenas uma possibilidade teórica.

2. **Classificação de probabilidade e impacto** — As classificações devem ser validadas com base no histórico real de incidentes e na experiência da equipe de TI e auditoria.

3. **Viabilidade das estratégias de resposta** — Nem todas as ações propostas podem ser executáveis no prazo, orçamento ou cultura organizacional da instituição.

4. **Adequação da linguagem do comunicado** — O tom institucional varia entre organizações; o comunicado deve ser revisado para aderir às práticas de comunicação da instituição.

5. **Completude das regras de negócio** — A IA não tem como saber se todas as regras de repasse foram consideradas; apenas a equipe técnica e o setor financeiro podem confirmar essa completude.

6. **Aderência às normas regulatórias** — Requisitos específicos de compliance do setor de saúde (ANS, TISS, auditorias externas) devem ser validados por profissionais da área.

---

## 5. Cuidados ao Utilizar IA em Projetos Hospitalares

### 5.1 Confidencialidade e Privacidade

- **Nunca fornecer dados reais de pacientes, médicos ou operadoras** à IA generativa.
- Utilizar sempre informações **anonimizadas** e cenários **genéricos** ao interagir com a ferramenta.
- Verificar se a política da instituição permite o uso de IA generativa e em quais condições.

### 5.2 Validação Obrigatória

- Todo conteúdo gerado pela IA deve ser **revisado por profissionais qualificados** antes de ser utilizado como documento oficial.
- Riscos, classificações e estratégias devem ser **validados com stakeholders** que possuem conhecimento do contexto real.
- A IA não substitui a análise crítica humana — ela **complementa e acelera** o processo.

### 5.3 Transparência

- Documentar explicitamente que a IA foi utilizada e em quais etapas.
- Manter registro dos prompts utilizados para garantir **reprodutibilidade**.
- Indicar nos artefatos que o conteúdo foi gerado com apoio de IA e revisado por profissionais.

### 5.4 Regulamentação

- O setor de saúde é altamente regulamentado. Decisões baseadas em conteúdo gerado por IA devem sempre considerar:
  - Normas da **ANS** (Agência Nacional de Saúde Suplementar);
  - Padrão **TISS** (Troca de Informação em Saúde Suplementar);
  - **LGPD** (Lei Geral de Proteção de Dados);
  - Requisitos de **acreditação hospitalar** (ONA, JCI).

### 5.5 Limites da IA

- A IA não possui **accountability** — a responsabilidade pelas decisões é sempre do profissional que valida e utiliza o conteúdo.
- A IA pode gerar conteúdo **plausível, porém incorreto** — a revisão crítica é indispensável.
- A IA não acessa **sistemas internos** — toda informação técnica específica deve ser fornecida pelo profissional.

---

## 6. Conclusão

A Inteligência Artificial Generativa demonstrou ser uma **ferramenta valiosa de produtividade** para o gerenciamento de riscos em projetos de software hospitalar, especialmente nas atividades de:

- Estruturação de documentos e artefatos;
- Brainstorming sistematizado de riscos;
- Análise comparativa de estratégias de resposta;
- Tradução de conteúdo técnico para linguagem executiva.

No entanto, seu uso **deve ser sempre acompanhado de validação humana**, especialmente em contextos hospitalares onde erros podem ter consequências financeiras, regulatórias e, em última instância, impactar a qualidade da assistência ao paciente.

---

## 7. Referências

- PMI. *Um Guia do Conhecimento em Gerenciamento de Projetos (Guia PMBOK)*. 7ª Edição. Project Management Institute, 2021.
- ABNT. *NBR ISO 31000:2018 — Gestão de riscos — Diretrizes*. Associação Brasileira de Normas Técnicas, 2018.
- Brasil. *Lei nº 13.709/2018 — Lei Geral de Proteção de Dados Pessoais (LGPD)*.

---

*Documento gerado com apoio de Inteligência Artificial Generativa e revisado para adequação ao contexto do projeto.*
