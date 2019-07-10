## 大象钱包过渡页面请求
**请求格式：**
```
https://elephantwallet.app/redirect?
	appName=<appName>&
	appTitle=<appTitle>&
	traceid=<traceid>&
	redirectURL=<redirectURL>
```
**指令参数：**

字段名称           | 类型              | 是否必选 | 描述
----------------------| ------------------- | ------------------- | -------------------
appName                | String     | 必选 | 应用的名字
appTitle               | String     | 必选 | 应用的名字
traceid                 | String    | 可选 | 追踪回调的地址
redirectURL         | String     | 必选 | 大象钱包的协议 拼接需要encodeURIComponent


**大象钱包过渡页面请求：**
```
https://elephantwallet.app/redirect/?
appName=ELA%20Multi-sig%20Wallet&
appTitle=ELA%20Multi-sig%20Wallet&
traceid=35b08aaf0cda458d818e6f7f7f77a6f4&redirectURL=elaphant%3A%2F%2Felapay%3FAppID%3Df4d54cd97afa828a9705e38eb679fad564cf3adf4cecd1a5503498155969b07baaa4c4a016084c0f21e06c59e76c33929925052d7d0ae3cfc679a0fdf48ec23f%26AppName%3DELA%20Multi-sig%20Wallet%26Description%3Dtest%20pay%26OrderID%3D12345%26CoinName%3DELA%26Amount%3D0.1%26ReceivingAddress%3DEYf3wvaiNHWvrEXL1bwSV5LytbhiPb6Vby%26DID%3DipFFpL1JwPRQKfhmxak8r1wWEbdkJ3rXZu%26PublicKey%3D035731ff69f8cfdcd9881e573143d71de2390b2e8e71fa14729e6b506f5d74939d%26ReturnUrl%3Dhttps%253A%252F%252Fwww.baidu.com%252F

```
