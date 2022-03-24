# 类型断言有两种形式。 其一是“尖括号”语法：
```
let someValue: any = "this is a string";
let strLength: number = (<string>someValue).length;
另一个为as语法：
let someValue: any = "this is a string";
let strLength: number = (someValue as string).length;
```
