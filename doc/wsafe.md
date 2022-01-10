SAFE跨链  

SAFE跨链是指SAFE币从SAFE主链转到ETH、BSC等其他区块链上，让用户充分享受到SAFE在DEFI中带来的更多可能性。   
我们把ETH、BSC上的SAFE称为Wrapped SAFE，简称wSAFE。   

SAFE跨链的技术方案    

1. 需要SAFE资产池即一个指定的SAFE地址，类似于wBTC的资产池，该资产池由开发团队管理，用于保存跨链到ETH或BSC的SAFE；  
   该资产池的存在，是因为需要从wSAFE转换回SAFE（如果不需要此种反向转换，则直接销毁SAFE是最好方案）。  
   虽然资产池由开发团队管理，但必须保证金额不被挪用，开发团队会在区块链浏览器上提供数据证明。  
   
2. 开发团队实施一个在线程序，监控SAFE主链和ETH或BSC主链，如发现有用户向资产池转入SAFE，即产生wSAFE发送给用户提供的ETH地址；  
   反之，监控到ETH或BSC主链的wSAFE合约中有用户销毁wSAFE，即在SAFE主链上发送同等数量给该用户提供的SAFE地址；  
   每次操作后，该程序保证：
   
            资产池中的SAFE金额 - 以SAFE计价扣除的ETH或BSC交易费用  = wSAFE@ETH + wSAFE@BSC   
      
   其中“以SAFE计价扣除的ETH或BSC交易费用“的说明如下：为方便用户使用，开发团队预先垫付ETH交易费；
   但因为ETH、BSC的交易费用太贵，只能是以当时SAFE的价格，把ETH交易费折算成SAFE，在wSAFE总额中扣除。开发团队不在此业务中挣钱，只求不亏本即可；
   
   假设SAFE价格50元，ETH价格2万元，ETH交易费400元；  
   
   举例： SAFE => wSAFE
 
   则用户转换100个SAFE为wSAFE，实际上将有92个wSAFE到账，8个SAFE作为ETH交易费用扣除；   
   转换10000个，则有9992个wSAFE到账，因而转换越多越划算；
   
   举例： wSAFE => SAFE  
   
   销毁wSAFE的ETH交易费用由用户支付了，因而当用户转换100个wSAFE为SAFE时，SAFE地址到账是100个，  
   因为SAFE主链的交易费用非常低廉，SAFE交易费用由开发团队承担。
   
   
3. 实施SAFE的ERC20合约wSAFE，wSAFE初始金额为0，其他不同接口在于：  
   - 发行出来的wSAFE总量不可能高过SAFE的流通量（2022年1月10日到达2087万）;
   - SAFE转wSAFE，用户将转账SAFE到资产池（并且附带ETH地址），调用此接口，给该ETH地址发送正确金额的wSAFE（wSAFE金额=转账SAFE金额-以SAFE计的ETH交易费），并且发出转入资产池通知；
   - wSAFE转SAFE，用户调用该接口销毁wSAFE（并且附带SAFE地址），并且发出销毁通知；


4. 具体实施：  

    SAFE跨链可通过以下两种具体方式进行：  

   - 通过中心化交易所，此种方式需要交易所的开发支持。中心化交易所向SAFE资产池转账一定数量的SAFE，其指定的ETH地址会收到同样数量的wSAFE；  
     而用户如需要兑换成wSAFE，只需要从交易所的ETH链提现wSAFE即可；反之，只需向交易所的wSAFE地址充值wSAFE，一定确认数后即可从交易所提现SAFE；  
  
   - 用户在SafeWallet上操作，需要SafeWallet开发支持。只需指定金额，即可进行双向转换；
