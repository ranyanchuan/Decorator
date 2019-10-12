
##### 装饰器类的装饰 

```js
// 装饰器可以用来装饰整个类。
@testable
class MyTestableClass {
  // ...
}

function testable(target) {
  target.isTestable = true;
}

MyTestableClass.isTestable // true
```
```js
@decorator
class A {}

// 等同于

class A {}
A = decorator(A) || A;
```


```js
// 装饰器添加参数
function testable(isTestable) {
  return function(target) {
    target.isTestable = isTestable;
  }
}

@testable(true)
class MyTestableClass {}
MyTestableClass.isTestable // true

@testable(false)
class MyClass {}
MyClass.isTestable // false
```


