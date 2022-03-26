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
