# Resources

Hello, world! This is a community site created by [Throw Out Error](https://github.com/throw-out-error) for finding all kinds of useful programming resources.

## Contents

- [Code Editors](#user-content-editors)
- [Typescript](#user-content-typescript)
    - [Key Value Storage](#user-content-key-value-storage)
- [Homelab](#user-content-homelab)

## Typescript

### Key Value Storage

If you want to set up a key value store in typescript, this is one way to do it.
First, install the following packages:

- [flash-store](https://www.npmjs.com/package/flash-store) for the key value storage
- [typed-path](https://www.npmjs.com/package/typed-path) for typed key compatibility

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
export const tc = tp<Config>();
```

Now you can create the store:
```typescript
export const store = new FlashStore(storeDir);
```

and get a value:

```typescript:
console.log(store.get(tc.user.age);
```
