# for...in


## 功能


逐一提取鍵（key）。

> The for...in statement iterates over all enumerable properties of an object that are keyed by strings (ignoring ones keyed by Symbols), including inherited enumerable properties.

> Note: for...in should not be used to iterate over an Array where the index order is important.

  [for...in](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in)


## 範例


### 一

```js
const object = { a: 1, b: 2, c: 3 };

for (const property in object) {
  console.log(`${property}: ${object[property]}`);
}

// expected output:
// "a: 1"
// "b: 2"
// "c: 3"
```


### 二

```js
let jewels = { A:true, B:true, C:true };
let stones = "ABc";
let count = 0;

for (const s of stones) {
  if(s in jewels){
	++count;
	}
}

console.log(count);

// 2
```