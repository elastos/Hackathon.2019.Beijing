## 生成AppId
  第三可以向elephant wallet发起调用请求，但它必须拥有一个合法的DID和Appid。其中DID代表开发者身份，而Appid是应用的唯一标识。
  
  Appid的生成规则是：用DID主私钥对Appname进行签名，生成的签名字符串即是Appid。开发者可以自己生成，也可以通过下面的页面生成，它的源码在github上，可以离线运行。
  
  [<生成DID和Appid>](https://zuohuahua.github.io/Elastos.Tools.Creator.Capsule)
  
  这里提供一个已经生成好的，测试用的DID和Appid，开发者可以用于测试使用，最终发布版本需要使用上面的方式生成自己的Appid。
  ```
  DID：iXzenTELVRDc712tmt2Qvbtk3KcAwV2tU8
  PublicKey：032f6347b27401dc0bced2de0ab4531e62c496841cd8e67a58c572e3018dcb72d9
  App Name：Hackathon
  Appid：7d80c7e800f5842b3b8e7ec7318189f66b7fd5b6db13bb80fbd89d2b1c444772c1d0202fea1e9cbabbf3258b3d91685484c02c2ae52d78ca39e2e54593ec81dd
  ```
