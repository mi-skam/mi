---
created: 2024-04-11 2024-04-15T21:58:49+02:00
modified: 2024-09-03T18:03:49+02:00
---
To also type-check javascript files on a file basis

```js
// @ts-check
```

per project:

`deno.json`:

```json
{
  "compilerOptions": {
    "checkJs": true
  }
}
```

---

[[Best-Practices]]
