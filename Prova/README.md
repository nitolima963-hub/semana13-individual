# AC4 - Integração Contínua em QA (CI/CD)

**Disciplina:** Automação de Testes  
**Professor:** Raphael Botelho  
**Trio:** preencher os nomes e RAs  
**Semana:** 13

## Objetivo

Automatizar testes de API usando uma coleção Postman, Newman e GitHub Actions. A cada `push`, o GitHub executa os testes automaticamente.

## Arquivos

- `colecao.json`: coleção Postman v2.1 com 3 requisições.
- `.github/workflows/main.yml`: pipeline no GitHub Actions.

## Testes previstos

| Requisição | Método | Resultado esperado |
|---|---|---|
| Buscar usuário 1 | GET `/users/1` | HTTP 200 e ID igual a 1 |
| Buscar usuário inexistente | GET `/users/999999` | HTTP 404 |
| Criar um post | POST `/posts` | HTTP 201 e título correto |

API utilizada: <https://jsonplaceholder.typicode.com>.

## Execução local (opcional)

É necessário ter Node.js e npm instalados. Na pasta do repositório:

```bash
npm install -g newman
newman run colecao.json
```

## GitHub Actions

1. Crie um repositório público chamado `semana13-trioX` (substitua X pelo número do trio).
2. Envie os arquivos desta pasta sem mudar o caminho `.github/workflows/main.yml`.
3. Abra a aba **Actions** e selecione **Testes de API**.
4. Abra a execução, o job **testes-api** e o passo **Rodar a coleção de testes**.
5. Confirme no log a quantidade de requisições, de assertions e de falhas.

## Missão 4: quebrar e consertar

1. Na coleção, mude temporariamente `pm.response.to.have.status(200)` no teste da requisição 01 para `pm.response.to.have.status(201)`.
2. Faça commit; depois verifique a execução vermelha (falha esperada).
3. Restaure `status(200)`, faça novo commit e confirme a execução verde.
4. **Crie um teste adicional do próprio trio** (sugestão abaixo) e faça um terceiro commit. O teste abaixo é um exemplo para adaptar, não foi inserido na coleção porque a missão pede que o trio o escreva.

Exemplo de teste adicional para a requisição 01:

```javascript
pm.test("Nome do usuário não está vazio", function () {
    pm.expect(pm.response.json().name).to.not.be.empty;
});
```

## Evidências para registrar

- Repositório público exibindo os arquivos.
- Aba Actions com primeira execução aprovada.
- Log do Newman com os testes passando.
- Execução com falha proposital e mensagem explicando a falha.
- Execução corrigida.
- Execução com o teste novo do trio.

> **Observação:** prints e resultados só podem ser registrados como realizados depois de fazer os commits e executar o pipeline no GitHub.
