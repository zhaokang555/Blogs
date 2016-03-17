```javascript
'use strict';

function f(x) {
    // do something...    
}

var readline = require('readline');

//创建readline接口实例
var rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

// ======= 方法一 =========
rl.question("input something:",function(str){
    console.log(f(str));

    // 不加close，则不会结束
    rl.close();
});
// =======================
// 或者这样：
// ======= 方法二 =========
// console.log('input something:');
// rl.on('line', function(line){
    
//     console.log(f(line));

//     // 不加close，则不会结束
//     rl.close();
// });
// ======================

rl.on('close', function() {
    process.exit(0);
});
```