---
created: 2023-08-15
tags:
  - code/js/lang
---

# Objects

Objects are collections of key-value pairs.

## Creation

>[!code]- *We can use a constructor function*
> ```js
> const newObject = new Object()
> ```

>[!code]- *Object literals*
> ```js
> const newObject = { hello: "world" }
> ```

>[!code]- *Object.create()*
>The **`Object.create()`** static method creates a new object, using an existing object as the prototype of the newly created object
> ```js
> const newObjectPrototype = { hello: "world" }
> const newObject = Object.create(newObjectPrototype)
> ```

>[!code]- *Object.assign*
>The **`Object.assign()`** static method copies all properties of one or more objects to a target object.
> ```js
> const target = { a: 1, b: 2 };
> const source = { b: 4, c: 5 };
> 
> const returnedTarget = Object.assign(target, source);
> ```
## Iteration

To iterate over the keys or values of an object, you can use `for...in` loops or the `Object.keys`, `Object.values`, or `Object.entries` methods.

> [!code]- Using `for...in`:
> ```javascript
> const obj = { a: 1, b: 2, c: 3 };
> for (const key in obj) {
> console.log(key);
> }
> ```

>[!code]- Using `Object.keys` 
> ```javascript
> const obj = { a: 1, b: 2, c: 3 };
> const keys = Object.keys(obj);
> keys.forEach((key) => {
>   console.log(key);
> });
> 
> // with a for-of-loop
> for (let key of keys) {
>   console.log(key);
> }
> ```

>[!code]- Using `Object.values`
> ```javascript
> const obj = { a: 1, b: 2, c: 3 };
> const values = Object.values(obj);
> values.forEach((value) => {
>   console.log(value);
> });
> ```

>[!code]- Using `Object.entries` (for key-value pairs)
> ```javascript
> const obj = { a: 1, b: 2, c: 3 };
> const entries = Object.entries(obj);
> entries.forEach(([key, value]) => {
>   console.log(key, value);
> });
> ```