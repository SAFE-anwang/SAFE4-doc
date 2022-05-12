SAFE跨链  

SAFE跨链是指SAFE币从SAFE主链转到ETH、BSC等其他区块链上，让用户充分享受到SAFE在DEFI中带来的更多可能性。   
我们把ETH、BSC上的SAFE称为Wrapped SAFE，简称wSAFE。   

SAFE跨链的技术方案    

1. SAFE资产池，即一个指定的SAFE地址如 XmkTAzN38tsNjEdXwuHkRL75U3Q3uuwRey ，类似于wBTC的资产池，该资产池由开发团队管理，用于保存跨链到ETH或BSC的SAFE；  
   该资产池的存在，是因为需要从wSAFE转换回SAFE，如果不需要此种反向转换，则直接销毁SAFE是最好方案。  
   虽然资产池由开发团队管理，但必须保证金额不被挪用，开发团队会在区块链浏览器上提供数据证明，即：  
   
   ```
   资产池地址中的金额  >=（ETH中wSAFE合约中的金额 + BSC中wSAFE合约中的金额）
   ```
   
2. SAFE跨链网关，功能如下：  
   - 监控SAFE主链，如发现有用户向资产池转入SAFE并且附带ETH地址，经过5个确认后，产生新的wSAFE发送给用户提供的ETH地址；  
   - 监控到ETH或BSC主链的wSAFE合约，当发现wSAFE合约中有用户销毁wSAFE回转到安网主链操作时，经过10个确认后，监控程序将通过SAFE主链从资产池地址发送同等数量SAFE给该用户提供的SAFE地址；  

3. 部署于ETH和BSC的ERC20合约wSAFE：    
   - wSAFE初始金额为0，用户从SAFE主链转SAFE到wSAFE时才会产生wSAFE；  
   - 发行出来的wSAFE总量不可能高过SAFE的流通量（2022年4月达到2100万）;
   - 接口safe2eth：此接口仅由合约创建者才能调用，SAFE转wSAFE，用户转账SAFE到资产池（并且附带ETH地址），之后由SAFE跨链网关才能调用此接口，给该ETH地址发送正确金额的wSAFE，并且发出转入资产池通知；
   - 接口eth2safe：wSAFE转SAFE，任何用户可调用该接口销毁wSAFE（并且附带SAFE地址），并且发出销毁通知；

跨链流程：

1. SAFE => wSAFE ，用户转账SAFE到资产池，且附带ETH地址或BSC地址；  

   - 用户使用SAFE PC钱包转账：
     - 目标地址填写基金会公布的资产池地址，金额填写你需要的金额，但不小于10个SAFE，否则有可能不够ETH交易费；  
     - 在备注中添加 网络 + ETH地址，示例如下：
     
        ```
        eth:0x88AeEd4D8FECfA0cE274C967254eaD0fA84c7EC6, 即向ETH网络转。   
        bsc:0x88AeEd4D8FECfA0cE274C967254eaD0fA84c7EC6, 则向BSC网络转，不过目前还不支持BSC网络。  
        safe4:XrLUNPwrNgBnRgRmKK49GxvqE9fXzYbu3R, 则向SAFE4网络转，不过SAFE4网络目前还未上线。  
        后续将支持更多网络  
        ```
        
     - 点击发送后，即在你提供的ETH地址中等待wSAFE。
     
   - 用户使用SafeWallet转账：（4-5月份上线，敬请期待）
     - 选择 SAFE=>wSAFE, 选择网络如ETH、BSC、SAFE4等，不过目前仅支持向ETH网络转账；
     - 只需输入转账金额，不小于10个SAFE；
     - 点击发送后待钱包中ETH地址出现wSAFE；

   - wSAFE金额问题：  
     用户收到的wSAFE金额如下所示：
     
      ```
      用户收到的wSAFE金额 - 以SAFE计价扣除的ETH交易费用  = wSAFE
      ```  
      
     用户收到的wSAFE金额会少于发送的SAFE金额，是因为SAFE跨链网关向用户ETH地址发送wSAFE需要消耗ETH，ETH的交易费用贵是众所周知的；  
     为方便用户使用，开发团队先垫付ETH交易费，但从SAFE中扣除相应的费用，以维持SAFE跨链业务；
     
     以SAFE计价扣除的ETHC交易费用，以当时SAFE、ETH的USDT价格，把ETH交易费折算成SAFE，从用户发送的SAFE中扣除；   
     
     开发团队不在此业务中挣钱，只求不亏本即可；
     
   - 举例： SAFE => wSAFE  
 
   用户转换100个SAFE为wSAFE，SAFE费用为0.4,因而实际上将有99.6个wSAFE到账，0.4个SAFE作为以SAFE计的ETH交易费用扣除；    
   转换10000个，则有9999.4个wSAFE到账，因而转换越多越划算；  
   
   该实时费用的接口放在safewallet.anwang.com上：safe_fee就是扣除的费用  
   
   测试网以SAFE计的ETH费用：https://safewallet.anwang.com/v1/gate/testnet    
   主网以SAFE计的ETH费用：  https://safewallet.anwang.com/v1/gate/mainnet  
   
   具体计算规则见第3点。
   
