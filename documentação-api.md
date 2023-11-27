## Modelo de Documentação de API

### Contexto 
A documentação de API é o documento que reúne as principais especificações técnicas que você precis saber para realizar uma requisição e obter uma resposta sucesso em uma integração com APIs. No caso de APIs construídas a partir de uma arquitetura REST, é comum que se use a especificação OpenAPI para documentar os endpoints, semelhante ao que se encontra no modelo de API do [Swagger](https://petstore.swagger.io/#/), principal ferramenta do mercado usada para documentar APIs deste tipo. 

## Exemplo de documentação 

# API Bytebank

Use as APIs da Bytebank para se integrar ao checkout da sua loja e processe pagamentos. 

## Informações gerais
* Registre-se no Portal de Desenvolvedores da Bytebank para ser autorizado a executar as APIs do banco. 
* Sempre configure Token de Acesso no header de Autorização de todas as suas chamadas, tal como o exemplo:

```
curl -H ‘Authorization: Bearer <ENV_ACCESS_TOKEN>’  \
https://api.mercadopago.com/V1/payments
````

## Pagamentos

É o recurso que permite você criar, obter ou gerenciar os pagamentos da sua loja virtual integrada aos serviços financeiros da Bytebank.  

### URL base para as chamadas 
```
https://api.mercadopago.com/v1/payments
```

### Endpoints

| Método | Nome do endpoint | Descrição |
|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| POST | Criar pagamento | Cria um novo pagamento a ser processado |
| GET | Buscar em pagamentos | Pesquisa por todos os pagamentos realizados | 
| GET | Obter pagamento | Consulte todas as informações de um pagamento através de um ```id``` .| 
| PUT | Atualizar pagamentos | Atualiza alguma informação de um determinado pagamento | 
