#Node.js的module.exports

##使用方式：

```javascript
// filename: hello.js
function greet() {/*......*/}

// 有下面这两种写法：
// 1.
module.exports = greet;
// 2.
module.exports = {
    greet:greet
}
```

它们的调用方式是不一样的

第一种是这样调用：
```javascript
var greet = require('./hello');
greet(s);
```

第二种是这样调用：
```javascript
var hello = require('./hello');
hello.greet(s);
```

总结：第二种更好。

##注意事项：

```javascript
var module = {
    id: 'hello',
    exports: {}
};

//load()函数最终返回module.exports：
var load = function (exports, module) {
    // hello.js的文件内容
    ...
    // load函数返回:
    return module.exports;
};

var exported = load(module.exports, module);
```

这个可以改变原始exports对象:

```javascript
exports.foo = function () { return 'foo'; };
```

而

```javascript
exports = function () { return 'foo'; };
```

只是改变了形参exports的引用(/指向)，而实际的module.exports还是指向空对象{}

