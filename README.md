
# typescript-http-client

## Install

```bash
npm i https://github.com/tikiram/typescript-http-client.git
```

```bash
yarn add typescript-http-client@https://github.com/tikiram/typescript-http-client.git
```

## Example

```js
import {
    ErrorHandlerMiddleware,
    HTTPClient,
    HTTPMethod,
    LoggerMiddleware,
} from 'typescript-http-client';

async function something() {
    const client = new HTTPClient(
        'https://pokeapi.co/api/v2',
        [new LoggerMiddleware(), new ErrorHandlerMiddleware()]
    );

    const response = await client.request<Pokemon>(HTTPMethod.Get, '/pokemon/ditto');

    console.log(response)    
}

```