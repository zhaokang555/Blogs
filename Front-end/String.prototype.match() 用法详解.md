String.prototype.match() 用法详解

``` javascript
var str="1 plus 2 equal 3"

// 正则表达式
console.log(str.match(/\d+/g)); // ["1", "2", "3"]
console.log(str.match(/\d+/)); // ["1", index: 0, input: "1 plus 2 equal 3"]

// 字符串
console.log(str.match(' ')); // [" ", index: 1, input: "1 plus 2 equal 3"]
```