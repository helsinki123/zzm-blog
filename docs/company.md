# 4/22星期五
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
