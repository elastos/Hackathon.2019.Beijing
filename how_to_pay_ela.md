# 使用ELA快捷支付

  第三方应用可以通过唤起Elephant Wallet发起支付调用。
  
  **调用示例：**
  
  ```
  elaphant://elapay?
AppID=cc053c61afc22dda9a309e96943c1734&
AppName=RedPacket&
Description=red&
PublicKey=028971D6DA990971ABF7E8338FA1A81E1342D0E0FD8C4D2A4DF68F776CA66EA0B1&
OrderID=354199ds9213k1f&
CoinName=ELA&
Amount=1.234&
ReceivingAddress=EXRNP8Pm3KQR7EeLXFGRtfLdkBaeZsMLyy&
CallbackUrl=http%3A%2F%2Flocalhost%3A8081%2Fpacket%2Fgrab%2F1509893100600982-0&
  ```
  
  
  
  具体操作如下：

## Step1 生成AppId

  请参考下面的文档来生成Appid

  [<生成DID和Appid>](./generate_appid.md)


## Step2 向Elephant Wallet发起调用
  Elephant Wallet通过拦截特殊scheme前缀的URL来接收调用请求；通过回调第三方指定的URL来返回结果。
  
  示例：
  ```
  elaphant://elapay?
AppID=cc053c61afc22dda9a309e96943c1734&
AppName=RedPacket&
Description=red&
PublicKey=028971D6DA990971ABF7E8338FA1A81E1342D0E0FD8C4D2A4DF68F776CA66EA0B1&
OrderID=354199ds9213k1f&
CoinName=ELA&
Amount=1.234&
ReceivingAddress=EXRNP8Pm3KQR7EeLXFGRtfLdkBaeZsMLyy&
CallbackUrl=http%3A%2F%2Flocalhost%3A8081%2Fpacket%2Fgrab%2F1509893100600982-0&
  ```
  
  可以在 https://www.qr-code-generator.com/ 生成二维码，并使用Elephant Wallet扫码，识别成功以后，它将在手机上会自动打开浏览器并跳转到设置的Return URL：https://bing.com
  
  你可以将上面的例子拷贝到手机浏览器中打开，也会自动唤起Elephant Wallet，结果是一样的。
  

## Step3 处理Elephant Wallet返回内容

  Elephant将返回支付交易的 TXID 

  具体请参考协议文档。
  
  [<Elephant Wallet Elapay Command>](https://github.com/elastos/Elastos.Developer.Doc/blob/master/CN/4.%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5/4.Elephant%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5%E5%8D%8F%E8%AE%AE.md#elapay%E6%8C%87%E4%BB%A4)
  
  **查询TXID有效性**
  https://node1.elaphant.app/api/1/tx/12ac39936b0d277b47b9e0bc17d76d51ecebd47d0fc2554405f250cfa0d95507

## 更简单调用Elephant Wallet的方法

  Elephant Wallet的开发团队提供了一个过渡页面，用于解决从PC Web或者是从微信里启动Elephant的问题。
  
  当第三方想要启动Elephant Wallet时，可以统一向过渡页面发起请求，它会对运行环境进行判断，如果是在pc web，它将显示一个二维码，用户可以打开Elephant Wallet对它扫码，即可跳转到预期的页面。
  
  如果当前是在微信中，它会显示一个提示用户使用手机浏览器打开的提示页面，当用户在微信里操作使用浏览器打开以后，手机上会自动唤起Elephant Wallet。 
  
  这样无论是App还是Web，无论是手机还是PC，都可以向Elephant Wallet发起调用。这个过渡页面对Elephant Wallet支持的所有命令都有效。
  
  更详细内容调用参数请参考下面文档：  
  
  [<过渡页面参数说明>](./redirect_page.md)




