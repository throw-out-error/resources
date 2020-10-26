
## Typescript

### Key Value Storage

If you want to set up a key value store in typescript, this is one way to do it.
First, install the following packages:

- [quick.db](https://github.com/lorencerri/quick.db) for the key value storage
- [typed-path](https://www.npmjs.com/package/typed-path) for typed key compatibility

You can use any map-like store that you want, but in this case I'm going to use quick.db which is a wrapper for sqlite.

Next, you'll want to create an interface for your configuration/database:

```typescript
export interface Config {
    user: {
        name: string;
        age: number;
    };
}
```

Lastly, you should define a variable that will be your typed path reference.
```typescript
/** Typed Config Paths */
import { typedPath as tp } from "typed-path";

export const tc = tp<Config>();
```

Now you can create the store:
```typescript
import db from "quick.db";

export const store = new db.table("config");
```

and get a value:

```typescript:
console.log(store.get(tc.user.age.$path);
```
