# 函数声明会被提升，但是函数表达式却不会被提升。 
foo(); // 不是 ReferenceError, 而是 TypeError!
var foo = function bar() { // ... };
# 总结：变量的赋值操作会执行两个动作，首先编译器会在当前作用域中声明一个变量（如 果之前没有声明过），然后在运行时引擎会在作用域中查找该变量，如果能够找到就会对 它赋值
# for in for of
```
let obj = {
    name:'zzm',
    age:12
}
let arr = [5,6,7]
for (const iterator of arr) {
    console.log(iterator);
}
for (const key in obj) {
    if (Object.hasOwnProperty.call(obj, key)) {
        const element = obj[key];
        console.log(element);
    }
}
```

因为能够被for...of正常遍历的，都需要实现一个遍历器Iterator。而数组、字符串、Set、Map结构，
早就内置好了Iterator（迭代器），它们的原型中都有一个Symbol.iterator方法，而Object对象并没有实现这个接口，使得它无法被for...of遍历
# 数组
```
数组也是对象，所以虽然每个下标都是整数，你仍然可以给数组添加属性：
var myArray = [ "foo", 42, "bar" ]; myArray.baz = "baz"; myArray.length; // 3 myArray.baz; // "baz" 可以看到虽然添加了命名属性（无论是通过 . 语法还是 [] 语法），数组的 length 值并未发 生变化。 你完全可以把数组当作一个普通的键 / 值对象来使用，并且不添加任何数值索引，但是这 并不是一个好主意。数组和普通的对象都根据其对应的行为和用途进行了优化，所以最好 只用对象来存储键 / 值对，只用数组来存储数值下标 / 值对。 注意：如果你试图向数组添加一个属性，但是属性名“看起来”像一个数字，那它会变成 一个数值下标（因此会修改数组的内容而不是添加一个属性）：
var myArray = [ "foo", 42, "bar" ]; myArray["3"] = "baz"; myArray.length; // 4 myArray[3]; // "baz"
```
# 箭头函数的词法作用域：
```
function foo() { // 返回一个箭头函数
return (a) => { //this 继承自 foo() console.log( this.a ); }; }
var obj1 = { a:2 };
var obj2 = { a:3
100 ｜ 第 2 章 };
var bar = foo.call( obj1 ); bar.call( obj2 ); // 2, 不是 3 ！ foo() 内部创建的箭头函数会捕获调用时 foo() 的 this。
由于 foo() 的 this 绑定到 obj1， bar（引用箭头函数）的 this 也会绑定到 obj1，箭头函数的绑定无法被修改。（new 也不 行！）
```
# 判断this 
```
现在我们可以根据优先级来判断函数在某个调用位置应用的是哪条规则。可以按照下面的 顺序来进行判断： 
1. 函数是否在 new 中调用（new 绑定）？如果是的话 this 绑定的是新创建的对象。 var bar = new foo() 
2. 函数是否通过 call、apply（显式绑定）或者硬绑定调用？如果是的话，this 绑定的是 指定的对象。 var bar = foo.call(obj2) 
3. 函数是否在某个上下文对象中调用（隐式绑定）？如果是的话，this 绑定的是那个上 下文对象。 var bar = obj1.foo() 
4. 如果都不是的话，使用默认绑定。如果在严格模式下，就绑定到 undefined，否则绑定到 全局对象。 var bar = foo() 就是这样。对于正常的函数调用来说，理解了这些知识你就可以明白 this 的绑定原理了
```
# this绑定的四种机制
1. 隐式绑定-window
2. 显示绑定-{}
3. 强绑定-call
4. new绑定-new foo()
# 隐式绑定
```
function foo() { console.log( this.a ); }
var obj = { a: 2, foo: foo };obj.foo(); //2
```
# global和window 
- global比较虚，属于js祖先对象，不能访问。
- 浏览器中的全局对象就是window
[参考](https://blog.csdn.net/chenchunlin526/article/details/78908592)
# this是window !之前一直理解错了 
```
var a = "global"
function foo(){
    console.log(this);
    console.log(this.a);
}
function bar(){
    let a = 1
    foo()
}
bar()
```
# 要弄清楚调用位置和调用栈
# this默认绑定
```
如果使用严格模式（strict mode），那么全局对象将无法使用默认绑定，因此 this 会绑定 到 undefined：
function foo() { "use strict"; console.log( this.a ); }
var a = 2; foo(); // TypeError: this is undefined 这里有一个微妙但是非常重要的细节，
虽然 this 的绑定规则完全取决于调用位置，
但是只 有 foo() 运行在非 strict mode 下时，默认绑定才能绑定到全局对象
```
# this是在运行时绑定
![this](https://github.com/helsinki123/zzm-blog/blob/main/docs/%E4%BD%A0%E4%B8%8D%E7%9F%A5%E9%81%93%E7%9A%84javascript/this.png?raw=true)
