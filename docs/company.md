# 4/13星期三
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
