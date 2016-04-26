#jQuery中的trigger和triggerHandler区别

##trigger(event, [data])

在每一个匹配的元素上触发某类事件。
这个函数也会导致浏览器同名的默认行为的执行。比如，如果用trigger()触发一个’submit’，则同样会导致浏览器提交表单。如果要阻止这种默认行为，应返回false。
你也可以触发由bind()注册的自定义事件

```javascript
$("p").click( function (event, a, b) { 
    // 一个普通的点击事件时，a和b是undefined类型 
    // 如果用下面的语句触发，那么a指向"foo",而b指向"bar" 
} ).trigger("click", ["foo", "bar"]);
```

##triggerHandler(event, [data])

这个特别的方法将会触发指定的事件类型上所有绑定的处理函数。但不会执行浏览器默认动作.
如果你对一个focus事件执行了 .triggerHandler() ，浏览器默认动作将不会被触发，只会触发你绑定的动作:

网上的一个例子：

```javascript
<button id="old">.trigger("focus")</button>
<button id="new">.triggerHandler("focus")</button><br><br>
<input type="text" value="To Be Focused">
<script>
$(function(){
    $("#old").click(function(){
        $("input").trigger("focus");
    });
    $("#new").click(function(){
        $("input").triggerHandler("focus");
    });
    $("input").focus(function(){
        $("<span>Focused!</span>").appendTo("body").fadeOut(1000);
    });
});
</script>
```

转自：[jquery中的trigger和triggerHandler区别](http://www.skygq.com/2011/02/18/jquery%E4%B8%AD%E7%9A%84trigger%E5%92%8Ctriggerhandler%E5%8C%BA%E5%88%AB/)





