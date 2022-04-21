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
