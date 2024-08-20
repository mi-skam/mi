---
created: 2024-06-11
tags:
  - code/js/patterns
---
The **memoization** pattern is using [[1 - Inbox/JavaScript Closures]] to avoid re-executing (costly) steps like long-running functions. There are slightly nuances.

1. Embedding a worker function which can access a cache
2. Re-writing the function by re-defining the function.

> [!code]- The "calculation" function we use as an example: `fib()`
> ```js
> function fib(n) {
>   const fibNumbers = [0, 1];
>   for (let i = 0; i < n; i++) {
>     fibNumbers.push(fibNumbers[0] + fibNumbers[1]);
>     fibNumbers.shift();
>   }
>   return fibNumbers[0];
> }
>```

We use `cache` object which is in scope of `getResult()` and return it as a factory function `getResultFactory()` to the outer scope. Thus the outer `getResult()` can cache the results in `cache` .

```js
function getResultFactory() {
  const cache = {};

  const getResult = (calculate, n) => {
    let result = cache[n];
    if (typeof result === "undefined") {
      cache[n] = calculate(n);
      result = cache[n];
    } else {
      console.log("Fetching from cache...");
    }
    return result;
  };
  return getResult;
}
const getResult = getResultFactory();
```

> [!WARNING] Cache
> This general version of getResultFactory() does not cache intermediary results of e.G. recursive calls, just the final result.

To optimize for recursive functions, one would need to write a _custom_ factory function.

```js
function fibWithCache() {
  const cache = [0, 1];
  return (n) => {
    if (!(n in cache)) {
      console.log(`Computing result: ${n}`);
      cache[n] = fib(n - 1) + fib(n - 2);
    }
    return cache[n];
  };
}

const fib = fibWithCache();
```

## Re-writing functions

```js
function getResult(calculate, n) {
  const result = calculate(n);

  // we re-write the function to NOT calculate() again
  getResult = () => {
    console.log("Fetching from cache...");

    return result;
  };
  return result;
}
```