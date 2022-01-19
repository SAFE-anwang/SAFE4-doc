跨链资产

跨链资产(Across Chain Asset, ACA)是指BTC、ETH、LTC、DASH等其他区块链的资产转移到SAFE主链上，在SAFE主链进行各种交易和应用后，还能转回至各自区块链；有中心化和去中心化两种实现方式：

- 中心化实现方式

所需组件：
  - SafeAcrossGate资产跨链网关，处理双向跨链交易；
  - SafeOriginPool原生资产池，保存各种区块链的原生资产(Original Chain Asset, OCA)的资产池，基本上每种资产池由几个地址组成；
  - SafeAcrossCode系统跨链安码，生成、销毁各种跨链资产，要与资产池金额一致；
  
  以BTC跨链为例，跨入的处理流程如下：
  
  - 用户转移BTC到SafeAcrossGate指定的BTC地址，并且附带SAFE地址；
  - SafeAcrossGate监测到收到用户转来的BTC，等待一定确认数；
  - SafeAcrossGate调用SafeAcrossCode生成对应金额的wBTC发送给用户SAFE地址；  
  
  跨出的处理流程如下：  
  - 用户通过SafeAcrossCode销毁wBTC且提供BTC地址；
  - SafeAcrossGate监测到用户的销毁wBTC金额，等待一定确认数；
  - SafeAcrossGate从SafeOriginPool发送BTC给用户BTC地址；
