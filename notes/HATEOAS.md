# HATEOAS - Hypermedia as the Engine of Application State 
Builds upon REST as an additional constraint

The restrictions imposed by HATEOAS decouple client and server, allowing them to evolve indepedently

## What does it do
Media Types for representations and link relations are standardized

Every response from the server, lets the client know what possible links can be called, so no out-of-band information is needed in order to interact with the resource

Example Banking:

```json
GET /accounts/12345 HTTP/1.1
Host: bank.example.com
```

Resp:

```json
HTTP/1.1 200 OK

{
    "account": {
        "account_number": 12345,
        "balance": {
            "currency": "usd",
            "value": 100.00
        },
        "links": {
            "deposits": "/accounts/12345/deposits",
            "withdrawals": "/accounts/12345/withdrawals",
            "transfers": "/accounts/12345/transfers",
            "close-requests": "/accounts/12345/close-requests"
        }
    }
}
```

The links may change as business logic requires it, for example an overdrawn account would not even present the client with opportunity to withdraw


The Client does not need to understand every media type or communication mechanism offered by the server due to these restrictions, instead it can pick them up on demand as they are needed
