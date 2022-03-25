# namespace和module
[参考](https://juejin.cn/post/6844903921031479309)
- namespace在官方也已经不是推荐的最佳实践了, 官方已经把模块替换为es6模块的格式了, 
- 只是namespace这个概念还在保留, 现在也就是declare全局变量的时候可能会用到namespace的关键字
- 本文的内容了解即可, 实际应用比较少.
# 元组类型 
```
let tup1:[number, string, boolean] = [1, 'a', true];
console.log(tup1);  
number, string, boolean必须一一对应
```
# 联合类型 |
```
var val:string|number 
val = 12 
console.log("数字为 "+ val) 
val = "Runoob" 
console.log("字符串为 " + val)
使用非string，number 会报错
```
# type 和 interface
- 一般来说，如果不清楚什么时候用interface/type，能用 interface 实现，就用 interface , 如果不能就用 type 
[参考](https://juejin.cn/post/6844903749501059085)
# super
```
super 实际上用在两种语法中:

1. constructor 内的 super(): 执行父类的构造函数。必须至少执行一次。

2. 一般方法内的 super.method(): 执行父类的 (未必同名的) 方法。不是必需。

super.method(...) 等价于 父类的构造函数.prototype.method.call(this, ...)。
```
# ts和java语法挺像的
[参考](https://juejin.cn/post/6870843175146258445)
# 泛型
```
基本写法
function handleClick<T>(params:T):T{}
泛型继承(为泛型添加限制范围)
function handleClick<T extends {length:number}>(params:T):T{}
```
# 接口使用泛型
```
class Collection<T>{
    data:T[]=[]//类里面的属性要给初始值
    public push(...items:T[]){
        this.data.push(...items)
    }
}
let collection = new Collection()
collection.push(1,'2')
console.log(collection.data);
```
# 断言assert 的作用
1、断言assert 是仅在Debug 版本起作用的宏，它用于检查“不应该”发生的情况；

2、以下是使用断言的几个原则： 
```
　　 
　　（1）使用断言捕捉不应该发生的非法情况。不要混淆非法情况与错误情况之间的区别，后者是必然存在的并且是一定要作出处理的。 
　　 
　　（2）使用断言对函数的参数进行确认。 
　　 
　　（3）在编写函数时，要进行反复的考查，并且自问：“我打算做哪些假定？”一旦确定了的假定，就要使用断言对假定进行检查。 
　　 
　　（4）一般教科书都鼓励程序员们进行防错性的程序设计，但要记住这种编程风格会隐瞒错误。当进行防错性编程时，如果“不可能发生”的事情的确发生了，则要使用断言进行报警。 
```
　　ASSERT ()是一个调试程序时经常使用的宏，在程序运行时它计算括号内的表达式，如果表达式为FALSE (0), 程序将报告错误，并终止执行。如果表达式不为0，则继续执行后面的语句。这个宏通常原来判断程序中是否出现了明显非法的数据，如果出现了终止程序以免导致严重后果，同时也便于查找错误。  

ASSERT只有在Debug版本中才有效，如果编译为Release版本则被忽略。

# 类型断言有两种形式。 
```
其一是“尖括号”语法：
let someValue: any = "this is a string";
let strLength: number = (<string>someValue).length;
另一个为as语法：
let someValue: any = "this is a string";
let strLength: number = (someValue as string).length;
```
