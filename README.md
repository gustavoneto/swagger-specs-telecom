__Especificações técnicas de conteúdo dos swaggers Algar Telecom__

# Description

__Todo swagger e API devem ter:__

* Descrições nos recursos
* Descrições nas operações de cada recurso
* Descrições nos parâmetros do payload (request e response) quando aplicável.
* Descrições nos query parâmeters (quando aplicável)

# Definitions

Para uma melhor apresentação do swagger e permitir facilidades de edição quando necessário adotamos a boa prática de
sempre seprar as definições de objetos (principalmente request e responses) no parâmetro definitions da [swagger Spec](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#definitionsObject).

__Exemplo:__

```
definitions:
  hold:
    type: object
    required:
      - statusConta
      - idAssinatura
    properties:
      statusConta:
        type: string
        enum:
          - Credito suspenso
          - Ativo
        example: "Credito suspenso"
      idAssinatura:
        type: string
        format: int32
        example: '1000002'
```

# Especial tags:

Para fins de aprovação todo swagger deve conter as seguintes tags customizadas:

__x-destination__

Para todas as operações em seu devido endpoint de destino após as transformações.

```
paths: 
  /customer:
    post:
      x-destination: "http://127.0.0.1:9001"
      description: Register new resource
      
```

__x-restrictedFields__

Para todas as operações que possam ter campos sensíveis às políticas de privacidade 

```
paths: 
  /customer:
    post:
      x-destination: "http://127.0.0.1:9001"
      x-restictedFields: ['address.cep', 'address.number', 'address.street', 'documentNumber']
      description: Register new resource
      
```

# Support

If you have any questions or suggestions please contact me: `renatosdesign@gmail.com` `renato.silva@eticasolucoes.com.br`
