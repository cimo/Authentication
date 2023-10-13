# Authentication

Authentication middleware. Light, fast and secure.

## Publish

1. npm run build
2. npm login --auth-type=legacy
3. npm publish --auth-type=legacy --access public

## Installation

1. Link for npm package -> https://www.npmjs.com/package/@cimo/authentication

## Server - Example with "NodeJs Express"

-   Server.ts

```
...

import { Ca } from "@cimo/authentication";

...

Ca.setCookieName("test_authentication");

app.use(CookieParser());

...

app.get("/login", (_request: Express.Request, response: Express.Response) => {
    const token = Ca.generateCookie();

    response.json({ stdout: token });
});

app.get("/profile", Ca.authenticationMiddleware, (_request: Express.Request, response: Express.Response) => {
    response.json({ stdout: "test authentication." });
});

...

```
