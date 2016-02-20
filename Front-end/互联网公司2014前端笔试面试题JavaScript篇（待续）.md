#互联网公司2014前端笔试面试题JavaScript篇（待续）

网上找的题目，自己做了下

``` javascript
/**************************** 
 *1. 用js实现随机选取10–100之间的10个数字，存入一个数组，并排序
 ****************************/

function f1(arr) {
    for (var i = 0; i < 10; i++) {
        var randomNum = Math.floor(Math.random() * 91 + 10); // 得到10~100之间的整数
        arr.push(randomNum);
    }
    arr.sort(function (a, b) {return  a - b});
    return arr;
}
// ======test======
var arr = [];
console.log(f1(arr));



/****************************
 * 2. 有这样一个URL：http://item.taobao.com/item.htm?a=1&b=2&c=&d=xxx&e，
 * 请写一段JS程序提取URL中的各个GET参数(参数名和参数个数不确定)，
 * 将其按key-value形式返回到一个json结构中，
 * 如{a:'1', b:'2', c:'', d:'xxx', e:undefined}。
 ****************************/

function f2(url) {
    var json = {};
    var regExp = /[\?\&](\w{1,})(={0,1})(\w{0,})/g;

    do {
        arr = regExp.exec(url);
        // console.log(arr); // arr = [完整的字符串, key, 等号或'', value或'']

        if (arr) {
            //  arr[2] === ''时, value = undefined
            //  arr[2] === '='时, value = arr[3]
            var key = arr[1];
            var value = undefined;

            if (arr[2] === '=')
                value = arr[3];

            json[key] = value;
        }
    } while (arr);

    return json;
}
// ======test======
var url = 'http://item.taobao.com/item.htm?a=1&b=2&c=&d=xxx&e';
console.log(f2(url));




/****************************
 * 3. 我们要给每个log方法添加一个(app)前缀，
 * 比如'hello world!'->'(app)hello world!'
 ****************************/

console.oldLog = console.log; // 保存原函数

console.log = function (str) {
    console.oldLog('(app)' + str);
};

// ======test======
console.log('zhaokang');
```