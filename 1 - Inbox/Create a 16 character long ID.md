---
created: 2024-04-12 2024-04-12T16:45:19+02:00
tags:
  - best-practices
  - code/js
languages: javascript
---
```js
const id = (Math.random() * 1e17).toString(16);
```
```dataviewjs
const id = (Math.random() * 1e17).toString(16);
dv.span(`id: ${id}`)
```