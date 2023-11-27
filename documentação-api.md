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

#### Query parameters

{This section is optional.}

| Query parameter | Type | Required? | Description                             |
|-----------------|------|-----------|-----------------------------------------|
| {pageSize}      | int  | Optional  | {The number of items to be returned in a single request. The default value is N.} |
|                 |      |           |                                         |

#### Header parameters

{This section is optional.}

| Header parameter | Type   | Required? | Description                          |
|------------------|--------|-----------|--------------------------------------|
| {Content-Type}   | string | Required  | {Media type of the resource. Must be an object.} |
|                  |        |           |                                      |

#### Request body

{This section is optional.}

| Field  | Type   | Required? | Description                      |
|--------|--------|-----------|----------------------------------|
| {id}   | string | Required  | {Unique identifier of the user}  |
| {name} | string | Optional  | {Name of the user}               |

### Request example

```
curl -X GET \
      'https://api.mercadopago.com/v1/payments/search?sort=date_created&criteria=desc&external_reference=ID_REF&range=date_created&begin_date=NOW-30DAYS&end_date=NOW&store_id=47792478&pos_id=58930090'\
       -H 'Content-Type: application/json' \
       -H 'Authorization: Bearer TEST-5774955929875430-051913-25075633b53f75b90ba952251896e9b3-413696175' \
       
```

### Response schema

| Status code | Schema                                  | Description          |
|-------------|-----------------------------------------|----------------------|
| `2xx`       | [{ExampleDataType}](#data-model)        | {Describe the result where the request succeeds.} |
| `4xx`       | [{ExampleErrorType}](#exampleerrortype) | {Describe the result where the request fails with the specified error code.} |

### Response example

```
{Provide an example of the API response, filled with sample values.}
```
---
