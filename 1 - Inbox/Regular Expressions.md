---
created: 2024-06-12
tags:
  - x
modified: 2024-09-03T18:03:36+02:00
---
## Capture Groups 

Rename a file like _script.js_ to _script.dev.js_

```js
// \.(js|ts|jsx|tsx) => matches .js (or .ts ...) => $1
// replaces .js with ${postfix}$1
// .dev$1 => .dev.js => public/js/script.dev.js

function renameFile(file, postfix) {
  return file.replace(/(\.(js|ts|jsx|tsx))/i, `.${postfix}$1`);
}
console.log(renameFile("public/js/script.js", "dev"));
```