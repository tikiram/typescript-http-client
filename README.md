
# typescript-http-client

## Install

```bash
npm i https://github.com/tikiram/typescript-http-client#0.3.0
```

```bash
yarn add typescript-http-client@https://github.com/tikiram/typescript-http-client#0.2.0
```

## Example

```typescript
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

## Middleware

```typescript
class SomeLogMiddleware implements Middleware {
  constructor(private readonly seconds: number) {}

  async request(request: Request, next: NextFn): Promise<Response> {
    
    someLog(request)
    
    const response = await next(request);
    
    someLog(request)
    
    return response
  }
}
```