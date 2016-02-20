有这样一个URL： http://item.taobao.com/item.htm?a=1&b=2&c=&d=xxx&e 

请写一段JS程序提取URL中的各个GET参数(参数名和参数个数不确定)，

将其按key-value形式返回到一个json结构中，

如{a:'1', b:'2', c:'', d:'xxx', e:undefined}。

```javascript
function f2(url) {
    var json = {};
    var regExp = /[\?\&](\w{1,})(=?)(\w{0,})/g;

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
! function () {
    var url = 'http://item.taobao.com/item.htm?a=1&b=2&c=&d=xxx&e';
    console.log(f2(url));
} ();
```