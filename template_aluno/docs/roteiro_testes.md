 # Roteiro de Testes — BiblioTech

## CT-01

### Requisito

RF01

### Título

Usuário ativo, sem pendência e sem empréstimos ativos pode realizar empréstimo.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar se um usuário ativo, sem pendências e sem empréstimos ativos pode realizar um novo empréstimo.

### Pré-condições

Sistema disponível e usuário cadastrado como ativo.

### Dados de teste

- usuario_ativo = True
- possui_pendencia = False
- emprestimos_ativos = 0

### Passos

1. Informar que o usuário está ativo.
2. Informar que o usuário não possui pendências.
3. Informar que o usuário possui 0 empréstimos ativos.
4. Executar `pode_emprestar(True, False, 0)`.

### Resultado esperado

`True` — o empréstimo deve ser permitido.

### Resultado obtido

`True` — o empréstimo foi permitido.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [x] Particionamento de equivalência
- [ ] Análise de valor-limite
- [x] Cenário positivo
- [ ] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_usuario_valido_pode_emprestar` passou no pytest.

### Observações

-


---

## CT-02

### Requisito

RF01

### Título

Usuário inativo não pode realizar empréstimo.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar se um usuário inativo tem seu empréstimo rejeitado.

### Pré-condições

Sistema disponível e usuário cadastrado como inativo.

### Dados de teste

- usuario_ativo = False
- possui_pendencia = False
- emprestimos_ativos = 0

### Passos

1. Informar que o usuário está inativo.
2. Informar que o usuário não possui pendências.
3. Informar que o usuário possui 0 empréstimos ativos.
4. Executar `pode_emprestar(False, False, 0)`.

### Resultado esperado

`False` — o empréstimo deve ser rejeitado.

### Resultado obtido

`False` — o empréstimo foi rejeitado.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [x] Particionamento de equivalência
- [ ] Análise de valor-limite
- [ ] Cenário positivo
- [x] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_usuario_inativo_nao_pode_emprestar` passou no pytest.

### Observações

-


---

## CT-03

### Requisito

RF01

### Título

Usuário com pendência não pode realizar empréstimo.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar se um usuário com pendência tem seu empréstimo rejeitado.

### Pré-condições

Sistema disponível, usuário ativo e sem empréstimos ativos.

### Dados de teste

- usuario_ativo = True
- possui_pendencia = True
- emprestimos_ativos = 0

### Passos

1. Informar que o usuário está ativo.
2. Informar que o usuário possui pendência.
3. Informar que o usuário possui 0 empréstimos ativos.
4. Executar `pode_emprestar(True, True, 0)`.

### Resultado esperado

`False` — o empréstimo deve ser rejeitado.

### Resultado obtido

`False` — o empréstimo foi rejeitado.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [x] Particionamento de equivalência
- [ ] Análise de valor-limite
- [ ] Cenário positivo
- [x] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_usuario_com_pendencia_nao_pode_emprestar` passou no pytest.

### Observações

-


---

## CT-04

### Requisito

RF01

### Título

Usuário com 3 empréstimos ativos não pode realizar outro empréstimo.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar o comportamento do sistema no limite máximo de empréstimos ativos definido pelo RF01.

### Pré-condições

Sistema disponível, usuário ativo e sem pendências.

### Dados de teste

- usuario_ativo = True
- possui_pendencia = False
- emprestimos_ativos = 3

### Passos

1. Informar que o usuário está ativo.
2. Informar que o usuário não possui pendências.
3. Informar que o usuário possui 3 empréstimos ativos.
4. Executar `pode_emprestar(True, False, 3)`.

### Resultado esperado

`False` — o empréstimo deve ser rejeitado, pois o requisito determina que o usuário deve possuir menos de 3 empréstimos ativos.

### Resultado obtido

`True` — o empréstimo foi permitido, contrariando o resultado esperado.

### Status

- [ ] PASSOU
- [x] FALHOU

### Técnica utilizada

- [ ] Particionamento de equivalência
- [x] Análise de valor-limite
- [ ] Cenário positivo
- [x] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

O teste automatizado `test_usuario_no_limite_nao_pode_emprestar` falhou:

`assert True is False`

Resultado do pytest: 1 teste falhou e 17 passaram.

### Observações

O caso de teste revelou um defeito na implementação do RF01.


---

## CT-05

### Requisito

RF02

### Título

Não cobrar multa quando não há atraso.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar se não é aplicada multa quando o empréstimo não possui atraso.

### Pré-condições

Sistema disponível.

### Dados de teste

- dias_atraso = 0

### Passos

1. Informar 0 dias de atraso.
2. Executar `calcular_multa(0)`.

### Resultado esperado

`0.0` — multa de R$ 0,00.

### Resultado obtido

`0.0` — multa de R$ 0,00.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [ ] Particionamento de equivalência
- [x] Análise de valor-limite
- [x] Cenário positivo
- [ ] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_multa_sem_atraso` passou no pytest.

### Observações

-


---

## CT-06

### Requisito

RF02

### Título

Calcular multa para 3 dias de atraso.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar o cálculo da multa dentro da primeira faixa de atraso.

### Pré-condições

Sistema disponível.

### Dados de teste

- dias_atraso = 3

### Passos

1. Informar 3 dias de atraso.
2. Executar `calcular_multa(3)`.

### Resultado esperado

`6.0` — multa de R$ 6,00.

### Resultado obtido

