# 如何使用DID登录
  DID是通过区块链生成的数字身份，类似钱包地址一样，也是通过私钥计算生成。第三方应用可以使用DID作为账号。
  
  用户的DID保存在Elephant Wallet里，第三方应用可以向Elephant Wallet发起请求来获得DID信息。同时Elephant Wallet也保存着用户的钱包地址、昵称、Email和手机号码等个人信息，第三方可以按需请求，用户也可以选择是否授权。这个过程从用户体验上来说，类似第三方请求使用微信或者支付宝登录。
  
  具体操作如下：

## Step1 申请开发应用的AppId
  第三可以向elephant wallet发起调用请求，但它必须拥有一个合法的DID和Appid。其中DID代表开发者身份，而Appid是应用的唯一标识。
  
  Appid的生成规则是：用DID主私钥对Appname进行签名，生成的签名字符串即是Appid。开发者可以自己生成，也可以通过下面的页面生成，它的源码在github上，可以离线运行。
  
  [生成DID和Appid](https://zuohuahua.github.io/Elastos.Tools.Creator.Capsule)
  
  这里提供一个已经生成好的，测试用的DID和Appid，开发者可以直接使用。
  ```
  DID：iXzenTELVRDc712tmt2Qvbtk3KcAwV2tU8
  PublicKey：032f6347b27401dc0bced2de0ab4531e62c496841cd8e67a58c572e3018dcb72d9
  App Name：Hackathon
  Appid：7d80c7e800f5842b3b8e7ec7318189f66b7fd5b6db13bb80fbd89d2b1c444772c1d0202fea1e9cbabbf3258b3d91685484c02c2ae52d78ca39e2e54593ec81dd
  ```

## Step2 向Elephant Wallet发起调用
  Elephant Wallet通过拦截特殊scheme前缀的URL来接收调用请求；通过回调第三方指定的URL来返回结果。
  
  示例：
  ```
  elaphant://identity?
  ReturnUrl=http%3A%2F%2Fbing.com&
  AppID=7d80c7e800f5842b3b8e7ec7318189f66b7fd5b6db13bb80fbd89d2b1c444772c1d0202fea1e9cbabbf3258b3d91685484c02c2ae52d78ca39e2e54593ec81dd&
  PublicKey=032f6347b27401dc0bced2de0ab4531e62c496841cd8e67a58c572e3018dcb72d9&
  DID=iXzenTELVRDc712tmt2Qvbtk3KcAwV2tU8&
  AppName=Hackathon&
  RequestInfo=elaaddress,Email,Nickname&
  description=Hackathon&
  RandomNumber=4284432979
  ```
  
  可以在 https://www.qr-code-generator.com/ 生成二维码，并使用Elephant Wallet扫码，识别成功以后，它将在手机上会自动打开浏览器并跳转到设置的Return URL：https://bing.com
  
  你可以将上面的例子拷贝到手机浏览器中打开，也会自动唤起Elephant Wallet，结果是一样的。
  

## Step3 处理Elephant Wallet返回内容

  如果你查看一下浏览器的URL，你会发现它的参数类似下面这样：
  ```
  https://cn.bing.com/?Data=%7B%0A%20%20%22Email%22%20:%20%22%22,%0A%20%20%22PublicKey%22%20:%20%22030ec25cfd4a584fda804f21c87a958e26161c82d72066d92327e2afa4789d29ae%22,%0A%20%20%22DID%22%20:%20%22ieS74VZw8vP9AcnvkseyV9BXwR6m54LFwi%22,%0A%20%20%22ELAAddress%22%20:%20%22EYH69rRAfDQ2HRa35bmYRh6UoAZ8u3n7ZJ%22,%0A%20%20%22Nickname%22%20:%20%22Your%20Nickname%22,%0A%20%20%22RandomNumber%22%20:%20%224284432979%22%0A%7D&Sign=4C05B3C995F9BD12D3C2B2E9ECEF18CC372272BB8A3AD340B34213082FB7F39084EB208FDDDEC3A65352DAE082FCFA88F8B15A46E90896664460715421F40456
  ```
  
  它附带了Data和Sign两个参数，Data是用户授权返回的个人信息，Sign是对Data的签名。Data的内容是被转换为string的Json对象。
  
  上面示例使用的是Return URL参数，这将会在手机端打开这个URL。
  
  也可以配置Callback URL，那么Elephant Wallet将会以POST方法返回Data和Sign，具体请参考协议文档。
  
  [Elephant Wallet Identity Command](https://github.com/elastos/Elastos.Developer.Doc/blob/master/CN/4.%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5/4.Elephant%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5%E5%8D%8F%E8%AE%AE.md#identity%E6%8C%87%E4%BB%A4)
   

## 更简单调用Elephant Wallet的方法

  Elephant Wallet的开发团队提供了一个过渡页面，用于解决从PC Web或者是从微信里启动Elephant的问题。
  
  当第三方想要启动Elephant Wallet时，可以统一向过渡页面发起请求，它会对运行环境进行判断，如果是在pc web，它将显示一个二维码，用户可以打开Elephant Wallet对它扫码，即可跳转到预期的页面。
  
  如果当前是在微信中，它会显示一个提示用户使用手机浏览器打开的提示页面，当用户在微信里操作使用浏览器打开以后，手机上会自动唤起Elephant Wallet。 
  
  这样无论是App还是Web，无论是手机还是PC，都可以向Elephant Wallet发起调用。这个过渡页面对Elephant Wallet支持的所有命令都有效。
  
  以上面对Elephant调用的URL为例：
  ```
  https://elephantwallet.app/redirect/?
  appName=Hackathon&
  appTitle=Hackathon&
  autoRedirect=True&
  redirectURL=elaphant%3A%2F%2Fidentity%3FReturnUrl%3Dhttp%253A%252F%252Fbing.com%26AppID%3D7d80c7e800f5842b3b8e7ec7318189f66b7fd5b6db13bb80fbd89d2b1c444772c1d0202fea1e9cbabbf3258b3d91685484c02c2ae52d78ca39e2e54593ec81dd%26PublicKey%3D032f6347b27401dc0bced2de0ab4531e62c496841cd8e67a58c572e3018dcb72d9%26DID%3DiXzenTELVRDc712tmt2Qvbtk3KcAwV2tU8%26AppName%3DHackathon%26RequestInfo%3Delaaddress%2CEmail%2CNickname%26description%3DEApp%2520Community%26RandomNumber%3D4284432979
  ```
  更详细内容调用参数请参考下面文档：  
  
  [过渡页面参数说明](./redirect_page.md)


