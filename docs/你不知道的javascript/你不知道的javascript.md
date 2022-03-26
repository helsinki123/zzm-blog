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
