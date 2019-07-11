## 过渡页面请求

过渡页面目的是帮助开发者实现从PC WEB、微信等环境中唤起Elephant Wallet。

在PC WEB里，它会将"elaphant://...."请求URL转换为二维码，用户可以启动Elephant Wallet扫码来完成调用请求。

如果是在微信里，它会提示用户在浏览器中打开此页面。

如果是在手机移动浏览器里，它会自动跳转到"elaphant://..."唤起Elephant Wallet。

**附加功能：前端助手**
除了上述功能之外，它还实现了一个特殊的功能：帮助前端处理Elephant Callback。对于一个Web site来说，如果它不想自己处理回调，甚至于是一个纯前端的Web site，它可以在调用过渡页面时附加一个参数“autoRedirect=True”，过渡页面将会负责接收Elephant Wallet的回调，收到回调并验证以后，先前的二维码页面将跳转到"elaphant://..."中设置的<Return URL>页面。

**请求格式：**
```
https://elephantwallet.app/redirect?
	appName=<appName>&
	appTitle=<appTitle>&
	autoRedirect=<autoRedirect>&
	redirectURL=<redirectURL>
```
**指令参数：**

字段名称           | 类型              | 是否必选 | 描述
----------------------| ------------------- | ------------------- | -------------------
appName                | String     | 必选 | 应用的名字
appTitle               | String     | 必选 | 应用的名字
autoRedirect           | String    | 可选 | True或者False，在PC WEB中打开时收到结果以后是否自动跳转
redirectURL         | String     | 必选 | 大象钱包的协议 拼接需要encodeURIComponent


**大象钱包过渡页面请求：**
```
https://elephantwallet.app/redirect/?
appName=ELA%20Multi-sig%20Wallet&
appTitle=ELA%20Multi-sig%20Wallet&
autoRedirect=True&redirectURL=elaphant%3A%2F%2Felapay%3FAppID%3Df4d54cd97afa828a9705e38eb679fad564cf3adf4cecd1a5503498155969b07baaa4c4a016084c0f21e06c59e76c33929925052d7d0ae3cfc679a0fdf48ec23f%26AppName%3DELA%20Multi-sig%20Wallet%26Description%3Dtest%20pay%26OrderID%3D12345%26CoinName%3DELA%26Amount%3D0.1%26ReceivingAddress%3DEYf3wvaiNHWvrEXL1bwSV5LytbhiPb6Vby%26DID%3DipFFpL1JwPRQKfhmxak8r1wWEbdkJ3rXZu%26PublicKey%3D035731ff69f8cfdcd9881e573143d71de2390b2e8e71fa14729e6b506f5d74939d%26ReturnUrl%3Dhttps%253A%252F%252Fwww.baidu.com%252F

```
