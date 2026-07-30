# 🏥 Gerenciamento de Riscos — Automatização da Auditoria de Contas Hospitalares

[![Status](https://img.shields.io/badge/Status-Conclu%C3%ADdo-brightgreen)]()
[![Licença](https://img.shields.io/badge/Licen%C3%A7a-MIT-blue)](LICENSE)
[![PMBOK](https://img.shields.io/badge/PMBOK-7%C2%AA%20Edi%C3%A7%C3%A3o-orange)]()
[![ISO](https://img.shields.io/badge/ISO-31000%3A2018-blue)]()
[![IA](https://img.shields.io/badge/IA%20Generativa-Utilizada-purple)]()

---

## 📋 Descrição do Projeto

Este repositório contém os artefatos do mini projeto acadêmico de **Gerenciamento de Riscos** desenvolvido para a disciplina de pós-graduação **Gerenciamento de Projetos de Software com Inteligência Artificial Generativa**.

O projeto aplica técnicas de gerenciamento de riscos — com base no **PMBOK 7ª Edição** e na **ISO 31000:2018** — a um cenário real de melhoria em sistema hospitalar, utilizando **Inteligência Artificial Generativa** como ferramenta de apoio na elaboração dos artefatos.

---

## 🎯 Objetivo

Criar uma solução que aumente a segurança do processo de auditoria hospitalar por meio da **automatização de validações de regras de negócio** durante a exclusão de itens da conta hospitalar.

A solução pretende reduzir:

- Erros operacionais
- Retrabalho
- Glosas pelas operadoras
- Inconsistências financeiras entre faturamento e repasse médico

---

## 🏗️ Contexto

O projeto é baseado em um cenário real de um hospital que utiliza o **ERP Tasy** para gestão hospitalar.

**Problema identificado:** durante o processo de auditoria das contas hospitalares, auditores podem excluir itens que possuem repasse financeiro vinculado a médicos. Essa exclusão pode provocar:

- Inconsistências financeiras
- Divergências entre faturamento e repasse médico
- Necessidade de retrabalho
- Glosas pelas operadoras
- Perda da rastreabilidade do processo

**Solução proposta:** desenvolver uma funcionalidade que valide automaticamente a existência de repasse financeiro vinculado ao item antes de permitir sua exclusão. Caso exista repasse, a exclusão é bloqueada e uma mensagem explicativa é apresentada ao auditor.

> ⚠️ **Nota:** O projeto representa uma melhoria de software e não o desenvolvimento completo do ERP. Todas as informações são apresentadas de forma anonimizada.

---

## 📂 Organização do Repositório

```
gerenciamento-de-risco/
│
├── README.md                              # Este arquivo
├── LICENSE                                # Licença MIT
│
├── riscos/                                # Documentação de riscos
│   ├── identificacao.md                   # Etapa 1 — Identificação dos riscos
│   ├── analise.md                         # Etapa 2 — Análise qualitativa dos riscos
│   └── respostas.md                       # Etapa 3 — Estratégias de resposta
│
├── comunicacao/                           # Documentação de comunicação
│   └── status-stakeholders.md             # Etapa 4 — Comunicação com stakeholders
│
├── docs/                                  # Outros documentos
│   └── consideracoes-ia.md                # Etapa 7 — Uso da IA Generativa
│
├── imagens/                               # Recursos visuais
│   ├── matriz-riscos.png                  # Matriz de Probabilidade × Impacto
│   └── fluxo-processo.png                 # Fluxo de validação automática
│
└── prompts/                               # Prompts utilizados com a IA
    ├── prompt-identificacao.md            # Prompt da Etapa 1
    ├── prompt-analise.md                  # Prompt da Etapa 2
    └── prompt-respostas.md                # Prompt da Etapa 3
```

---

## 🛠️ Tecnologias e Ferramentas Utilizadas

| Ferramenta                     | Finalidade                                                   |
|--------------------------------|--------------------------------------------------------------|
| **IA Generativa (LLM)**       | Apoio na elaboração de artefatos de gerenciamento de riscos  |
| **Markdown**                   | Formatação dos documentos                                     |
| **GitHub**                     | Versionamento e organização do repositório                    |
| **ERP Tasy (referência)**      | Contexto técnico do cenário do projeto                       |
| **PMBOK 7ª Edição**           | Framework de gerenciamento de projetos                        |
| **ISO 31000:2018**             | Norma de referência para gestão de riscos                    |

---

## 📑 Explicação de Cada Documento

### 📁 riscos/

| Documento                        | Conteúdo                                                                                                                     |
|----------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| `identificacao.md`               | Registro de 10 riscos identificados com ID, nome, descrição, contexto de ocorrência, categoria e consequência.               |
| `analise.md`                     | Análise qualitativa de cada risco (probabilidade, impacto, justificativa) e Matriz de Probabilidade × Impacto.               |
| `respostas.md`                   | Estratégias de resposta (evitar, mitigar, transferir, aceitar) para cada risco, com recomendação justificada e ações práticas.|

### 📁 comunicacao/

| Documento                        | Conteúdo                                                                                                                     |
|----------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| `status-stakeholders.md`         | Comunicado executivo destinado à Diretoria Hospitalar, em linguagem acessível para público não técnico.                      |

### 📁 docs/

| Documento                        | Conteúdo                                                                                                                     |
|----------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| `consideracoes-ia.md`            | Documentação de como a IA foi utilizada, limitações encontradas, validações necessárias e cuidados em projetos hospitalares.  |

### 📁 imagens/

| Arquivo                | Conteúdo                                                                |
|------------------------|-------------------------------------------------------------------------|
| `matriz-riscos.png`    | Representação visual da Matriz Qualitativa de Probabilidade × Impacto   |
| `fluxo-processo.png`   | Fluxograma da validação automática de repasse na exclusão de itens      |

### 📁 prompts/

| Arquivo                     | Conteúdo                                                                        |
|-----------------------------|---------------------------------------------------------------------------------|
| `prompt-identificacao.md`   | Prompt utilizado para solicitar à IA a identificação dos riscos (Etapa 1)        |
| `prompt-analise.md`         | Prompt utilizado para solicitar à IA a análise qualitativa (Etapa 2)             |
| `prompt-respostas.md`       | Prompt utilizado para solicitar à IA as estratégias de resposta (Etapa 3)        |

---

## 🤖 Como a Inteligência Artificial Foi Utilizada

A IA Generativa foi utilizada como **ferramenta de coprodução** em todas as etapas do projeto:

1. **Identificação de Riscos** — A IA gerou riscos específicos ao cenário a partir do contexto técnico fornecido, evitando riscos genéricos.

2. **Análise Qualitativa** — A IA classificou probabilidade e impacto com justificativas técnicas, gerando a matriz qualitativa.

3. **Estratégias de Resposta** — A IA elaborou quatro estratégias por risco e recomendou a mais adequada com ações práticas.

4. **Comunicação com Stakeholders** — A IA traduziu conteúdo técnico para linguagem executiva, adequada à Diretoria Hospitalar.

5. **Documentação e Organização** — A IA gerou a estrutura do repositório, README e documentação de uso da IA.

### ⚠️ Cuidados Adotados

- Todo conteúdo foi **revisado e validado** por profissional com conhecimento do contexto;
- **Nenhum dado real** de pacientes, médicos ou operadoras foi fornecido à IA;
- Os **prompts foram documentados** para garantir transparência e reprodutibilidade;
- As **limitações da IA** foram explicitamente documentadas no artefato correspondente.

> Para detalhes completos sobre o uso da IA, consulte [`docs/consideracoes-ia.md`](docs/consideracoes-ia.md).

---

## 👥 Stakeholders do Projeto

| Stakeholder                | Papel no Projeto                                              |
|----------------------------|---------------------------------------------------------------|
| Auditor Hospitalar         | Usuário final da funcionalidade                               |
| Analista de Sistemas       | Responsável técnico pela especificação e desenvolvimento      |
| Equipe de TI               | Suporte à implementação e infraestrutura                      |
| Faturamento Hospitalar     | Área impactada pelas inconsistências financeiras              |
| Gestor Financeiro          | Responsável pela validação das regras de repasse              |
| Coordenação da Auditoria   | Gestão do processo de auditoria e treinamento dos auditores   |
| Diretoria Hospitalar       | Patrocinador executivo do projeto                             |

---

## 📊 Visão Geral dos Riscos

| ID     | Risco                                             | Prob.  | Impacto | Criticidade  | Estratégia    |
|--------|---------------------------------------------------|--------|---------|--------------|---------------|
| RSK-01 | Mapeamento incompleto das regras de repasse       | Alta   | Alto    | 🔴 Crítica    | Evitar        |
| RSK-02 | Incompatibilidade com customizações do ERP        | Média  | Alto    | 🟠 Elevada    | Mitigar       |
| RSK-03 | Degradação de performance                         | Média  | Médio   | 🟡 Moderada   | Mitigar       |
| RSK-04 | Resistência dos auditores                         | Média  | Médio   | 🟡 Moderada   | Mitigar       |
| RSK-05 | Mensagem de bloqueio inadequada                   | Baixa  | Baixo   | 🟢 Baixa      | Evitar        |
| RSK-06 | Ausência de ambiente de homologação               | Média  | Alto    | 🟠 Elevada    | Mitigar       |
| RSK-07 | Priorização concorrente                           | Alta   | Médio   | 🟠 Elevada    | Mitigar       |
| RSK-08 | Falha na rastreabilidade                          | Baixa  | Alto    | 🟡 Moderada   | Evitar        |
| RSK-09 | Bloqueios incorretos (falso positivo)             | Média  | Alto    | 🟠 Elevada    | Evitar        |
| RSK-10 | Falta de alinhamento de escopo                    | Média  | Médio   | 🟡 Moderada   | Evitar        |

---

## 📚 Referências

- PMI. *Um Guia do Conhecimento em Gerenciamento de Projetos (Guia PMBOK)*. 7ª Edição. Project Management Institute, 2021.
- ABNT. *NBR ISO 31000:2018 — Gestão de riscos — Diretrizes*. Associação Brasileira de Normas Técnicas, 2018.
- Philips Tasy. *Documentação técnica do ERP Tasy*.

---

## 📄 Licença

Este projeto está licenciado sob a [Licença MIT](LICENSE).

---

*Projeto acadêmico desenvolvido com apoio de Inteligência Artificial Generativa para a disciplina de Gerenciamento de Projetos de Software.*
