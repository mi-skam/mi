---
in: "[[1 - Inbox/JS and TS Fullstack Development]]"
created: 2024-06-10
tags:
  - code/js
  - best-practices
languages: javascript
---
We use [JSON stringify](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) and its inverse [JSON.parse()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) to create a _deep clone_ of a JavaScript Object.
 
```js
const foo = {
  foundation: "Mozilla",
  model: "box",
  week: 45,
  transport: "car",
  month: 7,
};

const fooJSON = JSON.stringify(foo);
const fooCopy = JSON.parse(fooJSON);

console.log(fooCopy);
```
