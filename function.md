## Anonymous Functions(匿名函数)

#### function declarations(函数声明方式)
```
function functionName(arg0, arg1, arg2){
  //function body
}
```

#### function expression(函数表达方式)
```
var functionName = function(arg0, arg1, arg2) {
   // function body
}

```
#### anonymous function (匿名函数)
```
function (arg0, arg1, arg2) {
  // function body
}

```
上面这个匿名函数永远都不会被调用

匿名函数一般以这样的形式被调用
```
function createComparisonFunction(propertyName){
  return function(object1, object2){
    var value1 = object1[propertyName];
    var value2 = object2[propertyName];
    if (value1 <value2){
      return -1;
    } else if (value1 > value2){
      return 1;
    } else {
      return 0;
    }
  }
}
```
createComparisonFunction()函数返回一个匿名函数，这个被返回的函数
- 或者被赋予给变量
- 或者被调用

### Recursion (递归)

当函数自己调用自己就产生了递归

```
function factorial(num){
  if(num<=1){
    return 1;
  } else {
    return num * factorial(num-1);
  }
}

// f(3) = 3*f(2)
// f(3) = 3*2*f(1)
// f(3) = 3*2*1*f(0)

```
最经典的递归函数

```
var anotherFactorial = factorial;
factorial = null;
alert(anotherFactorial(4)); //error!
```
factorial()函数存储在变量anotherFactorial里，factorial变量被设置成空，当anotherFactorial()被调用的时候，会产生错误，anotherFactorial()会执行factorial(),但它不再是函数了，使用arguments.callee 能缓解这个问题。

```
function factorial(num) {
  if(num <=1){
    return 1;
  } else {
    return num * arguments.callee(num-1);
  }
}
```
> **注意：** 使用arguments.callee 代替直接使用函数名字保证了函数正常工作不管怎么接入的。
不管什么时候使用匿名函数，总是使用arguments.callee而不是函数名称，非常明智！

### Closures (闭包，此货比较难理解)

Closures 是函数从另外一个函数的作用域跟变量对接上了。
通常上一个函数里面有另外一个函数

```
function createComparisonFunction(propertyName){

    return function(object1, object2) {
        var value1 = object1[propertyName];
        var value2 = object2[propertyName];

        if (value1 < value2) {
          return -1;
        } else if (value1 > value2) {
          return 1;
        } else {
          return 0;
        }
    };

}
```
