## 过渡页面请求

  Elephant Wallet的开发团队提供了一个过渡页面，用于解决从PC Web或者是从微信里启动Elephant的问题。
  
  当第三方想要启动Elephant Wallet时，可以统一向过渡页面发起请求，它会对运行环境进行判断，如果是在pc web，它将显示一个二维码，用户可以打开Elephant Wallet对它扫码，即可跳转到预期的页面。
  
  如果当前是在微信中，它会显示一个提示用户使用手机浏览器打开的提示页面，当用户在微信里操作使用浏览器打开以后，手机上会自动唤起Elephant Wallet。 
  
  如果是在手机移动浏览器里，它会自动跳转到"elaphant://..."唤起Elephant Wallet。
  
  这样无论是App还是Web，无论是手机还是PC，都可以向Elephant Wallet发起调用。这个过渡页面对Elephant Wallet支持的所有命令都有效。
  
  以上面对Elephant调用的URL为例：
  ```
  https://elephantwallet.app/redirect/?
  appName=Hackathon&
  appTitle=Hackathon&
  autoRedirect=True&
  redirectURL=elaphant%3A%2F%2Fidentity%3FReturnUrl%3Dhttp%253A%252F%252Fbing.com%26AppID%3D7d80c7e800f5842b3b8e7ec7318189f66b7fd5b6db13bb80fbd89d2b1c444772c1d0202fea1e9cbabbf3258b3d91685484c02c2ae52d78ca39e2e54593ec81dd%26PublicKey%3D032f6347b27401dc0bced2de0ab4531e62c496841cd8e67a58c572e3018dcb72d9%26DID%3DiXzenTELVRDc712tmt2Qvbtk3KcAwV2tU8%26AppName%3DHackathon%26RequestInfo%3Delaaddress%2CEmail%2CNickname%26description%3DEApp%2520Community%26RandomNumber%3D4284432979
  ```

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
appName=Hackathon&
appTitle=Hackathon&
autoRedirect=True&
redirectURL=elaphant%3A%2F%2Fidentity%3FAppID%3D7d80c7e800f5842b3b8e7ec7318189f66b7fd5b6db13bb80fbd89d2b1c444772c1d0202fea1e9cbabbf3258b3d91685484c02c2ae52d78ca39e2e54593ec81dd%26AppName%3DHackathon%26RandomNumber%3D123456789%26DID%3DiXzenTELVRDc712tmt2Qvbtk3KcAwV2tU8%26PublicKey%3D032f6347b27401dc0bced2de0ab4531e62c496841cd8e67a58c572e3018dcb72d9%26ReturnUrl%3Dhttp%253A%252F%252Fbing.com%26RequestInfo%3Delaaddress%2CEmail%2CNickname

```
