# Plano de Teste e Relatório de Bugs – ServeRest

Projeto de **QA manual e exploratório** em que testei a API do [ServeRest](https://github.com/ServeRest/ServeRest): planejei os testes, executei 30 casos e registrei **10 defeitos** como *issues*, cada um com passos, resultado esperado, resultado obtido, severidade e evidência.

Este projeto complementa o [QA Automation – ServeRest](https://github.com/EsterNevess/qa-automation-serverest), em que automatizei testes de API e Web com pytest e Playwright.

## O que tem aqui
| O quê | Onde |
|---|---|
| Plano de teste (escopo, estratégia, técnicas, riscos) | [docs/plano_de_teste.md](docs/plano_de_teste.md) |
| 30 casos executados, com resultado | [docs/casos_de_teste_executados.md](docs/casos_de_teste_executados.md) |
| Relatório de bugs (resumo e severidade) | [docs/relatorio_de_bugs.md](docs/relatorio_de_bugs.md) |
| Cada bug com a evidência completa | [aba Issues](../../issues) (BUG-01 a BUG-10) |
| Modelo de relatório de bug | [.github/ISSUE_TEMPLATE](.github/ISSUE_TEMPLATE/bug_report.md) |

## Resultado
- **30** casos executados: **20 passaram** e **10 falharam**.
- **10 bugs**: 2 de severidade Alta (segurança), 5 Média e 3 Baixa.

| Bug | Severidade | Resumo |
|---|---|---|
| BUG-01 | Alta | Token JWT do login contém a senha em texto puro |
| BUG-02 | Alta | `GET /usuarios` sem autenticação devolve as senhas |
| BUG-03 | Média | Usuário aceita nome só com espaços |
| BUG-04 | Média | Usuário aceita senha de 1 caractere |
| BUG-05 | Baixa | Nome do usuário sem limite de tamanho |
| BUG-06 | Média | E-mail duplicado aceito mudando maiúsculas e minúsculas |
| BUG-07 | Média | Produto aceita nome só com espaços |
| BUG-08 | Baixa | Preço enviado como texto é aceito e convertido |
| BUG-09 | Baixa | Preço sem valor máximo |
| BUG-10 | Média | Produto duplicado aceito mudando maiúsculas e minúsculas |

## Como reproduzir
```bash
npx serverest -p 3000      # sobe a API em http://localhost:3000
```
Depois é só repetir os passos de cada bug (cada issue traz os passos e a requisição usada).

## Observação
O ServeRest é uma API criada para **estudo de testes**, e algumas falhas podem ser propositais. O objetivo aqui é mostrar o trabalho de QA de ponta a ponta: planejar, executar, encontrar e relatar defeitos de forma clara e reproduzível.

## Autora
**Ester Neves** – QA Júnior · [LinkedIn](https://www.linkedin.com/in/esterneves/) · [GitHub](https://github.com/EsterNevess)
