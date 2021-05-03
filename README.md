# Test case for wds + esbuild + lit 2.x

The import `lit/directives/class-map.js` should resolve to `node_modules/lit/directives/class-map.js`

```ts
// src/MyElement.ts
import { classMap } from 'lit/directives/class-map.js';
```

Instead, it resolves to `node_modules/lit/directives/class-map.ts` and triggers the following error in the browser:

```
GET http://localhost:8000/node_modules/lit/directives/class-map.ts net::ERR_ABORTED 404 (Not Found)
```

## How to run

1. Run `npm start`
1. Visit `localhost:8000` with Dev Tools open
1. Inspect network tab on the resources
1. Notice how `lit/directives/class-map.js` gets resolved using `.ts` instead of `.js`
