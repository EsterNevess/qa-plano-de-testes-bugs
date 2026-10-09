# Casos de Teste Executados

Ambiente: ServeRest 3.2.2 rodando localmente. Execução manual por API (curl e scripts de apoio) em 09/10/2026.

**Resultado:** 30 casos executados, 20 passaram e 10 falharam (cada falha gerou um bug).

| ID | Módulo | Cenário | Esperado | Obtido | Resultado | Bug / Obs. |
|---|---|---|---|---|---|---|
| CT-01 | Usuários | Cadastrar usuário com nome só de espaços | 400 (nome em branco) | 201 – cadastrou | ❌ Falhou | [BUG-03](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/3) |
| CT-02 | Usuários | Cadastrar usuário com senha de 1 caractere | 400 (senha fraca) | 201 – cadastrou | ❌ Falhou | [BUG-04](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/4) |
| CT-03 | Usuários | Cadastrar usuário com nome de 5000 caracteres | 400 (limite de tamanho) | 201 – cadastrou | ❌ Falhou | [BUG-05](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/5) |
| CT-04 | Usuários | Cadastrar o mesmo e-mail em MAIÚSCULAS | 400 (e-mail já usado) | 201 – duplicou | ❌ Falhou | [BUG-06](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/6) |
| CT-05 | Usuários | Cadastrar com `administrador` inválido ("talvez") | 400 | 400 – "administrador deve ser 'true' ou 'false'" | ✅ Passou |  |
| CT-06 | Usuários | Cadastrar com e-mail com espaço | 400 | 400 – "email deve ser um email válido" | ✅ Passou |  |
| CT-07 | Usuários | Cadastrar com e-mail sem domínio completo (a@b) | 400 | 400 – "email deve ser um email válido" | ✅ Passou |  |
| CT-08 | Usuários | Cadastrar com campo extra no corpo | 400 | 400 – "extra não é permitido" | ✅ Passou |  |
| CT-09 | Usuários | Cadastrar com JSON malformado | 400 | 400 – mensagem sobre aspas (texto pouco claro) | ✅ Passou | Observação: mensagem de erro confusa |
| CT-10 | Usuários | Editar usuário usando o e-mail de outro usuário | 400 (e-mail já usado) | 400 – "Este email já está sendo usado" | ✅ Passou |  |
| CT-11 | Segurança | Conteúdo do token JWT retornado no login | Sem dados sensíveis | Payload com a senha em texto puro | ❌ Falhou | [BUG-01](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/1) |
| CT-12 | Segurança | Listar usuários sem autenticação | 401/403 ou sem campo de senha | 200 – com `password` em texto puro | ❌ Falhou | [BUG-02](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/2) |
| CT-13 | Login | Login com senha enviada como número | 400 | 400 – "password deve ser uma string" | ✅ Passou |  |
| CT-14 | Login | Login com e-mail com espaços nas pontas | 400 | 400 – "email deve ser um email válido" | ✅ Passou |  |
| CT-15 | Autorização | Cadastrar produto com token sem o prefixo Bearer | 401 | 401 – token ausente ou inválido | ✅ Passou |  |
| CT-16 | Autorização | Cadastrar produto com token adulterado | 401 | 401 – token ausente ou inválido | ✅ Passou |  |
| CT-17 | Produtos | Cadastrar produto com nome só de espaços | 400 (nome em branco) | 201 – cadastrou | ❌ Falhou | [BUG-07](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/7) |
| CT-18 | Produtos | Cadastrar produto com preço como texto ("10") | 400 | 201 – converteu para número | ❌ Falhou | [BUG-08](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/8) |
| CT-19 | Produtos | Cadastrar produto com preço de 1.000.000.000.000.000 | 400 (limite máximo) | 201 – cadastrou | ❌ Falhou | [BUG-09](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/9) |
| CT-20 | Produtos | Cadastrar o mesmo nome de produto em MAIÚSCULAS | 400 (nome já existe) | 201 – duplicou | ❌ Falhou | [BUG-10](https://github.com/EsterNevess/qa-plano-de-testes-bugs/issues/10) |
| CT-21 | Produtos | Cadastrar produto com preço decimal (10.5) | 400 | 400 – "preco deve ser um inteiro" | ✅ Passou |  |
| CT-22 | Produtos | Cadastrar produto com quantidade negativa | 400 | 400 – "quantidade deve ser maior ou igual a 0" | ✅ Passou |  |
| CT-23 | Produtos | Cadastrar produto com descrição vazia | 400 | 400 – "descricao não pode ficar em branco" | ✅ Passou |  |
| CT-24 | Produtos | Filtrar produtos com preço negativo | 400 | 400 – "preco deve ser um número positivo" | ✅ Passou |  |
| CT-25 | Carrinho | Adicionar ao carrinho mais itens do que o estoque | 400 | 400 – "Produto não possui quantidade suficiente" | ✅ Passou |  |
| CT-26 | Carrinho | Adicionar ao carrinho quantidade zero ou negativa | 400 | 400 – "deve ser um número positivo" | ✅ Passou |  |
| CT-27 | Carrinho | Adicionar o mesmo produto duas vezes no carrinho | 400 | 400 – "Não é permitido possuir produto duplicado" | ✅ Passou |  |
| CT-28 | Carrinho | Excluir produto que está em um carrinho | 400 | 400 – "Não é permitido excluir produto que faz parte de carrinho" | ✅ Passou |  |
| CT-29 | Carrinho | Excluir usuário que tem carrinho | 400 | 400 – "Não é permitido excluir usuário com carrinho cadastrado" | ✅ Passou |  |
| CT-30 | Carrinho | Cancelar compra e conferir o estoque | 200 e estoque reabastecido (3 → 1 → 3) | 200 – estoque voltou a 3 | ✅ Passou |  |
