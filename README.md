## Falar sobre o framework Serverless (esqueci nos slides sorry :( )

https://serverless.com/

## Tuto de como criar sua primeira Lambda em Javascript.

### 1. Instalar Node

### 2. Criar um diretório

### 3. Executar

```
npm init
npm install -g serverless
npm install --save-dev serverless

mkdir src
```

#### Crie o código da sua função

```
code src/index.js
```

Contendo:

```
'use strict';

module.exports.handler = async event => {
  return {
    statusCode: 200,
    body: JSON.stringify(
      {
        message: 'Parabéns seu primeiro endpoint serverless!',
        // input: event,
      },
      null,
      2
    ),
  };
};

```

#### Crie seu arquivo de infra

```
code serverless.yml
```

Contendo:

```
service: meetup-douglas
provider:
  name: aws
  runtime: nodejs12.x
  region: sa-east-1
functions:
  hello:
    handler: src/index.handler
```

#### Adicione um evento

```
    events:
      - http: GET hello

```

### Execute local

Instale um plugin para funcionar local

```
npm i --save-dev serverless-offline

```

adicione

```
plugins:
  - serverless-offline
```

```
sls offline
```

### De deploy

```
sls deploy
```
