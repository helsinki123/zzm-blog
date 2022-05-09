# 5/9星期一
## linux执行CSAPP的echo客户端和服务器程序
- 下载csapp.h
- 下载csapp.c
- (参考)[https://www.cxyzjd.com/article/gebigye/50240581]
- 执行gcc -c csapp.c echoclient.c echoserveri.c //将.c编译成.o可执行文件
-  gcc -o client csapp.o echoclient.o -lpthread //生成客户端
-  gcc -o server csapp.o echoserveri.o -lpthread //生成服务端
-  首先启动server：执行./server 80.然后启动client：./client localhost 80
## gcc -o factorial main.c factorial.c //将两个从源程序编译成叫factorial的可执行文件 ./factorial 便可以执行
## C语言:宏就类似定义变量，是一条命令 #define N 100就是宏定义，N为宏名，100是宏的内容。在预处理阶段，对程序中所有出现的“宏名”，预处理器都会用宏定义中的字符串去代换，这称为“宏替换”或“宏展开”。
## C语言中 .c文件写函数逻辑 .h文件写函数声明
# 5/7星期六
## 位运算（&、|、^、~、>>、<<）
## 正数按位取反变为负数要转为补码形式
## 负数按位取反要先转换位源码，再进行按位取反
## console.log(~15)->-16//-15按位取反（符号位也会取反）为负数，负数以补码的形式存储，所以再取反(符号位不变，操作数位取反)+1->-16
## 补码
```
1的 二进制原码：0000 0001

~1 之后：1111 1110 （~就是按位取反）

以原码的角度看待 1111 1110 ，分析出它是负数（由于第一位是1，因此为负数）

这个负数要在计算机中存储，必须是补码，而原码转换补码规则：
符号位不变，数值位取反加1
所以 1111 1110变成补码为：1000 0010
这样的补码代表：-2
```
## 1000 0000 0000 0000 0000 0000 0000 0000是32位最小整数-2147483648
## 1100 0000 0000 0000 0000 0000 0000 0000             -1073741824
## 计算机逻辑符号与数学的关系
```
∪ 或者 + 表示并集，即是 ｜运算，

∩ 或者 * 表示交集，即是 & 运算。

¬ 表示交集，即是 ~ 运算。

⊕ 表示交集，即是 ^ 运算。
```
## linux 命令
```
netstat -lnpt 查看进程

#用rpm查看是否安装了MySQL
rpm -qa | grep mysql
#用ps命令查看是否有MySQL进程
ps -ef | grep mysql
##########拓展小知识##############
linux系统基本上分两大类，RedHat系列和Debian系列。
RedHat系列：有Redhat、Centos、Fedora等。
Debian系列：有Debian、Ubuntu等 。
RedHat 系列常见的安装包格式 rpm包,安装rpm包的命令是“rpm -参数”。
    包管理工具 yum。
    支持tar包 。
Debian系列常见的安装包格式 deb包,安装deb包的命令是“dpkg -参数”。
    包管理工具 apt-get。
    支持tar包 。

启动 Mysql 服务
systemctl start mysqld.service

查看 Mysql 运行状态
service mysqld status

Linux查看进程 
ps aux

Linux 查看端口占用情况
lsof -i:端口号

cat /etc/centos-release//查看linux版本
Alibaba Cloud Linux release 3 (Soaring Falcon) 
兼容性：兼容CentOS 8、RHEL 8软件生态

#查询服务
ps -ef|grep mysql
ps -ef|grep mysqld

查询所有mysql对应的文件夹
whereis mysql
find / -name mysql

rm -rf /usr/share/mysql //卸载文件
rpm -ev //卸载组件
 
chown将指定文件的拥有者改为指定的用户或组

Linux sudo命令以系统管理者的身份执行指令，也就是说，经由 sudo 所执行的指令就好像是 root 亲自执行

```
## 部署spring boot 命令
```
nohup java -jar demo55-0.0.1-SNAPSHOT.jar > SNAPSHOT.log &
//&确保后台运行 //SNAPSHOT.log指定日志输出

less SNAPSHOT.log
//启动jar包
```
## CSAPP实验环境搭建

1. 下载Docker[参考，到WSL2 linux kernel这一步就可以了](https://zhuanlan.zhihu.com/p/379328928)
2. 打开cmd 运行如下命令:
- docker pull centos

- (获取实验文件)[https://www.geek-share.com/detail/2730781891.html] 解压到D:/狂人笔记/csapp/datalab-handout
- docker container run -it -v D:/狂人笔记/csapp/datalab-handout:/csapp --name=csapp_env ubuntu /bin/bash
- 在docker桌面客户端运行csapp_env容器
- cd csapp
安装c/c++编译环境
- yum install make automake gcc gcc-c++ kernel-devel
准备32位嵌入式c库
- yum install glibc-devel.i686
- 完成
- 运行make
- 运行./btest
- 修改bits.c
- 运行./btest
- 就可以看到实验分数


# 5/6星期五
## 递归是重复调用函数自身实现循环。迭代是函数内某段代码实现循环，而迭代与普通循环的区别是：循环代码中参与运算的变量同时是保存结果的变量，当前保存的结果作为下一次循环计算的初始值。

递归循环中，遇到满足终止条件的情况时逐层返回来结束。迭代则使用计数器结束循环。
# 4/29星期四
## isPrototypeOf() 方法用于测试一个对象是否存在于另一个对象的原型链上
## Object.getPrototypeOf() 方法返回指定对象的原型（内部[[Prototype]]属性的值）。
## instanceof运算符用于检测构造函数的 prototype 属性是否出现在某个实例对象的原型链上
##  object instanceof constructor
## instanceof 运算符用来检测 constructor.prototype 是否存在于参数 object 的原型链上。
## vue与webpack的区别
## instanceof与isPrototypeOf的区别
```
A.isPrototypeOf(B) 判断的是A对象是否存在于B对象的原型链之中
A instanceof B  判断的是B.prototype是否存在与A的原型链之中
```
```
vue官方描述下，vue-cli是：
基于 webpack 构建，并带有合理的默认配置；
而使用webpack构建vue项目，比较灵活，可以自己配置模块相关的规则
```

## js函数的调用方式
1. 作为函数调用 foo()
2. 作为方法调用 o.foo()
3. 作为构造函数调用 new foo()
4. 通过call apply 调用
## 在{}内，函数声明不会提升到外面，只会在{}顶部，函数声明即使在{}内也是会挂在window
```
		a();//报错
	{
		a();//正常
        	function a(){
            		console.log(1);
        	}
       }
        window.a()//正常
```
## 在 对象 里面查找属性不会报错，无则返回undefined
```
	console.log(window.c);//undefined
        var c = {
            name: 'zzm'
        };
        console.log(window.c.d);//undefined
```
## 使用var在函数内是局部的，在函数外属于window，是全局的，不使用var 在函数内部声明的变量也是window的
```
多数语言都支持字面量，而其中最著名的要数 JavaScript，它支持字符串字面量，数字字面量(即2, 8, 10, 16进制数)，布尔值字面量(true, false)，对象字面量({})，数组字面量([])
```
## var变量提升,即使在{}块内，也会提升到外面，在函数里面只会提升到函数头部
### 
```
	console.log('outer:',a);//undefined
        console.log('outer:',b);
        console.log('window-outer:',window.a);
        console.log('window-outer:',window.b);
        {
            console.log('inner:',a);
            var a = 1;

        }
	
	<!--->
	 console.log(a);//报错
       function foo(){
        console.log(a);//undefined
           var a =1;
       }
```
## console.assert()可以断言
## css优先级：就近原则，内联>内部>外部引入
# 4/28星期四
## 浏览器存储的应用场景
```
cookie：短期登陆，例如：token 会过期，需要设置过期时间，过期后重新换取 token
sessionStorage：敏感账号一次性登录
localStorage：长期登录
indexedDB：存储大量结构化数据数据
```
- history 模式改变 url 的方式会导致浏览器向服务器发送请求，这不是我们想看到的，我们需要在服务器端做处理，pushState会发送请求到服务器
- 改变hash不会发送请求到服务器
## 对于开发者来说，rel="noreferrer"属性是最简单的一种方法。<a>、<area>和<form>三个标签可以使用这个属性，一旦使用，该元素就不会发送Referer字段。
## 获取查询字符串参数，并去除问号
### URLSearchParams封装了一些数据的操作
```
let getQueryStringArgs = function() { 
 // 取得没有开头问号的查询字符串
 let qs = (location.search.length > 0 ? location.search.substring(1) : ""), 
 // 保存数据的对象
 args = {}; 
 // 把每个参数添加到 args 对象
 for (let item of qs.split("&").map(kv => kv.split("="))) { 
 let name = decodeURIComponent(item[0]), 
 value = decodeURIComponent(item[1]); 
 if (name.length) { 
 args[name] = value; 
 } 
 }
 return args; 
}
```
## setTiemout
```
setTimeout()的第二个参数只是告诉 JavaScript 引擎在指定的毫秒数过后
把任务添加到这个队列。如果队列是空的，则会立即执行该代码。如果队列不是空的，则代码必须等待
前面的任务执行完才能执行。
```
## 确定页面视口大小
```
let pageWidth = window.innerWidth, 
 pageHeight = window.innerHeight; 
if (typeof pageWidth != "number") { 
 if (document.compatMode == "CSS1Compat"){ 
 pageWidth = document.documentElement.clientWidth; 
 pageHeight = document.documentElement.clientHeight; 
 } else { 
 pageWidth = document.body.clientWidth; 
 pageHeight = document.body.clientHeight; 
 } 
}
```
# !important 
```
另外，访问未声明的变量会抛出错误，但是可以在 window 对象上查询是否存在可能未声明的变量。
比如：
// 这会导致抛出错误，因为 oldValue 没有声明
var newValue = oldValue; 
// 这不会抛出错误，因为这里是属性查询
// newValue 会被设置为 undefined 
var newValue = window.oldValue;
```
```
JSON 的迅速流行并不仅仅因为其语法与 JavaScript 类似，很大程度上还因为 JSON 可以直接被解析
成可用的 JavaScript 对象。与解析为 DOM 文档的 XML 相比，这个优势非常明显
```
- json 可以是简单值，对象和数组
```
1var变量提升
2全局变量？？？？
3函数声明提升
｛｝块
｛｝与123的提升的关系
块的定义

块与函数声明
块级作用域里面的提前声明仅限于块内，而不能作用于块外，但是在外部下面可以使用，是因为函数存在于window中，所以可以输出？？？

块的作用：
1解决函数声明提升 
2配合let解决var变量提升
3由于for也有｛｝
for循环用var声明也会提升到外部使用let可以每次都创建一个块作用域

试一下在函数里面var可不可以跑到window？？？
js类和其他语言的类的最大区别 js是创建__proto__指向构造函数的prototype并不是复制类

模块加载器？
高级程序设计24 25章
```
# 4/27星期三
## Set的使用场景去重，Set不可以取值
## js对象无法使用非字符串作为key！important
## Map->key:value形式的属性集合 Set->存储唯一值，数组形式的集合。他们都是数据结构，都是object类型，都可迭代
## 传统的模块化:闭包和单例模式IIFE
## 迭代器

```
var arr = [1,2,3]; 
var it = arr[Symbol.iterator](); //it就是迭代器
it.next(); // { value: 1, done: false } 
it.next(); // { value: 2, done: false } 
it.next(); // { value: 3, done: false } 
it.next(); // { value: undefined, done: true }
```
## 生成器:返回一个迭代器，每次next返回yield的值
```
	function* foo() {
            yield 'zzm'
            return 1
        }
        var it = foo();
       console.log( it.next());// { value: zzm, done: false } 
       console.log( it.next());// { value: 1, done: false } 
```
### 第一次调用next是启动生成器
```
function* foo() {
            var x = yield 1;
            var y = yield 2;
            var z = yield 3;
            console.log(x, y, z);
        }
        var it = foo();
        // 启动生成器
        console.log(it.next());; // { value: 1, done: false } 
        // 回答第一个问题
        it.next("foo"); // { value: 2, done: false } 
        // 回答第二个问题
        it.next("bar"); // { value: 3, done: false } 
        // 回答第三个问题
        console.log(it.next("baz"));; // "foo" "bar" "baz" 
 // { value: undefined, done: true }
```
## for/of循环是专门用于可迭代对象，例如array，string，set，map
## 对象结构重新命名，妙啊
```
 	var o1 = { a: 1, b: 2, c: 3 },
            o2 = {};
        ({ a: o2.x, b: o2.y, c: o2.z } = o1);
        console.log(o2.x, o2.y, o2.z); // 1 2 3
```
## 块级作用域ES6{}的理解
## a=1不会提升，var a=1;会提升，提升到window，即使在{}块级作用域内也会提升到window
```
console.log(window.a,a);//undefined  undefined
{
  console.log(window.a,a);//undefined  、undefined
    var a = 10;
    console.log(window.a,a)//10 10
}
console.log(window.a,a);//10 10
```
- 块级作用域函数在编译阶段将函数声明提升到全局作用域，并且会在全局声明一个变量，值为undefined。同时，也会被提升到对应的块级作用域顶层。
- 块级作用域函数只有定义声明函数的那行代码执行过后，才会被映射到全局作用域。
```
console.log(window.a,a);//undefined undefined
{
  console.log(window.a,a);//undefined function a(){}
  function a(){};
  console.log(window.a,a)//function a(){} function a(){}
}
console.log(window.a,a);//function a(){} function a(){}
```
## for 循环头部的 let i 不只为 for 循环本身声明了一个 i，而是为循环的每一次迭代都重新声明了一个新的 i
# 4/26星期二
- ES6 开始我们可以使用工具函数 Number.isNaN(..)来检测NaN；
- window.isNaN(... )有BUG
- undefined 是一个内置标识符（除非被重新定义，见前面的介绍），它的值为 undefined
- typeof b; // "undefined" ->尽管b未声明，typeof也是显示undefined，而不是报错
```
if (typeof b === "undefined") { // ReferenceError! 
 // .. 
 } 
 // .. 
 let b;
```
- 然而，通过 typeof 的安全防范机制（阻止报错）来检查 undeclared 变量，有时是个不错的办法
## form提交刷新页面
- 因为早期网页交互模型只能是浏览器提交数据给服务器，服务器做出响应重新返回一个页面，浏览器加载这个页面进行显示。早期前端没有编程式发送网络请求的 API，更没有前端路由管理的概念，所以表单提交跳转页面是广泛接受的方案。
- GitLab是一个基于Git实现的在线代码仓库软件，你可以用GitLab自己搭建一个类似于GitHub一样的仓库，但是GitLab有完善的管理界面和权限控制，一般用于在企业、学校等内部网络搭建Git私服
- GitLab CI/CD 是一个内置在GitLab中的工具，用于通过持续方法进行软件开发： Continuous Integration (CI) 持续集成 Continuous Delivery (CD) 持续交付 Continuous Deployment (CD) 持续部署
```
可视化展示的插件/库有哪些，轻量级图表类的有 Echarts/Highcharts,我用的比较多的是 Echarts，相比 Highcharts 来说，echarts 的数据格式更容易处理，文档阅读性更好；重量级图表插件有 D3，处理类似于 jquery，功能强大，自己是小白的时候实际开发过一些内容~，惨不忍睹。空间位置的有二维的和三维的，其中二维的有天地图，高德，百度，谷歌,LeafLet,openlayers，三维的有 cesium,Three JS，其它第三方可视化插件 Antv G2,DataV(阿里的/基于 vue 的两个)，还有很多，知道了这些工具/插件，那么合理的应用到我们的项目场景中又是一大难题，加油吧，小伙子
那么 cesium 是干嘛的，做 3D 地图的呀，支持很多空间数据格式，在一些可视化展示上面，能够做出很炫酷的数据分析场景
```
- requestAnimationFrame使用递归回调的形式执行，形成动画效果
- IcosahedronGeometry二十面球体
- 光线追踪
```
  			cube = new THREE.Mesh(new THREE.CubeGeometry(1, 1, 1),
                        new THREE.MeshLambertMaterial({color: 0x00ff00}));
 			var light = new THREE.SpotLight(0xffff00, 1, 100, Math.PI / 6, 25);
                	light.position.set(2, 5, 3);
			light.target = cube;
```
- 将圆的一周表示为 2*PI 的度量单位，称为弧度，弧度代表半径为 1、圆心角为 θ 的圆弧
- 下面代码可以使物体做圆周运动，半径为5
```
requestAnimationFrame(draw);
		function draw() {
                alpha += 0.01;
                if (alpha >  Math.PI*2) {
                    alpha -=  Math.PI*2;
                }
                
                cube.position.set( 5*Math.cos(alpha),0, 5*Math.sin(alpha));
                
                renderer.render(scene, camera);
                
                requestAnimationFrame(draw);
            }
```
```
	renderer.setClearColor( 0x002451 );//设置渲染器的bgcolor
	renderer.setPixelRatio( window.devicePixelRatio );
	renderer.setSize( window.innerWidth, window.innerHeight );//设置渲染器的宽高
```
- 网格辅助线
```
			var helper = new THREE.GridHelper( 80, 10 );
			helper.rotation.x = Math.PI / 2;
			group.add( helper );
```
- Ambient Light是模拟漫反射的一种光源
- stats.js 主要用于检测动画运行时的帧数
## threejs绘制图像的过程:
1. scene = new THREE.Scene();
2. camera = new THREE.PerspectiveCamera( 50, window.innerWidth / window.innerHeight, 1, 1000 );
3. scene.add( camera );
4. group = new THREE.Group();
5. scene.add( group );
6. 6.1 new THREE.ShapeGeometry( shape );//创建形状
6.2 var mesh = new THREE.Mesh( geometry, new THREE.MeshPhongMaterial( { color: color, side: THREE.DoubleSide } ) );
6.3 group.add( mesh );
7. renderer = new THREE.WebGLRenderer( { antialias: true } );
8. container.appendChild( renderer.domElement );//container是DOM
9. 调用动画循环渲染
```
			function animate() {
				requestAnimationFrame( animate );
				render();
				// stats.update();
			}
			function render() {
				group.rotation.y += ( targetRotation - group.rotation.y ) * 0.05;
				renderer.render( scene, camera );
			}
```
# 4/25星期一
## three.js加载的模型全是黑色
- 如果调整环境光后还是黑色或其他的纯色，那么将模型的材质里的emssive设置为material.color，如果材质里有纹理，再把emissiveMap设置为material.map
```
scene.add(new THREE.AmbientLight(0x666666));//环境光

gltf.scene.traverse( function ( child ) {
  if ( child.isMesh ) {
    child.material.emissive =  child.material.color;
    child.material.emissiveMap = child.material.map ;
  }
});
```
- thingjs使用在线开发点击分享可以生成链接，选择公开项目，可以通过iframe内嵌到其他web页面
- thingjs提供模型，也可以自己建一些简单的模型,使用marker为模型添加覆盖物
##  three.js导入外部模型报错Unexpected token < in JSON at position 0 
- GLTFLoader加载失败，注意根路径是public
# 4/24星期日
## vue使用three.js
```
风机3D数据可视化，使用了three.js：
GLTFLoader加载3D模型，
three-outlinepass->Three.js 后期处理-物体边界线条高亮处理-OutlinePass
@tweenjs/tween.js 动画引擎，让动画顺滑
Three.js依赖一些要素，第一是scene，第二是render，第三是carmea
轨道控制器（OrbitControls）建立控制 讓鏡頭旋轉
平行光（DirectionalLight）
CSS 2D渲染器（CSS2DRenderer）如果你希望将三维物体和基于HTML的标签相结合，
则这一渲染器将十分有用。在这里，各个DOM元素也被包含到一个CSS2DObject实例中，并被添加到场景图中。
stats.js 介绍
（1）stats.js 是一个 Three.js 开发的辅助库，这个库同样也是 Three.js 作者开发的。
（2）stats.js 主要用于检测动画运行时的帧数。

```
- 轨道控制器相关设置
```
// Set to false to disable this control
//鼠标控制是否可用
	this.enabled = true;

// "target" sets the location of focus, where the object orbits around
//聚焦坐标
	this.target = new THREE.Vector3();

// How far you can dolly in and out ( PerspectiveCamera only )
//最大最小相机移动距离(景深相机)
	this.minDistance = 0;
	this.maxDistance = Infinity;

// How far you can zoom in and out ( OrthographicCamera only )
//最大最小鼠标缩放大小（正交相机）
	this.minZoom = 0;
	this.maxZoom = Infinity;

// How far you can orbit vertically, upper and lower limits.
// Range is 0 to Math.PI radians.
//最大仰视角和俯视角
	this.minPolarAngle = 0; // radians
	this.maxPolarAngle = Math.PI; // radians

// How far you can orbit horizontally, upper and lower limits.
// If set, must be a sub-interval of the interval [ - Math.PI, Math.PI ].
//水平方向视角限制
	this.minAzimuthAngle = - Infinity; // radians
	this.maxAzimuthAngle = Infinity; // radians

// Set to true to enable damping (inertia)
// If damping is enabled, you must call controls.update() in your animation loop
//惯性滑动，滑动大小默认0.25
	this.enableDamping = false;
	this.dampingFactor = 0.25;

// This option actually enables dollying in and out; left as "zoom" for backwards compatibility.
// Set to false to disable zooming
//滚轮是否可控制zoom，zoom速度默认1
	this.enableZoom = true;
	this.zoomSpeed = 1.0;

// Set to false to disable rotating
//是否可旋转，旋转速度
	this.enableRotate = true;
	this.rotateSpeed = 1.0;

// Set to false to disable panning
//是否可平移，默认移动速度为7px
	this.enablePan = true;
	this.keyPanSpeed = 7.0;	// pixels moved per arrow key push

// Set to true to automatically rotate around the target
// If auto-rotate is enabled, you must call controls.update() in your animation loop
//是否自动旋转，自动旋转速度。默认每秒30圈
	this.autoRotate = false;
	this.autoRotateSpeed = 2.0; // 30 seconds per round when fps is 60

// Set to false to disable use of the keys
//是否能使用键盘
	this.enableKeys = true;

// The four arrow keys
//默认键盘控制上下左右的键
	this.keys = { LEFT: 37, UP: 38, RIGHT: 39, BOTTOM: 40 };

// Mouse buttons
//鼠标点击按钮
	this.mouseButtons = { ORBIT: THREE.MOUSE.LEFT, ZOOM: THREE.MOUSE.MIDDLE, PAN: THREE.MOUSE.RIGHT };

```
# 4/22星期五
## browse the repository at this point of history 在这个历史时刻浏览存储库 不会覆盖现在的记录，只是浏览过去某个时刻的状态
## 拿到一个项目若报sass安装错误，将原来的node-sass和sass-loader uninstall 再安装相应的node-sass和sass-loader,还要注意安装node-sass有node版本的要求
```
sass-loader 4.1.1，node-sass 4.3.0
sass-loader 7.0.3，node-sass 4.7.2
sass-loader 7.3.1，node-sass 4.7.2
sass-loader 7.3.1，node-sass 4.14.1
```
## 查看vue脚手架版本 vue -V 报错不是有效命令
- 若装了nvm 则配置系统环境 path 为vue.cmd的路径，比如：G:\nvm\nvm\v10.15.2
## 使用vue脚手架创建uniapp项目注意事项
```
1.node最好使用10  v10.15.2有效
2.vue@cli使用4 @vue/cli 4.5.10有效
3.vue create -p dcloudio/uni-preset-vue my-project 便可创建
```
- 使用hbuildx创建uniapp项目和vue-cli创建项目的区别不大，公司的老项目是使用vue脚手架创建的
## 注意 vue脚手架创建的uniapp项目可以发布H5、各种小程序，所以使用脚手架创建即可，最多是没有uniapp专属的api提示功能（问题不大）
```
3.1编译器的区别
cli创建的项目，编译器安装在项目下。并且不会跟随HBuilderX升级。如需升级编译器，执行 npm update，或者手动修改package.json 中的 uni 相关依赖版本后执行 npm install。更新后可能会有新增的依赖并不会自动安装，手动安装缺少的依赖即可。
HBuilderX可视化界面创建的项目，编译器在HBuilderX的安装目录下的plugin目录，随着HBuilderX的升级会自动升级编译器。
已经使用cli创建的项目，如果想继续在HBuilderX里使用，可以把工程拖到HBuilderX中。注意如果是把整个项目拖入HBuilderX，则编译时走的是项目下的编译器。如果是把src目录拖入到HBuilderX中，则走的是HBuilderX安装目录下plugin目录下的编译器。
cli版如果想安装less、scss、ts等编译器，需自己手动npm安装。在HBuilderX的插件管理界面安装无效，那个只作用于HBuilderX创建的项目
npm install sass-loader@10  node-sass@4 --save-dev
1
  sass-loader@11 以上需要是 webpack5，这里示例的uni-app项目是通过vue-cli4生成的(webpack4)。所以这里指定10版本

3.2开发工具的区别
cli创建的项目，内置了d.ts，同其他常规npm库一样，可在vscode、webstorm等支持d.ts的开发工具里正常开发并有语法提示。
使用HBuilderX创建的项目不带d.ts，HBuilderX内置了uni-app语法提示库。如需把HBuilderX创建的项目在其他编辑器打开并且补充d.ts，可以在项目下先执行
npm init，然后npm i @types/uni-app -D，来补充d.ts。但vscode等其他开发工具，在vue或uni-app领域，开发效率比不过HBuilderX。详见：https://ask.dcloud.net.cn/article/35451

！！！发布App时，仍然需要使用HBuilderX。其他开发工具无法发布App，但可以发布H5、各种小程序。如需开发App，可以先在HBuilderX里运行起来，然后在其他编辑器里修改保存代码，代码修改后会自动同步到手机基座。
如果使用cli创建项目，那下载HBuilderX时只需下载10M的标准版即可。因为编译器已经安装到项目下了。

```
# 4/21星期四
## 微信小程序使用weui
- 若是一直报错，就重启一下项目
```
在app.json加入
 "useExtendedLib": {
      "weui": true
    }
全局注册
  "usingComponents":{"mp-icon": "weui-miniprogram/icon/icon",}
example：
<mp-icon icon="close"></mp-icon>
    
```
- 微信小程序构建npm配置
```
 "packNpmManually": true,
    "packNpmRelationList": [
      {
        "packageJsonPath": "./package.json",
        "miniprogramNpmDistDir": "./"
      }
    ]
```
## 安装node-sass要注意版本，不建议使用默认安装
```
sass-loader 4.1.1，node-sass 4.3.0
sass-loader 7.0.3，node-sass 4.7.2
sass-loader 7.3.1，node-sass 4.7.2
sass-loader 7.3.1，node-sass 4.14.1
```
```
智慧卫监平台：提供医疗废物、放射卫生在线监督功能

使用者：卫生计生监督执法人员或者医疗机构

医废溯源->医疗卫生机构的医疗废物溯源
监管机构：监管医疗机构的医废报表是否按时提交
医废指标：感染性	病理性	损伤性	药物性	化学性
异常预警：工作人员操作不当

放射机构：
放射机构应当：使用剂量低、辐射风险较小的放射检查技术。
在各种放射检查技术中择优选择，比如胸部检查，有透视、普通X射线摄影、CR（计算机X线摄影）、DR（数字X线摄影）甚至CT等多种选择，这时要充分考虑经济可承受性、对某种疾病的特异性和敏感性、检查导致的受检者剂量的高低、需要复查的可能性、需要进行的各种检查的总体潜在危害等等。健康体
特检院电梯部：
电梯部主要从事电梯及相关产品的检验检测、型式试验、鉴定评审、安全风险评估、质量抽查、科学研究、法规标准起草、失效分析、技术仲裁、事故调查处理、司法鉴定、技术咨询等

120指挥调度系统使用对象：卫计委
```
# 4/20星期三
## 项目启动与vue.config.js
- "dev": "webpack-dev-server --inline --progress --config build/webpack.dev.conf.js"使用webpack创建项目，启动config里面的index.js配置文件
- "serve": "vue-cli-service serve"这是使用vue-cli创建的项目启动vue.config.js文件
- 都是在上面两个文件里面配置跨域
## 4个项目总结

1，自来水厂后台：大屏展示加后台
使用vue2语法

2，观澜H5：uniapp
cus-button是自定义组件
在main全局注册
uni-icon是uni-ui组件
[uni-ui使用参考](https://www.jianshu.com/p/d5ac4db0b16c)

3，电梯一码通：mpvue
static里面的compnents的i-button是iview-weapp组件，直接在github下载代码复制到项目，在app.json里面的usingComponents属性注册使用 [官网](https://weapp.iviewui.com/components/panel)
usingComponents还可以直接注册微信小程序官方组件库"mp-icon": "weui-miniprogram/icon/icon"便可直接使用
mpvue可以使用vue的语法，所以自定义组件和vue的使用方式一样

4，智慧卫监
使用vue2语法
## 跨域BUG
```
1.删除baseURL，才能走代理
2.注意配置dev的host要是localhost
3.proxyTable那个代理的正则匹配<   一定要加/   >这个很重要

```
- 代理服务器会自动识别//和/,将//替换为/
## 关于changeOrigin的作用，设置为true就对了[参考](https://blog.csdn.net/qq_39291919/article/details/108807111)
代理target是匹配拼接
- vue.config.js和config下面的index.js都可配置代理
## vue-cli-service serve会启用vue.config.js 
## webpack-dev-server会启用config下面的index.js
## vue create 和 vue init 的区别[参考](https://segmentfault.com/a/1190000040099773)
```
vue create 和 vue init 有什么区别
01、vue create
vue create 是vue-cli3.x的初始化方式，目前模板是固定的，模板选项可自由配置，创建出来的是vue-cli3的项目，与cue-cli2项目结构不同，配置方法不同，具体配置方法参考官方文档。

02、vue init
vue init 是vue-cli2.x的初始化方式，可以使用github上面的一些模板来初始化项目，webpack是官方推荐的标准模板名。vue-cli2.x项目向3.x迁移只需要把static目录复制到public目录下，老项目的src目录覆盖3.x的src目录(如果修改了配置，可以查看文档，用cli3的方法进行配置)
```
# 4/19星期二
## 小程序调用validate方法会调用onShow方法
## VM1999 WAService.js:2 TypeError: Cannot read property 'call' of undefined 这个bug经常出现
## unexpected character `` 这个报错莫名其妙，vscode格式化代码格式会报
# 4/18星期一
## 当微信小程序只显示pages/xxx/.wxml路径，不展示页面的时候，重新npm run start:wx一下
## 在线查看使用了哪些iconfont

[在线链接](http://blog.luckly-mjw.cn/tool-show/iconfont-preview/index.html)
- 例子：url('//at.alicdn.com/t/font_880468_eglfuc5j6ec.ttf?t=1577442795375') format('truetype')
- 线上预览链接使用这个格式//at.alicdn.com/t/font_880468_eglfuc5j6ec.ttf?t=1577442795375
## iview-weapp使用
- 比如button，将这个组件拷贝到项目
[Button](https://github.com/TalkingData/iview-weapp/blob/master/src/button/index.wxml)
```
app.json配置
"usingComponents": {
    "i-button": "static/component/button/index"
}，
"useExtendedLib": {
    "weui": true
}
便可全局使用
```
# 4/15星期五
- 当实在是解决不了bug的时候，试试将原来的代码块复制过来，原因可能是不小心误删了某些东西
## 生成二维码
```
npm install weapp-qrcode --save

import drawQrcode from "weapp-qrcode";

<canvas class="myQrcode" canvas-id="myQrcode"></canvas>

drawQrcode({
      width: 150,
      height: 150,
      canvasId: "myQrcode",
      text:'zzm'
    });
```
## app.json配置usingComponents全局自定义组件配置
## weui微信小程序自带的组件库，在app.json直接配置就可以使用
## sourcemap
- sourceMap就是一个信息文件，里面储存着打包前的位置信息
- 有了它，出错的时候，浏览器控制台将直接显示原始代码出错的位置，而不是转换后的代码，点击出错信息将直接跳转到原始代码位置。
## 瀑布图
```
蓝线表示 DOMReady 事件。事件触发的条件是：浏览器已经把整个 HTML 文档的 DOM 结构解析完毕。一般前端开发者监听这个事件是为了可靠地在文档中查找元素。这个事件触发之前有可能只下载了半截 HTML，想要的元素还没出现。

红线表示 load 事件，触发条件是：整个页面的 JS CSS 图片都下载完毕。用户看到的进度条/小菊花已经不再显示为 “忙” 的状态。是用户眼中的加载完毕。

DNS Lookup [深绿色] - 在浏览器和服务器进行通信之前, 必须经过DNS查询, 将域名转换成IP地址. 在这个阶段, 你可以处理的东西很少. 但幸运的是, 并非所有的请求都需要经过这一阶段.

Initial Connection [橙色] - 在浏览器发送请求之前, 必须建立TCP连接. 这个过程仅仅发生在瀑布图中的开头几行, 否则这就是个性能问题(后边细说).

SSL/TLS Negotiation [紫色] - 如果你的页面是通过SSL/TLS这类安全协议加载资源, 这段时间就是浏览器建立安全连接的过程. 目前Google将HTTPS作为其 搜索排名因素 之一, SSL/TLS 协商的使用变得越来越普遍了.

Time To First Byte (TTFB) [绿色] - TTFB 是浏览器请求发送到服务器的时间+服务器处理请求时间+响应报文的第一字节到达浏览器的时间. 我们用这个指标来判断你的web服务器是否性能不够, 或者说你是否需要使用CDN.

Downloading (蓝色) - 这是浏览器用来下载资源所用的时间. 这段时间越长, 说明资源越大. 理想情况下, 你可以通过控制资源的大小来控制这段时间的长度.
```
```
电梯一码通项目结构：电梯安全主页，pages目录结构：brake制动器？？
canvas文件夹->手写板
```
# ❓mpvue的onShow和mounted生命周期有点混乱
- onShow() 事件不接受参数，因此无法获取页面 url 传递过来的参数，只有 onLoad() 事件可以
```
列表的详情可以使用统一的page->zhengchexingwen,只需要在onLoad生命周期函数里面判断一下跳转传参再设置wx.setNavigationBarTitle的title
```
# 4/14星期四
# 震惊mpvue项目pages下的目录-> ../指向爷爷级别
pages新增了三个个文件夹wenshenchangshidetail searchtemp searchdetailtemp  
## 微信小程序文件太大上传失败
- 使用分包，格式如下
- 注意要把pages配置里面的pages/anquan/main路径删除，不然会报bug“pages *** 不应该在分包 subPackages[*] 中”
```
 "subPackages": [
    {
      "root": "pages/toVideo",
      "pages": [
        "room"
      ]
    },
    {
      "root": "pages/anquan",
      "pages": [
        "main"
      ]
    },
    {
      "root": "pages/searchtemp",
      "pages": [
        "main"
      ]
    }
  ]
```
- anquan文件夹新增了三个文件weishenchangshi.vue mockData.js weishenmockData.js
```
searchtemp文件夹搜索列表页 
searchdetailtemp文件夹搜索列表详情页

weishenchangshi.vue卫生常识列表页
weishenmockData.js卫生常识数据

mockData.js 法规政策数据
```
## mpvue遇到bug导致输入框无法选中，试试重启小程序项目
## mpvue main路径指代index.vue和与文件夹同名的vue文件
## 一码通逻辑
```
anquan文件夹下的index动态展示组件法规政策，电梯常识，安全视频组件注释了（暂时无法使用）
菜单里的每个列表也拆分为了组件，法规政策详情也拆成了一个组件
电梯常识详情->对于anquachangshi文件夹的index
anquanshiping和anquan两个组件暂时没用到
```
## https://www.sz96333.com 不在以下 request 合法域名列表中（为什么小程序也可以正常运行）
# 4/13星期三
## dev和 start是两个等价的命令，执行其中之一都可以将项目以开发模式启动
## build目录下是一些用于项目编译打包的node.js脚本和webpack配置文件。一般情况下不需要修改这些文件。
## mpvue可以将小程序打包到多端
```
npm run dev:my   // 支付宝
npm run dev:swan  // 百度
npm run dev:tt   // 今日头条
```
## 小程序实现登录的流程，是先通过wx.login获取code，然后再用code请求自己服务器，自己服务器拿着code去微信服务器获取openid，然后业务自定义实现登录
## git reset --hard 15455331b72702014a8eb3fcff91443ac2837280
- 版本回退到commit的版本
```
git pull在有冲突的时候是不会拉取的
git push也可以检测冲突
冲突不解决也可以提交，会显示冲突字符串
```
## uniapp不需要重置css？
```
vue.config.js配置格式
'/return_mh_server':{
		  target:'https://ilh.szlhq.gov.cn'
	  }
.vue文件使用格式
 uni.request({
	      url: '/return_mh_server/nlztRequest/getAppsmsessions', //仅为示例，并非真实接口地址。
		  method:'get',
	      data: {
	        usertoken: this.token
	      },
	      success: (res) => {
          this.ipone = res.data.sjh
	      }
	  });
浏览器显示的URL路径：https://localhost:8080/return_mh_server/nlztRequest/getAppsmsessions?usertoken=
完整的URL路径：https://ilh.szlhq.gov.cn/return_mh_server/nlztRequest/getAppsmsessions?usertoken=
```
# 4/12星期二
## mixin使用事项
- 对于creaetd，mounted 等生命周期函数。mixin中的代码先执行，单文件中的后执行
- 对于同名的变量和方法，只执行page中的代码。
## uni-ui组件支持easycom模式，直接将组件下载到components就可以直接使用，不需要注册
- uniapp项目运行到微信小程序
- 下载微信开发者工具稳定版
- 要使用公司内部人员的appid
- 1.在uniapp项目的manifest.json文件设置appid
- 2.在微信开发者工具使用开发人员的appid
- uniapp运行到小程序模拟器，打不开的话手动导入dist文件夹的mp-weixin文件夹

# 4/11星期一
- 401状态码是未授权
```
4/8
vue-cli是基于nodejs+webpack封装的命令行工具。你可以理解为汇集了各种命令的 bash，或者bat。
原本需要自己配置webpack的相关配置，被cli简化了。并且按照vue的用户习惯整理了一套构建和目录规范。
这样，你只要按照vue-cli的配置规则来，就可以满足很多繁琐的webpack+plugin配置

cli-service是一个运行时依赖，基于 webpack 构建

dev.env.js和prod.env.js配置文件有何作用？
你用vue-cli模板构建的vue项目都会有这些文件，属于webpack相关配置；
dev.env.js文件是开发环境的变量，npm run dev命令；在build文件下webpack.dev.conf可找到在什么地方引入了此变量；
prod.env.js文件是生产环境的变量，npm run build命令；在build文件下webpack.prod.conf可找到在什么地方引入了此变量；

原来老版本的vue项目中有build文件夹。@vue-cli4.0或者3.0没有build文件夹
```
# vue项目不能运行node-sass，注意node版本与node-sass版本
# 安装最新的脚手架需要node版本12.0.0

# 问题 
```
node-sass官网显示Node 12支持4.12+
公司项目使用"node-sass": "^4.12.0"，下载node12版本还是不行
下node12是因为vue-cli最新版本需要node最少12+
```
```
公司水厂监测项目node环境Node.js:10.15.1 npm:6.4.1
```
# 疑惑
```
git clone 两个人修改同一个分支的内容为什么不发生冲突？
```
```
git clone 会clone所有分支
创建分支是clone某个分支所有文件到新的分支
github 合并分支 是将其他分支合并到master，如果没有冲突，那么其余分支的内容会添加到master分支
git pull是拉取加合并，git pull后若修改，提交，若期间同时没有更改同一份代码，那么不会有冲突，若其他人改了，则会有冲突
```
- jsconfig.json文件是vscode自动生成的。通过jsconfig.json文件定义一个JavaScript项目。目录中是否存在此类文件表示该目录是JavaScript项目的根目录
# babel插件介绍
[babel插件介绍](https://zhuanlan.zhihu.com/p/61780633)
- babel插件作用：扩展既有方法、提前执行运行时代码、提高代码性能
- babel.config.js是babel的全局配置文件，@vue/cli-plugin-babel/preset是vue-cli默认安装的一个babael npm包
- babel的presets：预设其实就是一组babel插件的集合
```
// 查看全局安装路径
npm root -g
C盘Roaming文件夹存储你所安装的应用程序的设置和缓存文件
npx
1.临时安装可执行依赖包，不用全局安装，不用担心长期的污染。
2.可以执行文件
```
# browserslist配置的作用 使用npx browserslist可以查看限定的浏览器的范围
```
在创建前端工程的时候，一个比较好的做法是制定你的工程上线之后主要支持的浏览器版本，
在你支持的浏览器版本里面，你的项目运行没问题，不在范围的浏览器可能会出现一些高级 JS，css 特性不支持的 bug。
哪些新的 ES6+的特性保留原样，哪些特性要转译成 es5，
webpack，babel 本身是通过这个工具提供的浏览器支持范围来确定的
```
# polyfill
- 浏览器不支持某些功能，polyfill使其能够用自身支持的方式实现该功能
```
比如：
提示：polyfill 指的是“用于实现浏览器不支持原生功能的代码”，比如，现代浏览器应该支持 fetch 函数，对于不支持的浏览器，
网页中引入对应 fetch 的 polyfill 后，这个 polyfill 就给全局的window对象上增加一个fetch函数，
让这个网页中的 JavaScript 可以直接使用 fetch 函数了，就好像浏览器本来就支持 fetch 一样。
```
# Babel 中的预设就是一组babel插件的集合
```
如果手动修改package.json里面的模块的版本,npm i则会下载package-lock.json里面的版本
加入npm指定版本，则node_modules和package-lock.json都会是指定的那个版本
```
```
使用npm i安装中会根据package-lock.json来安装
当我们在一个项目中npm install时候，会自动生成一个package-lock.json文件，
和package.json在同一级目录下。package-lock.json记录了项目的一些信息和所依赖的模块。
这样在每次安装都会出现相同的结果. 不管你在什么机器上面或什么时候安装。

当我们下次再npm install时候，npm发现如果项目中有package-lock.json文件，会根据package-lock.json里的内容来处理和安装依赖而不再根据package.json。注意，使用cnpm install时候，并不会生成package-lock.json文件，也不会根据package-lock.json来安装依赖包，还是会使用package.json来安装。
```
