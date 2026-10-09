# Plano de Teste – ServeRest (exploratório)

## 1. Objetivo
Verificar se a API do ServeRest valida corretamente os dados enviados e protege as informações dos usuários, com foco em **cadastro de usuários, login, produtos e carrinho**, e registrar os defeitos encontrados.

## 2. Sistema sob teste
- **ServeRest 3.2.2**, executado localmente (`npx serverest -p 3000`).
- Documentação de referência: Swagger do próprio ServeRest.

## 3. Escopo
**Dentro do escopo**
- Usuários: cadastro, edição, consulta e exclusão.
- Login e token de acesso.
- Produtos: cadastro, consulta e regras de validação.
- Carrinho: inclusão, regras de estoque e cancelamento da compra.

**Fora do escopo**
- Testes de desempenho e carga.
- Testes da interface web (já cobertos no projeto de automação).
- Testes de acessibilidade e compatibilidade de navegadores.

## 4. Estratégia e técnicas
- **Teste exploratório por API**, com requisições feitas manualmente (curl) e por scripts de apoio.
- **Partição de equivalência:** dados válidos e inválidos para cada campo.
- **Análise de valor-limite:** preço zero e negativo, quantidade zero e negativa, textos muito longos.
- **Testes negativos:** campos vazios, tipos errados, token ausente ou adulterado.
- **Testes de segurança básicos:** conteúdo do token e exposição de dados sem autenticação.
- Cada falha é **reproduzida duas vezes** antes de virar bug, para ter certeza de que não foi acaso.

## 5. Critérios
- **Entrada:** ServeRest no ar e respondendo; massa de dados criada pelo próprio teste.
- **Saída:** todos os casos planejados executados e todos os defeitos registrados como *issue*.

## 6. Ambiente e ferramentas
curl, Python (requests) para os scripts de apoio, GitHub Issues para o registro dos bugs.

## 7. Riscos
- O ServeRest é uma API educacional, e algumas falhas podem ser intencionais. Mesmo assim, todas foram registradas, porque o objetivo é exercitar o processo completo de QA.
- A versão local pode ser diferente da versão pública (serverest.dev).

## 8. Entregáveis
- [Casos de teste executados](casos_de_teste_executados.md)
- [Relatório de bugs](relatorio_de_bugs.md)
- 10 *issues* abertas neste repositório
