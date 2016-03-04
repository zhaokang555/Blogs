new操作符具体干了什么呢?

##Preconditions:

```javascript
function PrimaryStudent() {
    this.grade = 1;
}

PrimaryStudent.prototype.sayHi = function(){
    alert('hi');
}
```

```javascript
var p = new PrimaryStudent();
```

相当于

```javascript
var p  = {};
p.__proto__ = PrimaryStudent.prototype;
PrimaryStudent.call(obj); 
```