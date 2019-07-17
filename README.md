# Hackathon.2019.Beijing

## 赛题:基于区块链技术开发App
必须使用区块链技术作为主要功能之一，欢迎使用亦来云技术方案，特别是亦来云智能合约侧链，这条侧链完全兼容ETH合约，可以使用Solid编程。

## 评分规则

- 完成度（5分），参赛项目功能流程是否闭环、完整，用户体验是否顺畅。
- 创新性（5分），能结合区块链技术方案对互联网已有业务流程进行创新改造，或者结合区块链特性创造出全新的业务领域和应用场景。
- 附加分（10分），使用到下述技术方案可获得附加分。
  - 使用亦来云智能合约侧链开发合约。（5分）（注：亦来云智能合约侧链与ETH完全兼容）
  - 使用ELASTOS DID作为用户账号登录App。（2分）
  - 使用ELA支付。（1分）
  - 使用ELASTOS ID侧链存证数据。（1分）
  - 使用ELASTOS DID为证书、证明签名，实现第三方证明业务场景。（1分）

## 奖项

按得分排名，取前三名。

* 第1名，一等奖 人民币15000元。
* 第2名，二等奖 人民币10000元。
* 第3名，三等奖 人民币5000元。

所有选手均可获得以下权益：

  - 辅助选手获得项目孵化支持；
  - 参赛项目获得亦来云生态支持；
  - 参赛选手直接加入亦来云核心团队的工作机会
  

## 技术支持微信群

<img src="./2E2B050C-CEBE-4E62-9B5B-1421B16F7F06.jpeg" width = "200" height = "200" alt="wechat group" align=center />

仅限黑客松相关选手和技术支持加入。


## 比赛相关技术指南

### 使用亦来云eth侧链进行智能合约编程

- [eth侧链开发环境](./eth_sidechain_env.md)
- [eth侧链编程示例](./eth_sample.md)

### 使用ela did作为用户身份

- [生成开发者DID和注册Appid](./generate_appid.md)
- [通过Elephant Wallet进行第三方登录](./how_to_login_with_did.md)
- [H5 Sample](./how_to_login_with_did.html)
- [更多文档参考](https://github.com/elastos/Elastos.Developer.Doc/blob/master/CN/4.%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5/4.Elephant%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5%E5%8D%8F%E8%AE%AE.md)

### 使用ela did链存证数据

- [使用代理服务存证数据到区块链](https://github.com/elastos/Hackathon.2019.Beijing/blob/master/使用代理服务存证数据到区块链.md)
- [Java Sample](https://github.com/elastos/Elastos.SDK.DIDClient.Java/blob/master/sample/src/main/java/sample/com/upChain/UpChainSample.java)
- [更多文档参考](https://did-client-java-api.readthedocs.io/en/latest/)

### 使用ela did代表用户身份进行签名授权和开具证明文件

- [生成开发者DID和注册Appid](./generate_appid.md)
- [通过Elephant Wallet开具第三方证明](https://github.com/elastos/Elastos.Developer.Doc/blob/master/CN/4.%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5/4.Elephant%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5%E5%8D%8F%E8%AE%AE.md#sign%E6%8C%87%E4%BB%A4)
- [更多文档参考](https://github.com/elastos/Elastos.Developer.Doc/blob/master/CN/4.%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5/4.Elephant%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5%E5%8D%8F%E8%AE%AE.md)

### 使用ela进行支付

- [生成开发者DID和注册Appid](./generate_appid.md)
- [通过Elephant Wallet进行ELA快速支付](./how_to_pay_ela.md)
- [H5 Sample](./how_to_pay_ela.html)
- [更多文档参考](https://github.com/elastos/Elastos.Developer.Doc/blob/master/CN/4.%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5/4.Elephant%E9%92%B1%E5%8C%85%E5%AF%B9%E6%8E%A5%E5%8D%8F%E8%AE%AE.md)

## 使用carrier进行通信

- [使用Elastos Carrier实现点对点通信](./carrier/get-started-for-android.md)
- [Android Sample](./carrier/demo.md)
- [更多文档参考](https://github.com/elastos/Elastos.NET.Carrier.Native.SDK/blob/master/README.md)
