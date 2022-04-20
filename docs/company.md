# 4/20星期三
## vue create 和 vue init 的区别[参考](https://segmentfault.com/a/1190000040099773)

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
