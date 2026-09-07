# Matriz de Rastreabilidade — BiblioTech

## Objetivo

Relacionar requisitos aos casos de teste e verificar se todos os requisitos possuem evidências de validação.

---

| Requisito | Casos de Caixa Preta | Casos de Caixa Branca | Coberto? |
|---|---|---|---|
| RF01 | CT-01, CT-02, CT-03, CT-04, CT-05 | WB-01, WB-02, WB-03 | Sim |
| RF02 | CT-06, CT-07, CT-08, CT-09 | WB-04, WB-05 | Sim |
| RF03 | CT-10, CT-11, CT-12 | WB-06, WB-07, WB-08 | Sim |

---

# Análise

## Existe requisito sem teste?

Resposta:

Não. Os requisitos RF01, RF02 e RF03 possuem casos de teste associados e evidências de execução.

---

## Existe caso de teste sem requisito claramente associado?

Resposta:

Não. Todos os casos de teste estão associados a um dos requisitos RF01, RF02 ou RF03.

---

## Qual requisito apresentou maior risco durante a atividade?

Resposta:

RF01 — Regra de empréstimo.

---

## Justificativa

Resposta:

O RF01 apresentou o principal risco porque o caso de teste CT-04, que verifica o limite de 3 empréstimos ativos, falhou. O requisito determina que o usuário deve possuir menos de 3 empréstimos ativos, portanto, com exatamente 3 empréstimos, o resultado esperado é False.

A execução automatizada apresentou resultado True nesse cenário, caracterizando um defeito no comportamento da função `pode_emprestar`.

---

# Cobertura

## Cobertura de linhas

Resultado:

100 %

## Cobertura de branches

Resultado:

100 %

---

# Observações

- O defeito identificado em RF01 foi mantido no código de produção para fins da atividade de QA.
- O teste CT-04 falha propositalmente ao evidenciar o comportamento incorreto no limite.
- A execução apresentou 17 testes aprovados e 1 teste reprovado.
- A cobertura obtida foi de 100% de linhas e 100% de branches.