2. wSAFE => SAFE ，用户销毁wSAFE附带SAFE地址，SAFE跨链网关发送SAFE到指定SAFE地址；    

   用户通过safewallet来转账：（4-5月份上线，敬请期待）  
   - 选择wSAFE=>SAFE, 选择网络如ETH、BSC、SAFE4等，不过目前仅支持从ETH网络转账回SAFE主链；  
   - 只需输入转账金额，不小于10个wSAFE；  
   - 点击发送后待钱包中SAFE地址出现SAFE；  
   - 用户支付ETH交易费用，但wSAFE金额不会减少，因为SAFE主链的交易费用很低廉，由开发团队支付；  
   
   举例： wSAFE => SAFE  
   
   当用户转换100个wSAFE为SAFE时，SAFE地址到账是100个，  
   
3. 以SAFE计价扣除的ETH交易费用计算方法
   
   以SAFE计价扣除的ETH或BSC交易费用的计算方法：  
   
   （1）先获取ETH网络的交易费用 eth_fee，如0.0015；  
   （2）再从ZB上获取ETH和SAFE的USDT价格比 rate，如ETH：3000，SAFE：41；ETH:SAFE=73.17:1   
   （3）计算 safe_fee = eth_fee * rate * 1.1 = 0.1207317 ，小数点保留4位，0.1207317  => 0.1207。  
       0.1207就是以SAFE计价扣除的ETH交易费用。乘以1.1的原因是SAFE网关会提高ETH交易费10%，以便ETH交易能够快速确认。
   
   以上述标准来计算以SAFE计的ETH交易费用。 此费用每30秒计算一次，因而可能会有所滞后。
   
   每次操作后，跨链网关保证：
   
   ```
   资产池中的SAFE金额 - 以SAFE计价扣除的ETH或BSC交易费用  >= wSAFE@ETH + wSAFE@BSC   
   ```

4. 具体实施：  

    SAFE跨链可通过以下方式进行：  

   - 通过中心化交易所，此种方式需要交易所的开发支持。中心化交易所向SAFE资产池转账一定数量的SAFE，其指定的ETH地址会收到同样数量的wSAFE；  
     而用户如需要兑换成wSAFE，只需要从交易所的ETH链提现wSAFE即可；反之，只需向交易所的wSAFE地址充值wSAFE，一定确认数后即可从交易所提现SAFE；  
  
   - 用户在SafeWallet上操作，需要SafeWallet开发支持，只需指定金额，即可进行双向转换；

   - SAFE PC钱包可以从 SAFE => wSAFE ;  
