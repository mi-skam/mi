---
created: 2024-04-12 2024-04-12T17:02:46+02:00
languages: typescript
tags:
  - x/🚧
  - code/ts/lang
---

Using Generics in statically typed languages we may work with the type as a **type variable**

```ts
const identity = <T>(arg: T): T => {
  return arg;
};

console.log(identity(1));
console.log(identity(true));
```