
#require函数实现原理

```javascript
// require函数实现原理：
function require(modulePath) {

    var regExp = /\w+$/g;
    var moduleName = regExp.exec(modulePath);

    var module = {
        id: moduleName,
        exports: {}
    };

    var load = function (exports, module) {
        // ============
        // 读取的文件内容：
        // ...
        // ...
        // ============

        return module.exports;
    };

    return load(module.exports, module);   
}
```