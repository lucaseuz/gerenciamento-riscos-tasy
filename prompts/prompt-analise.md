# Prompt — Análise Qualitativa dos Riscos

## Contexto fornecido à IA

O prompt abaixo foi utilizado para solicitar à IA a análise qualitativa dos riscos previamente identificados na Etapa 1.

---

## Prompt Utilizado

```
Com base nos 10 riscos identificados na etapa anterior (RSK-01 a RSK-10), 
realize a análise qualitativa de cada um.

Para cada risco, apresente:
- Descrição
- Possíveis impactos
- Fatores que influenciam sua ocorrência
- Probabilidade (Baixa, Média ou Alta)
- Impacto (Baixo, Médio ou Alto)
- Justificativa detalhada para a classificação

Ao final, gere uma Matriz Qualitativa de Probabilidade × Impacto (3×3), 
posicionando cada risco na célula correspondente.

CRITÉRIOS:
- Baixa: evento improvável nas condições normais do projeto.
- Média: evento possível, considerando o histórico e as condições do cenário.
- Alta: evento esperado ou muito provável.

- Baixo: impacto limitado, absorvido sem alteração significativa.
- Médio: impacto moderado, exigindo ações corretivas.
- Alto: impacto severo, comprometendo entregas críticas ou integridade financeira.

REGRAS:
- As classificações devem ser coerentes com o cenário hospitalar;
- Justifique cada classificação de forma técnica;
- A matriz deve conter os IDs dos riscos posicionados nas células corretas;
- Inclua legenda de criticidade (Crítica, Elevada, Moderada, Baixa).
```

---

## Observações

- A IA foi orientada a usar critérios explícitos de classificação para evitar subjetividade excessiva.
- As justificativas foram revisadas para garantir aderência ao contexto específico do projeto.
- A matriz foi validada manualmente, verificando a coerência entre a classificação individual e o posicionamento na matriz.

---

*Prompt documentado para fins de transparência e reprodutibilidade.*
