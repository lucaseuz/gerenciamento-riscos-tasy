# Prompt — Identificação dos Riscos

## Contexto fornecido à IA

O prompt abaixo foi utilizado para solicitar à IA Generativa a identificação dos riscos do projeto. O contexto do cenário, escopo e stakeholders foi fornecido como entrada para garantir que os riscos gerados fossem específicos e relevantes.

---

## Prompt Utilizado

```
Você atuará como um Especialista em Gerenciamento de Projetos de Software, 
certificado em PMBOK, ISO 31000 e Engenharia de Software, com experiência em 
gerenciamento de riscos e projetos hospitalares.

CONTEXTO DO PROJETO:
- Projeto de melhoria em ERP hospitalar (Tasy);
- Objetivo: validar automaticamente se um item da conta hospitalar possui repasse 
  médico vinculado antes de permitir sua exclusão pelo auditor;
- Se houver repasse, a exclusão deve ser bloqueada com mensagem explicativa;
- A tentativa deve ser registrada para auditoria.

ESCOPO:
- Validação automática de repasse vinculado;
- Bloqueio da exclusão;
- Mensagem explicativa;
- Registro de log da tentativa;
- NÃO inclui: desenvolvimento de telas, alteração de faturamento, alteração de 
  regras de repasse, implantação em produção.

STAKEHOLDERS:
- Auditor Hospitalar, Analista de Sistemas, Equipe de TI, Faturamento Hospitalar, 
  Gestor Financeiro, Coordenação da Auditoria, Diretoria Hospitalar.

TAREFA:
Identifique de 8 a 10 riscos relevantes para este projeto. Para cada risco, 
apresente em formato de tabela:
- ID
- Nome do risco
- Descrição detalhada
- Contexto de ocorrência
- Categoria (Técnico, Operacional, Organizacional ou Negócio)
- Consequência caso ocorra

REGRAS:
- Não invente riscos genéricos;
- Considere riscos técnicos, operacionais, organizacionais e de negócio;
- Todos os riscos devem ser coerentes com o cenário descrito;
- Utilize linguagem técnica, porém objetiva.
```

---

## Observações

- O prompt foi iterado para refinar a especificidade dos riscos gerados.
- Riscos genéricos como "falta de orçamento" ou "saída de membros da equipe" foram descartados por não serem relevantes para uma melhoria pontual de software.
- O contexto técnico do ERP Tasy (customizações, triggers, tabelas de repasse) foi adicionado para direcionar a IA a riscos mais realistas.

---

*Prompt documentado para fins de transparência e reprodutibilidade, conforme boas práticas de uso de IA Generativa em projetos acadêmicos.*
