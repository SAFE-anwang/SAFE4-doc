## SAFE跨链ETH/BSC使用教程v0.2

SAFE跨链是指SAFE币从SAFE主链转到ETH/BSC区块链上，且可回转至SAFE主链，让用户充分享受到SAFE在DEFI中带来的更多可能性，我们把ETH/BSC上的SAFE称为Wrapped SAFE，简称wSAFE（仅为了区分，但在合约中体现的币名称还是SAFE）。

### 0.重要信息

|     | eth  | bsc | matic |
|  ----  | ----  | ---- |---- |
|  操作名称  | safe2eth/eth2safe | safe2bsc/bsc2safe | safe2matic/matic2safe |
| 资产池地址  | [Xnr78kmFtZBWKypYeyDLaaQRLf2EoMSgMV](https://chain.anwang.com/address/Xnr78kmFtZBWKypYeyDLaaQRLf2EoMSgMV) |[XdyjRkZpyDdPD3uJAUC3MzJSoCtEZincFf](https://chain.anwang.com/address/XdyjRkZpyDdPD3uJAUC3MzJSoCtEZincFf) | [XuPmDoaNb6rbNywefkTbESHXiYqNpYvaPU](https://chain.anwang.com/address/XuPmDoaNb6rbNywefkTbESHXiYqNpYvaPU) |
| SAFE合约地址 | [0xEE9c1Ea4DCF0AAf4Ff2D78B6fF83AA69797B65Eb](https://etherscan.io/token/0xee9c1ea4dcf0aaf4ff2d78b6ff83aa69797b65eb) |[0x4d7fa587ec8e50bd0e9cd837cb4da796f47218a1](https://bscscan.com/token/0x4d7fa587ec8e50bd0e9cd837cb4da796f47218a1)  | [0xb7Dd19490951339fE65E341Df6eC5f7f93FF2779](https://polygonscan.com/token/0xb7dd19490951339fe65e341df6ec5f7f93ff2779) |
| 确认数 | 10/12 | 10/12 | 10/12 |
| 跨链费用 | 以SAFE计 | 无需费用 | 无需费用 |

 
- 以SAFE计的ETH网络费用实时获取接口：  https://safewallet.anwang.com/v1/gate/mainnet  
- 跨链记录查询：https://anwang.com/assetgate.html   
- SAFE跨链支持钱包SafeWallet永久下载链接：  https://anwang.com/download/safewallet-latest.apk   

![SafeWallet永久下载链接](https://github.com/SAFE-anwang/SAFE4-doc/blob/main/img/1.jpg)
  
  
### 1.safe2eth/safe2bsc/safe2matic
  
![safe2eth](https://github.com/SAFE-anwang/SAFE4-doc/blob/main/img/2.jpg)  
  
SAFE转换为wSAFE的流程如上图所示,详细说明如下：  
#### 1.1 用户向上述资产池地址，发送一定金额的SAFE并且附带ETH/BSC/MATIC地址  
说明：  
（1）发送方式：通过SAFE的官方PC钱包或者safewallet（第一页下载链接）；  
SAFE官方PC钱包的发送方式如下图所示：  
  
![safe2eth](https://github.com/SAFE-anwang/SAFE4-doc/blob/main/img/3.jpg)  
  
（2）资产池地址：必须填写ETH/BSC/MATIC mainnet主网对应的SAFE资产池地址，该地址由基金会控制，仅用于SAFE跨链，SAFE留存金额需大于等于wSAFE合约中的SAFE金额；ETH/BSC/MATIC测试网与ETH/BSC/MATIC主网对应的资产池地址不同；  

  如果发向ETH网络，资产池地址必须是Xnr78kmFtZBWKypYeyDLaaQRLf2EoMSgMV，备注中前4个字节必须是“eth:”,后面跟ETH地址；  
  如果发向BSC网络，资产池地址必须是XdyjRkZpyDdPD3uJAUC3MzJSoCtEZincFf，备注中前4个字节必须是“bsc:”,后面跟BSC地址；  
  如果发向BSC网络，资产池地址必须是XuPmDoaNb6rbNywefkTbESHXiYqNpYvaPU，备注中前6个字节必须是“matic:”,后面跟MATIC地址；

（3）发送金额：一般最小金额不能小于2个SAFE，否则可能不够ETH网络费用，此种情况下，会等待至ETH网络费用下降至小于发送金额才会发送，不予以退还；  

（4）ETH/BSC/MATIC地址：必须附带ETH/BSC/MATIC地址，且其格式要按照上述格式，如果不能检测出ETH/BSC/MATIC地址，则不会列入发送队列，也不予以退还；

（5）不能使用交易所提现的方式，不能使用不支持SAFE跨链的钱包转SAFE给资产池地址，这种情况下不会附带用户ETH/BSC/MATIC地址，损失自负；  

#### 1.2 SAFE跨链网关通过ETH/BSC/MATIC网络向用户ETH/BSC/MATIC地址发送wSAFE  
说明：  
（1）SAFE跨链网关收到SAFE达到10个确认数之后，才会向对应的ETH/BSC/MATIC地址发送wSAFE；ETH/BSC/MATIC主网  safe2eth/safe2bsc/safe2matic操作要达到10个确认，eth2safe/bsc2safe/matic2safe操作要达到12个确认，目的是为了保证资产安全。  

（2）扣除以SAFE计的ETH/BSC/MATIC网络费，剩余部分是SAFE跨链网关将向用户ETH地址发送的金额；以SAFE计的ETH网络费用的计算方法如下：  

- 先获取ETH网络的网络费用 eth_fee，如0.0015；  
- 再从ZB上获取ETH和SAFE的USDT价格比 rate，如ETH：3000，SAFE：41；ETH:SAFE=73.17:1  
- 计算 safe_fee = eth_fee * rate * 1.1 = 0.1207317 ，小数点保留4位，0.1207317 => 0.1207。 0.1207就是以SAFE计价扣除的ETH网络费用。乘以1.1的原因是SAFE网关会提高ETH网络费10%，以便ETH交易能够快速确认。  
- 此费用每30秒计算一次，因而可能会有所滞后。  
- 获得以SAFE计的ETH网络费用的最简单方法是,在浏览器中打开费用获取接口：https://safewallet.anwang.com/v1/gate/mainnet  
返回的json文本中第一个safe_fee后面就是以SAFE计的ETH网络费。  

（3）用户发送safe2eth请求时的ETH网络费用，与10个确认（5分钟）后跨链网关发送wSAFE时所花费的ETH真实网络费可能会有差别，以实际扣除为准。  
（4）BSC和MATIC网络交易费用比较低，BNB/MATIC价格也不高，因而在BSC/MATIC网络的费用由开发团队代付，safe2bsc/safe2matic不扣除用户的SAFE；  
（5）当发送wSAFE交易后，2小时内不确认，跨链网关会重发；  
（6）可在上述重要信息的主网wSAFE合约地址中查看用户交易是否发出；  

#### 1.3 用户收到wSAFE  
说明：  
（1）当SAFE跨链网关以高于10%网络费的交易发送wSAFE时，确认速度应该很快；  
（2）用户可使用任何支持ETH/BSC/MATIC钱包的ETH/BSC/MATIC地址收到wSAFE,safewallet内置对wSAFE合约的支持，其他钱包必须导入ETH/BSC/MATIC主网的SAFE合约地址才能看到收到的wSAFE;  

### 2. eth2safe/bsc2safe/matic2safe  
  
![eth2safe](https://github.com/SAFE-anwang/SAFE4-doc/blob/main/img/4.jpg)  
  
#### 2.1用户通过合约销毁wSAFE且带SAFE地址  
说明：  
（1）wSAFE合约提供eth2safe/bsc2safe/matic2safe接口，其功能是记录用户的SAFE地址，并且销毁用户指定金额的wSAFE；  
（2）用户只能销毁自己的wSAFE，销毁wSAFE事件会通知给SAFE跨链网关；  
（3）销毁金额：ETH/BSC/MATIC网络费用由用户自己支付，因而如果金额太小，ETH网络费用会远大于SAFE金额的价值，因而SAFE金额多一些更合适；  
（4）操作方法：safewallet已经发布，第一页下载链接下载；  
 
#### 2.2跨链网关通过SAFE网络发送SAFE给用户  
说明：  
（1）跨链网关使用资产池中的SAFE发送给用户，且零钱也同样回归到资产池地址，方便用户验证金额；  
（2）跨链网关在eth2safe/bsc2safe/matic2safe操作中，不收取任何费用，SAFE网络费也由跨链网关支付；  
（3）需要等ETH/BSC/MATIC销毁wSAFE的交易到达12个确认后，才会发送SAFE；  

#### 2.3用户收到SAFE  
说明：  
（1）用户使用SAFE官方PC钱包、safewallet钱包、交易所SAFE充值地址、其他支持SAFE的钱包都可以收到SAFE；  

### 附录：ETH ropsten和BSC testnet测试网重要信息：  (<font color="#660000">目前以下测试网已经关闭，直接使用正式网即可<font>)  

- ETH ropsten测试网仅用于测试目的，其中的wSAFE没任何价值，普通用户不用理会，开发者可以使用它来开发和测试SAFE相关程序；  
- ETH ropsten测试对应的SAFE资产池地址： [XiY8mw8XXxfkfrgAwgVUs7qQW7vGGFLByx](https://chain.anwang.com/address/XiY8mw8XXxfkfrgAwgVUs7qQW7vGGFLByx)  
- ETH ropsten测试wSAFE合约地址： [0x32885f2FaF83AeeE39e2cfE7F302e3BB884869f4](https://etherscan.io/token/0x32885f2FaF83AeeE39e2cfE7F302e3BB884869f4) 
- ETH ropsten safe2eth:3个确认，eth2safe:3个确认；不扣SAFE计的ETH网络费用  
- ETH ropsten以SAFE计的ETH费用：https://safewallet.anwang.com/v1/gate/testnet  
  
- BSC testnet测试网重要信息：  
- BSC testnet测试网对应的SAFE资产池地址： [Xm3DvW7ZpmCYtyhtPSu5iYQknpofseVxaF](https://chain.anwang.com/address/Xm3DvW7ZpmCYtyhtPSu5iYQknpofseVxaF)  
- BSC testnet测试wSAFE合约地址：   [0xa3D8077c3A447049164e60294C892e5E4C7f3aD2](https://bscscan.com/token/0xa3D8077c3A447049164e60294C892e5E4C7f3aD2)
- BSC testnet safe2eth:3个确认，eth2safe:3个确认；不扣SAFE计的ETH网络费  
- BSC testnet以SAFE计的ETH费用：https://safewallet.anwang.com/v1/gate/testnet    
  
  
