##  报错Unexpected token < in JSON at position 0 
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
