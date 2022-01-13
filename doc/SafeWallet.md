已知问题：  

（1）市值排名有点出入，未按照阿拉伯数字排名；  
（2）基于ETH、BNB的币种，收款交易没有显示；如果卸载重装，导入原有助记词后，基于ETH、BNB发送的交易也没有；  
（3）TOR网络连接有问题，需要能正常连接；  
（4）助记词和对应密码不应该被存贮在手机上，应该删除；保存加密后的种子即可；  
（5）chain.anwang.com被封，SAFE同步时需从chain.anwang.com上获得地址的起始区块，如果未获取成功，则SAFE同步出错；  

后续开发：  

（1）界面修改：合并交易记录界面至余额界面；新增一个蓝色主题，叫SAFE Blue(SAFE蓝)；  
（2）SAFE支持：新增SAFE主界面，SAFE线性锁仓，SAFE跨链到ETH和BSC（https://github.com/SAFE-anwang/SAFE4/blob/main/doc/wsafe.md ），后续会再添加；  
（3）DAPP支持：新增dapp主界面，dapps商店和应用列表，可参考imtoken，把设置中的钱包连接也纳入这里；   
（4）DEFI强化：uniswap, pancakeswap, 1inch增加添加流动性功能；  
（5）钱包加密：钱包加密体系修改，使之更安全，类似于imtoken；https://github.com/consenlabs/token-core-android/  
（6）钱包导入：可导入各种主流软件钱包和硬件钱包的助记词、私钥、二维码等等，通过钱包名称，助记词、密码、BIP32路径导入；收集大量钱包上述特征（https://walletsrecovery.org/ ），只需对应到钱包名称即可；  
（7）接入SafeSwap：接入SAFE在ETH网络、BSC网络与其他币种的兑换SafeSwap（主要功能：嵌入到币种功能中，添加流动性/swap/挖矿)；  
（8）主流币锁仓：如SAFE、BTC、LTC、ETH、BNB、DASH等锁仓功能，不到时间不能取回，防止剁手；  
（9）原子兑换： SAFE与所支持的币种之间的原子兑换（暂缓，等技术方案确定再说）；  
（10）其他功能：按需协商添加；  
