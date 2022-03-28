```
function getAge(...args) {
  console.log(typeof args);//object
}

getAge(21);
```
# 经典
```
foo(); // 报错TypeError ReferenceError：引用错误，即在作用域中没有找到该变量
bar(); // 报错ReferenceError TypeError：类型错误，在作用域中已经声明变量并且找到，但是没有找到确切定义或者引用
var foo = function bar() {
    // ...
};
```
