```
function* Gen1() {
  yield 2;
  yield 3;
}
function* Gen2() {
  yield 1;
  yield* Gen1();
  yield 4;
}
var g2 = Gen2();
console.log(g2.next().value); // 1
console.log(g2.next().value); // 2
console.log(g2.next().value); // 3
console.log(g2.next().value); // 4
- 从上面几个例子可以看出，yield 与 yield* 的区别在于：yield 只是返回右值，
- 而 yield* 则将函数委托（delegate）到另一个生成器（ Generator）或可迭代的对象（如字符串、数组和类数组 arguments，以及 ES6 中的 Map、Set 等）。
```
- 要访问const let定义的变量才会形成暂时性死区
```
const randomValue = 21;

function getInfo() {
	console.log(typeof randomValue);//number
    const a = "Lydia Hallie";
}

getInfo();
***
const randomValue = 21;

function getInfo() {
	console.log(typeof randomValue);//报错 refference error (应为有const randomValue，所以不会出函数外面找randomValue)
    const randomValue = "Lydia Hallie";
}

getInfo();
```
- NaN是number类型
```
const person = {
  name: 'Lydia',
  age: 21,
};

const changeAge = (x = { ...person }) => (x.age += 1);
const changeAgeAndName = (x = { ...person }) => {
  x.age += 1;
  x.name = 'Sarah';
};

changeAge(person);//传值则指向相同
changeAgeAndName();

console.log(person);//{name: "Lydia", age: 22}
```
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
