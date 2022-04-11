# Spread syntax


## 功能

逐一展開。

> Spread syntax (...) allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

   [Spread syntax (...)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

## 範例


### 展開字串1


```js
let stones = "aAAA";
let stonesArray = {...stones};

console.log(stonesArray);
/*
{
  0: "a",
  1: "A",
  2: "A",
  3: "A"
}
*/
```


### 展開字串2


```js
let stones = "aAAA";
let jewels = "aA";
let count = 0;

[...stones].forEach( s =>{
	[...jewels].forEach( j =>{
		if(s === j){
    	++count;
    }
	}
		
	)
}	
)

console.log(count);
// 4
```
 

### 插入變數


```js
let numberStore = [0, 1, 2];
let newNumber = 12;
numberStore = [...numberStore, newNumber];
console.log(numberStore);

// [0, 1, 2, 12]
```