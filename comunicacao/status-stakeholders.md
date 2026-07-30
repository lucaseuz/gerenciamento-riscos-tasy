# Etapa 4 — Comunicação para Stakeholders

## Comunicado à Diretoria Hospitalar

---

**COMUNICADO EXECUTIVO — PROJETO DE MELHORIA**

**Assunto:** Automatização da Validação de Exclusão de Itens com Repasse Financeiro na Auditoria de Contas

**Data:** Julho de 2026

**De:** Equipe do Projeto — Analista de Sistemas / Coordenação da Auditoria

**Para:** Diretoria Hospitalar

---

### 1. Contexto

Durante o processo de auditoria das contas hospitalares, auditores realizam ajustes nos itens cobrados — incluindo procedimentos, materiais e medicamentos — antes que a conta seja enviada ao faturamento.

Alguns desses itens possuem **vínculo financeiro com repasses médicos**. Isso significa que a remuneração de profissionais médicos está diretamente associada à presença desses itens na conta.

---

### 2. Situação Atual

Atualmente, o sistema **permite que um auditor exclua um item da conta mesmo quando existe um repasse médico já registrado** para aquele item. Essa situação pode gerar:

- **Inconsistências financeiras** entre o valor faturado e o valor repassado ao médico;
- **Divergências contábeis** que dificultam o fechamento mensal;
- **Glosas por parte das operadoras**, quando há divergência entre a conta apresentada e os serviços efetivamente registrados;
- **Retrabalho** das equipes de faturamento e auditoria para identificar e corrigir as divergências;
- **Perda de rastreabilidade**, dificultando a investigação de eventuais questionamentos.

Este cenário representa um **risco operacional e financeiro** que pode ser eliminado com uma melhoria simples e objetiva no sistema.

---

### 3. Projeto Proposto

O projeto consiste em desenvolver uma **validação automática** no sistema de auditoria que:

1. **Verifica**, no momento da exclusão, se o item possui repasse financeiro vinculado;
2. **Bloqueia** a exclusão quando houver repasse ativo;
3. **Informa** ao auditor o motivo do bloqueio com uma mensagem clara;
4. **Registra** a tentativa para fins de auditoria e rastreabilidade.

> **Importante:** O projeto trata exclusivamente de uma melhoria de validação. Não serão alterados os processos de faturamento, as regras de cálculo de repasse ou o fluxo de trabalho dos auditores.

---

### 4. Principais Riscos Identificados

A equipe do projeto realizou uma análise de riscos seguindo boas práticas de gerenciamento de projetos. Os principais riscos identificados são:

| Risco                                                    | Nível       | Ação em Andamento                                                |
|----------------------------------------------------------|-------------|------------------------------------------------------------------|
| Regras de repasse não completamente mapeadas             | Crítico     | Levantamento detalhado com o Financeiro e TI em andamento        |
| Possível conflito com customizações existentes no sistema | Elevado     | Solução técnica desacoplada para minimizar interferência         |
| Bloqueios indevidos em repasses já cancelados            | Elevado     | Mapeamento completo dos status de repasse com o setor Financeiro |
| Concorrência com outros projetos da equipe de TI        | Elevado     | Projeto dimensionado para execução em até 2 semanas              |

A análise completa dos riscos, incluindo estratégias de resposta, está documentada nos artefatos do projeto.

---

### 5. Ações em Andamento

- ✅ Levantamento das regras de repasse com o setor financeiro;
- ✅ Análise técnica das tabelas e customizações do sistema;
- ✅ Definição dos cenários de teste com a Coordenação da Auditoria;
- 🔄 Desenvolvimento da validação automatizada;
- 🔄 Preparação do material de treinamento para auditores;
- ⏳ Testes em ambiente de homologação;
- ⏳ Implantação em produção (mediante aprovação).

---

### 6. Benefícios Esperados

A implementação desta melhoria trará os seguintes benefícios:

| Benefício                             | Descrição                                                                                    |
|---------------------------------------|----------------------------------------------------------------------------------------------|
| **Segurança financeira**              | Eliminação do risco de exclusão de itens com repasse, preservando a integridade dos valores   |
| **Redução de retrabalho**             | Menos correções manuais por parte da auditoria e do faturamento                               |
| **Redução de glosas**                 | Menor incidência de divergências que resultam em glosas pelas operadoras                      |
| **Rastreabilidade**                   | Registro automático de todas as tentativas de exclusão bloqueadas                              |
| **Conformidade**                      | Maior aderência aos requisitos de auditoria interna e externa                                  |
| **Eficiência operacional**            | Auditores informados em tempo real sobre restrições, sem necessidade de consultas manuais     |

---

### 7. Próximos Passos

| Etapa                                    | Previsão         | Responsável              |
|------------------------------------------|------------------|--------------------------|
| Conclusão do mapeamento de repasses      | Semana 1         | Gestor Financeiro + TI   |
| Desenvolvimento da validação             | Semanas 2-3      | Analista de Sistemas     |
| Testes em homologação                    | Semana 3         | Equipe de TI + Auditoria |
| Treinamento dos auditores               | Semana 4         | Coordenação da Auditoria |
| Implantação em produção                 | Semana 4 (após aprovação) | Equipe de TI      |

---

### 8. Solicitação

Solicitamos o **patrocínio e a priorização** deste projeto pela Diretoria, considerando:

- O **risco financeiro** que a situação atual representa;
- O **baixo custo de implementação** (melhoria pontual, sem necessidade de aquisição de software);
- O **alto retorno** em segurança, rastreabilidade e redução de retrabalho.

A equipe está à disposição para esclarecimentos adicionais e para apresentação presencial do projeto, caso necessário.

---

**Equipe do Projeto**

Analista de Sistemas | Coordenação da Auditoria | Equipe de TI

---

*Comunicado elaborado com apoio de Inteligência Artificial Generativa e revisado para adequação ao contexto institucional.*
