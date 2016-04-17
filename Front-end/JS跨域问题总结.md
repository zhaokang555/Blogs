#JS跨域问题总结

详情见原博客：[详解js跨域问题](https://segmentfault.com/a/1190000000718840)

概念：只要协议、域名、端口有任何一个不同，都被当作是不同的域。

##跨域资源共享（CORS）

CORS（Cross-Origin Resource Sharing）跨域资源共享，定义了必须在访问跨域资源时，浏览器与服务器应该如何沟通。CORS背后的基本思想就是使用自定义的HTTP头部让浏览器与服务器进行沟通，从而决定请求或响应是应该成功还是失败。

服务器端对于CORS的支持，主要就是通过设置Access-Control-Allow-Origin来进行的。如果浏览器检测到相应的设置，就可以允许Ajax进行跨域的访问。

##JSONP的缺点

JSONP的缺点是：它只支持GET请求而不支持POST等其它类型的HTTP请求；它只支持跨域HTTP请求这种情况，不能解决不同域的两个页面之间如何进行JavaScript调用的问题。

##CORS和JSONP对比

CORS与JSONP相比，无疑更为先进、方便和可靠。

1. JSONP只能实现GET请求，而CORS支持所有类型的HTTP请求。 
2. 使用CORS，开发者可以使用普通的XMLHttpRequest发起请求和获得数据，比起JSONP 有更好的错误处理。
3. JSONP主要被老的浏览器支持，它们往往不支持CORS，而绝大多数现代浏览器都已经支持了CORS。

##通过修改document.domain来跨子域

浏览器都有一个同源策略，其限制之一就是第一种方法中我们说的不能通过ajax的方法去请求不同源中的文档。 它的第二个限制是浏览器中不同域的框架之间是不能进行js的交互操作的。

不同的frame之间是可以获取window对象的，但却无法获取相应的属性和方法。

这个时候，document.domain就可以派上用场了，我们只要把`http://www.example.com/a.html` 和 `http://example.com/b.html`这两个页面的`document.domain`都设成相同的域名就可以了。但要注意的是，`document.domain`的设置是有限制的，我们只能把`document.domain`设置成自身或更高一级的父域，且主域必须相同。(这里必须设置为`example.com`)

##使用window.name来进行跨域

window对象有个name属性，该属性有个特征：即在一个窗口(window)的生命周期内,窗口载入的所有的页面都是共享一个window.name的，每个页面对window.name都有读写的权限，window.name是持久存在一个窗口载入过的所有页面中的

##使用HTML5的window.postMessage方法跨域

window.postMessage(message,targetOrigin) 方法是html5新引进的特性，可以使用它来向其它的window对象发送消息，无论这个window对象是属于同源或不同源，目前IE8+、FireFox、Chrome、Opera等浏览器都已经支持window.postMessage方法。

