# for...of 


## 功能


逐一展開，像 spread syntax(`...`) 。

> The for...of statement creates a loop iterating over iterable objects, including: built-in String, Array, array-like objects (e.g., arguments or NodeList), TypedArray, Map, Set, and user-defined iterables. 

  [for...of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)


## 範例


```js
const iterable = [10, 20, 30];

for (let value of iterable) {
  value += 1;
  console.log(value);
}

// 11
// 21
// 31

console.log("---");
console.log(iterable); // [10, 20, 30]
```