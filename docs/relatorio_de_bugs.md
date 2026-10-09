# Relatório de Bugs – ServeRest

ServeRest 3.2.2, executado localmente (`npx serverest -p 3000`), testes manuais por API, em 09/10/2026.

## Resumo
- **10 defeitos** encontrados em 30 casos de teste executados.
- Por severidade: **2 Alta**, **5 Média**, **3 Baixa**.
- Cada defeito está registrado como *issue* neste repositório, com passos, resultado esperado, resultado obtido e evidência.

## Critério de severidade
| Severidade | Quando uso |
|---|---|
| Crítica | Sistema inutilizável ou perda de dados |
| Alta | Falha de segurança ou regra de negócio central quebrada, sem alternativa |
| Média | Regra de validação ou de negócio quebrada, com alternativa |
| Baixa | Inconsistência pequena, sem risco para o usuário |

## Lista de defeitos
| ID | Severidade | Área | Título |
|---|---|---|---|
| [BUG-01](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/1) | Alta | Segurança / Login | Token JWT retornado no login contém a senha do usuário em texto puro |
| [BUG-02](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/2) | Alta | Segurança / Usuários | GET /usuarios, sem autenticação, devolve a senha de todos os usuários em texto puro |
| [BUG-03](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/3) | Média | Validação / Usuários | Cadastro de usuário aceita nome formado apenas por espaços em branco |
| [BUG-04](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/4) | Média | Validação / Usuários | Cadastro de usuário aceita senha de apenas 1 caractere |
| [BUG-05](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/5) | Baixa | Validação / Usuários | Campo nome do usuário não tem limite de tamanho (aceita 5000 caracteres) |
| [BUG-06](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/6) | Média | Regra de negócio / Usuários | É possível cadastrar o mesmo e-mail duas vezes mudando apenas as letras maiúsculas e minúsculas |
| [BUG-07](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/7) | Média | Validação / Produtos | Cadastro de produto aceita nome formado apenas por espaços em branco |
| [BUG-08](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/8) | Baixa | Validação / Produtos | Cadastro de produto aceita preço enviado como texto ("10") e converte sem avisar |
| [BUG-09](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/9) | Baixa | Validação / Produtos | Cadastro de produto não limita o valor máximo do preço (aceita 1.000.000.000.000.000) |
| [BUG-10](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/10) | Média | Regra de negócio / Produtos | É possível cadastrar dois produtos com o mesmo nome mudando apenas maiúsculas e minúsculas |

## Observação
O ServeRest é uma API educacional, criada para estudo de testes, e algumas das falhas acima podem ser intencionais. O objetivo aqui é exercitar o ciclo completo do trabalho de QA: planejar, executar, encontrar e registrar defeitos de forma clara e reproduzível.
