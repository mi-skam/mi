---
created: 2024-04-12 2024-04-12T17:02:46+02:00
modified: 2024-09-03T18:10:51+02:00
---

Using Generics in statically typed languages we may work with the type as a **type variable**

```ts
const identity = <T>(arg: T): T => {
  return arg;
};

console.log(identity(1));
console.log(identity(true));
```