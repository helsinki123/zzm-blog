- ...展开运算符是浅拷贝
- 使用 defineProperty 方法，我们可以向对象添加新属性，或修改现有属性。 
- 当我们使用 defineProperty 方法向对象添加属性时，默认情况下它们是不可枚举的。所以使用Object.keys无法遍历出刚创建的key
***
- 删除操作符返回一个布尔值：成功删除时为 true，否则返回 false。 但是，使用const 或 let 关键字声明的变量不能使用 delete 运算符删除。var可以删除
- 导入的模块是只读的：您不能修改导入的模块。
- 参数是按值传递的，除非它们的值是一个对象，否则它们是通过引用传递的。 birthYear 是按值传递的，因为它是一个字符串，而不是一个对象。 当我们按值传递参数时，会创建该值的副本 
```
function getInfo(member, year) {
  member.name = 'Lydia';
  year = '1998';
}

const person = { name: 'Sarah' };
const birthYear = '1997';

getInfo(person, birthYear);

console.log(person, birthYear);
//{ name: "Lydia" }, "1997"
```
# js所有假值
```
There are 8 falsy values:

undefined
null
NaN
false
'' (empty string)
0
-0
0n (BigInt(0))
```
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
