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
