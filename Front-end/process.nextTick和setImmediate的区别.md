#process.nextTick和setImmediate的区别

- `process.nextTick`方法可以在当前"执行栈"的尾部----下一次Event Loop（主线程读取"任务队列"）之前----触发回调函数。

- `setImmediate`方法则是在当前"任务队列"的头部添加事件，也就是说，它指定的任务总是在下一次Event Loop时执行，这与`setTimeout(fn, 0)`很像。

