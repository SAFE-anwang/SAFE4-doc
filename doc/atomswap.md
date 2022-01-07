原子兑换  

&emsp;&emsp;原子兑换发生在SAFE和其他区块链的加密货币之间，如BTC、BCH、ETH和ERC20代币、LTC、BNB和BEP20代币、DASH等，这就意味着SAFE钱包需要以RPC或SPV支持其他区块链的钱包。  
    
&emsp;&emsp;假设有A、B两方，A有SAFE，需要BTC；B有BTC，要交换SAFE；他们可以把拥有的币种转到中心化交易所，然后直接兑换成BTC或SAFE，或者卖成USDT再购买所需币种；如果他们想直接在钱包中以去中心化的方式完成彼此兑换，可以遵照如下步骤进行：

1.  AB双方准备好币种和金额
    - A确保SAFE钱包有足够金额的SAFE；
    - B把BTC转入SAFE钱包控制的BTC钱包或地址。以SAFE钱包连接Bitcoin Core钱包的RPC接口，确保Bitcoin Core钱包中有正确金额的BTC；或者在SAFE钱包中按照BIP39/BIP32标准生成BTC地址，把BTC转入该地址；

2.  订单撮合
    - A在SAFE钱包的原子兑换功能中发布一个买单，花费x个SAFE，以价格v购买BTC（或B发布一个卖单，以价格v卖出BTC，BTC数量y）, 该买(卖)单发布在SAFE网络上；
    - B在SAFE钱包的原子兑换功能中接受该买单，表明同意该买单的价格和金额，即发送一个全网交易；在此之前SAFE钱包会检查BTC金额是否充足；
    - A的买单被B锁定，AB双方开始兑换过程；

3. 兑换过程
    - A在SAFE主链上发布一个新交易，将SAFE锁在时间锁和HASH锁中；需要一定时间如3天之后A才能拿回SAFE；
    - B在BTC链上发布一个新交易，把BTC锁在时间锁和HASH锁中，同样需要3天时间才能拿回BTC；
