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

### Buscar em pagamentos

### Endpoint

```
[{GET} /{request-url}/{{path-parameter}}](https://api.mercadopago.com/v1/payments/search)]
```

### Requisição

#### Parâmetros 

| Path do parâmetro | Tipo   | Obrigatório? | Descrição                  |
|----------------|--------|-----------|------------------------------|
| ```sort```          | string | Sim  | Auxilia na ordenação de uma lista de pagamentos. |
| ```criteria```      | string | Sim  | Ordena o pagamento de maneira ascendente ou descendente. |
| ```external_reference``` | string | Sim | É uma referência externa do pagamento |
| ```range``` | string | Sim | Define o intervalo de busca pelos pagamentos. | 


### Exemplo de Requisição

```
curl -X GET \
      'https://api.mercadopago.com/v1/payments/search?sort=date_created&criteria=desc&external_reference=ID_REF&range=date_created&begin_date=NOW-30DAYS&end_date=NOW&store_id=47792478&pos_id=58930090'\
       -H 'Content-Type: application/json' \
       -H 'Authorization: Bearer TEST-5774955929875430-051913-25075633b53f75b90ba952251896e9b3-413696175' \
       
```

### Resposta

| Status code | Schema                                  | Description          |
|-------------|-----------------------------------------|----------------------|
| `200`       | [{ExampleDataType}](#data-model)        | Request suceeds. |
| `403`       | [{ExampleErrorType}](#exampleerrortype) |  | The caller is not authorized to perform this action.


### Response example

```
[
  {
    "paging": {
      "total": 17493,
      "limit": 30,
      "offset": 0
    },
    "results": [
      {
        "id": 1,
        "date_created": "2017-08-31T11:26:38.000Z",
        "date_approved": "2017-08-31T11:26:38.000Z",
        "date_last_updated": "2017-08-31T11:26:38.000Z",
        "money_release_date": "2017-09-14T11:26:38.000Z",
        "payment_method_id": "account_money",
        "payment_type_id": "credit_card",
        "status": "approved",
        "status_detail": "accredited",
        "currency_id": "BRL",
        "description": "Pago Pizza",
        "collector_id": 2,
        "payer": {
          "id": 123,
          "email": "test_user_80507629@testuser.com",
          "identification": {
            "type": "CPF",
            "number": 19119119100
          },
          "type": "customer"
        },
        "metadata": {},
        "additional_info": {},
        "transaction_amount": 250,
        "transaction_amount_refunded": 0,
        "coupon_amount": 0,
        "transaction_details": {
          "net_received_amount": 250,
          "total_paid_amount": 250,
          "overpaid_amount": 0,
          "installment_amount": 250
        },
        "installments": 1,
        "card": {}
      }
    ]
  }
]
```
---
