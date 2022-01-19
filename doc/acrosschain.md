跨链资产

跨链资产是指BTC、ETH、LTC、DASH等其他区块链的资产转移到SAFE主链上，在SAFE主链进行各种交易和应用后，还能转回至各自区块链；有中心化和去中心化两种实现方式：

- 中心化实现方式

  建立一个跨链资产网关SafeGate，处理双向跨链交易，管理各种跨链资产的资产池。以BTC跨链为例，跨入的处理流程如下：  
  - 用户转移BTC到SafeGate指定的BTC地址，并且附带SAFE地址；
  - SafeGate监测到收到用户转来的BTC；
  - SafeGate调用系统跨链安码生成对应金额的wBTC发送给用户SAFE地址；  
  
  跨出的处理流程如下：  
  - 用户通过系统跨链安码销毁wBTC且提供BTC地址；
  - SafeGate监测到用户的销毁wBTC金额；
  - SafeGate从BTC资产池发送BTC给用户BTC地址；
