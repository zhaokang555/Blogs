#Precondition:

现在有一个页面，里面HTML代码为：

```html
<div class="css">
     <p class="rain">测试1</p>
</div>
<div class="rain">
     <p>测试2</p>
</div>
```

#如果我们使用find()方法：

```javascript
var $find = $("div").find(".rain");
alert( $find.text() ) ;
```

将会输出：

```
测试1
```

#如果使用filter()方法：

```javascript
var $filter = $("div").filter(".rain");
alert( $filter.text() );
```

将会输出：

```
测试2
```

#总结：

find()会在div元素内 寻找 class为rain 的元素。
而filter()则是筛选div的class为rain的元素。
一个是对它的子集操作，一个是对自身集合元素筛选。

另外find()其实还可以用选择器表示:

```javascript
var $select = $("div .rain");
```

转自：[jQuery基础---filter()和find()](http://www.cnblogs.com/qiantuwuliang/archive/2009/10/18/1585682.html)
