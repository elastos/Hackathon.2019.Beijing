## 搭建本地节点运行环境
* 本地搭建[ELA主节点](https://github.com/elastos/Elastos.ELA)，使用tagv0.3.3版本编译，配置文件如下:

```
{
  "Configuration": {
    "ActiveNet": "testnet",
    "DisableDNS": true,
    "PermanentPeers": [
      "18.205.31.224:21338",
      "3.212.133.221:21338",
      "18.207.43.194:21338",
      "35.169.223.183:21338"
    ],
    "PowConfiguration": {
      "PayToAddr": "8ZNizBf4KhhPjeJRGpox6rPcHE5Np6tFx3",
      "MinerInfo": "ELA",
      "MinTxFee": 100
    },
    "EnableRPC": true,
    "RpcConfiguration": {
      "User": "",
      "Pass": "",
      "WhiteIPList": [
        "0.0.0.0"
      ]
    }
  }
}
```

* 本地搭建[ETH侧链节点](https://github.com/elastos/Elastos.ELA.SideChain.ETH)，使用dev分支编译，进入`build/bin`目录，使用命令`./geth  --rpcaddr "127.0.0.1" --rpccorsdomain "*" --rpc --rpcapi "personal,db,eth,net,web3,txpool,miner" --testnetc`连接testnet节点


* 使用dev分支编译[ela-cli](https://github.com/elastos/Elastos.ELA.Client)，配置文件 `cli-config.json` 修改如下:

```
{
  "LogToFile":false,
  "Host": "127.0.0.1:10016",
  "DepositAddress":"EEmfgnrDLQmFPBJiWvsyYGV2jzLQY58J6G"
}
```


## 将测试币ela充值到eth侧链
* 创建充值交易: `./ela-cli wallet -t create --deposit eth_address(充值以太坊地址) --amount recharge_value(充值金额) --fee recharge_fee(充值消耗手续费)`
* 签名交易: `./ela-cli wallet -t sign --file to_be_signed.txn -p yourpassword(密码)`
* 发送交易: `./ela-cli wallet -t send --file ready_to_send.txn`


## 使用网页钱包部署合约
* 登录[myetherwallet](https://www.myetherwallet.com)钱包
* 右上角网络点击change按钮
* 点击添加自定义网络/节点
* ETH Node Name随便填写，选择ETH，URL填写测试服务器地址(http://52.205.30.16/)，port填写rpc端口(8545)
* 使用配置合约来部署合约，合约交互来调用合约

