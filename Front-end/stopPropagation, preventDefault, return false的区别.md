#stopPropagation, preventDefault, return false的区别

##`e.stopPropagation()`阻止事件冒泡或者捕获

因为事件可以在各层级的节点中传递, 不管是冒泡还是捕获, 有时我们希望事件在特定节点执行完之后不再传递, 可以使用事件对象的 stopPropagation() 方法.

例如：阻止表单提交。

##`e.preventDefault()`阻止浏览器默认动作

执行监听函数在前, 触发浏览器默认动作在后.

例如：用户点击链接后，阻止在本页面打开链接。

##`return false`等效于同时调用`e.preventDefault()`和`e.stopPropagation()`

```javascript
if (ret===false){
　　event.preventDefault();
　　event.stopPropagation();
}
```

---

详情可以看：[stopPropagation, preventDefault 和 return false 的区别](http://www.neoease.com/stoppropagation-and-preventdefault-and-return-false/)