`6.0` — multa de R$ 6,00.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [x] Particionamento de equivalência
- [ ] Análise de valor-limite
- [x] Cenário positivo
- [ ] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_multa_tres_dias` passou no pytest.

### Observações

-


---

## CT-07

### Requisito

RF02

### Título

Calcular multa no limite de 7 dias de atraso.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar o cálculo da multa no limite superior da primeira faixa de atraso.

### Pré-condições

Sistema disponível.

### Dados de teste

- dias_atraso = 7

### Passos

1. Informar 7 dias de atraso.
2. Executar `calcular_multa(7)`.

### Resultado esperado

`14.0` — multa de R$ 14,00.

### Resultado obtido

`14.0` — multa de R$ 14,00.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [ ] Particionamento de equivalência
- [x] Análise de valor-limite
- [x] Cenário positivo
- [ ] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_multa_sete_dias` passou no pytest.

### Observações

-


---

## CT-08

### Requisito

RF02

### Título

Calcular multa no início da segunda faixa de atraso.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar o cálculo da multa quando o atraso ultrapassa 7 dias.

### Pré-condições

Sistema disponível.

### Dados de teste

- dias_atraso = 8

### Passos

1. Informar 8 dias de atraso.
2. Executar `calcular_multa(8)`.

### Resultado esperado

`17.0` — multa de R$ 17,00.

### Resultado obtido

`17.0` — multa de R$ 17,00.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [ ] Particionamento de equivalência
- [x] Análise de valor-limite
- [x] Cenário positivo
- [ ] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_multa_oito_dias` passou no pytest.

### Observações

-


---

## CT-09

### Requisito

RF03

### Título

Classificar usuário sem atraso.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar a classificação de um usuário sem atraso.

### Pré-condições

Sistema disponível.

### Dados de teste

- dias_atraso = 0

### Passos

1. Informar 0 dias de atraso.
2. Executar `classificar_atraso(0)`.

### Resultado esperado

`sem atraso`.

### Resultado obtido

`sem atraso`.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [ ] Particionamento de equivalência
- [x] Análise de valor-limite
- [x] Cenário positivo
- [ ] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_classificacao_sem_atraso` passou no pytest.

### Observações

-


---

## CT-10

### Requisito

RF03

### Título

Classificar atraso leve.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar a classificação de atrasos entre 1 e 7 dias.

### Pré-condições

Sistema disponível.

### Dados de teste

- dias_atraso = 5

### Passos

1. Informar 5 dias de atraso.
2. Executar `classificar_atraso(5)`.

### Resultado esperado

`atraso leve`.

### Resultado obtido

`atraso leve`.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [x] Particionamento de equivalência
- [ ] Análise de valor-limite
- [x] Cenário positivo
- [ ] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_classificacao_atraso_leve` passou no pytest.

### Observações

-


---

## CT-11

### Requisito

RF03

### Título

Classificar atraso moderado.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar a classificação de atrasos entre 8 e 30 dias.

### Pré-condições

Sistema disponível.

### Dados de teste

- dias_atraso = 15

### Passos

1. Informar 15 dias de atraso.
2. Executar `classificar_atraso(15)`.

### Resultado esperado

`atraso moderado`.

### Resultado obtido

`atraso moderado`.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [x] Particionamento de equivalência
- [ ] Análise de valor-limite
- [x] Cenário positivo
- [ ] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_classificacao_atraso_moderado` passou no pytest.

### Observações

-


---

## CT-12

### Requisito

RF03

### Título

Classificar atraso grave.

### Tipo

- [x] Caixa Preta
- [ ] Caixa Branca

### Prioridade

- [x] Alta
- [ ] Média
- [ ] Baixa

### Objetivo

Verificar a classificação de atrasos superiores a 30 dias.

### Pré-condições

Sistema disponível.

### Dados de teste

- dias_atraso = 45

### Passos

1. Informar 45 dias de atraso.
2. Executar `classificar_atraso(45)`.

### Resultado esperado

`atraso grave`.

### Resultado obtido

`atraso grave`.

### Status

- [x] PASSOU
- [ ] FALHOU

### Técnica utilizada

- [x] Particionamento de equivalência
- [ ] Análise de valor-limite
- [x] Cenário positivo
- [ ] Cenário negativo
- [ ] Caminho estrutural
- [ ] Outro

### Evidência

Teste automatizado `test_classificacao_atraso_grave` passou no pytest.

### Observações

-


---

# Registro de Defeito

## BUG-01

### Requisito associado

RF01 — Permissão para empréstimo.

### Caso de teste

CT-04 — Usuário com 3 empréstimos ativos não pode realizar outro empréstimo.

### Entrada utilizada

- usuario_ativo = True
- possui_pendencia = False
- emprestimos_ativos = 3

### Resultado esperado

`False` — o empréstimo deveria ser rejeitado, pois o RF01 determina que o usuário deve possuir menos de 3 empréstimos ativos.

### Resultado obtido

`True` — o empréstimo foi permitido.

### Prioridade sugerida

- [x] Alta
- [ ] Média
- [ ] Baixa

### Evidência

Execução do pytest:

`FAILED tests/test_bibliotech.py::test_usuario_no_limite_nao_pode_emprestar`

Erro apresentado:

`assert True is False`

Resultado geral:

`1 failed, 17 passed`

A cobertura obtida foi de 100% de linhas e 100% de branches.

### Justificativa

O comportamento observado diverge do requisito RF01. O teste de valor-limite com exatamente 3 empréstimos ativos revelou que o sistema permite um novo empréstimo quando deveria rejeitá-lo.

O defeito está relacionado à condição utilizada na implementação para verificar o limite de empréstimos.

### Observações

O defeito foi apenas identificado e registrado. Nenhuma alteração foi realizada no código de produção.
