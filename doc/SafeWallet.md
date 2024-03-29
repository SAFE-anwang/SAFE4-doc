2022年1月13日SafeWallet开发规划

时间周期：2022年1月-2022年9月

已知问题：  

（1）市值排名有点出入，未按照阿拉伯数字排名；  
（2）基于ETH、BNB的币种，收款交易没有显示；如果卸载重装，导入原有助记词后，基于ETH、BNB发送的交易也没有；  
（3）TOR网络连接有问题，需要能正常连接；  
（4）助记词和对应密码不应该被存贮在手机上，应该删除；保存加密后的种子即可；  
（5）chain.anwang.com被封，SAFE同步时需从chain.anwang.com上获得地址的起始区块，如果未获取成功，则SAFE同步出错；  注：最新版本已订正  
（6）安资资产转到safewallet的地址时，会被认为是1%的SAFE资产；  注：最新版本已订正  
（7）某些特殊安网交易未能被正确识别，导致某些地址不能成功同步最新数据；  注：最新版本已订正  

开发计划：  

（1）界面修改：合并交易记录界面至余额界面；新增一个蓝色主题，叫SAFE Blue(SAFE蓝)；  
（2）SAFE支持：新增SAFE主界面，SAFE线性锁仓，[SAFE跨链到ETH和BSC](https://github.com/SAFE-anwang/SAFE4-doc/blob/main/doc/wsafe.md )，后续再添加其他SAFE相关功能；  
（3）DAPP支持：新增dapp主界面，dapps商店和应用列表，把设置中的"钱包连接"也纳入这里；   
（4）DEFI强化：uniswap, pancakeswap, 1inch增加添加流动性功能；  
（5）钱包加密：钱包加密体系修改，使之更安全; 助记词和对应密码不应该被存贮在手机上，应该删除；保存加密后的种子即可；  
（6）钱包导入：可导入各种主流软件钱包和硬件钱包的助记词、私钥、二维码等等，收集大量钱包上述特征，导入时只需知道钱包名称即可；  
（7）接入SafeSwap：接入SAFE在ETH网络、BSC网络与其他币种的兑换SafeSwap（主要功能：嵌入到币种功能中，添加流动性/swap/挖矿)；  
（8）主流币锁仓：如SAFE、BTC、LTC、ETH、BNB、DASH等锁仓功能，不到时间不能取回，防止剁手；  
（9）原子兑换： SAFE与所支持的币种之间的原子兑换（暂缓，等技术方案确定再说）；  
（10）其他功能：按需添加；  

技术预研和实现：  
（1）比特币锁仓脚本、ETH锁仓合约及SDK；  
（2）SAFE跨链到ETH和BSC；  
（3）SAFESwap规划；  
（4）原子兑换技术及SDK；  

初步时间安排如下，具体时间可能会有调整，视技术预研情况而定：

（1）3-15解决SAFE同步、市值排名、eth和bnb交易记录问题；  
（2）3-30解决Tor或VPN问题。  
（3）4月底SAFE支持（SAFE线性锁仓，SAFE跨链到ETH）、DEFI强化；  
（4）5月底DAPP支持和接入safeswap；  
（5）6月底钱包加密和钱包导入；  
（6）7月底主流币锁仓；  
（7）8月底原子兑换；  

2022年6月2日SafeWallet开发规划调整：  

（1）6月新增SAFE跨链BSC，pancakeswap上兑换SAFE，ETH上支持uniswap V3兑换，官方twitter放第一页关注之后；解决新建钱包从当前区块开始；  
（2）7月新增线性锁仓、节点锁仓，新增DAPP列表；  
（4）8月新增钱包导入；  
（5）9月新增BTC、LTC、DASH等主流币锁仓；  
（6）10月-12月SafeSwap、跨链原子兑换；  

实际开发进度：  

（1）04-02解决SAFE同步、市值排名、eth和bnb交易记录问题；  
（2）06-01新增电报群、新增VPN连接（解决VPN连接稳定性、闪退等问题）、新增SAFE与SAFE ERC20互换、解决SAFE节点连接稳定性问题、解决语言问题、解决多子钱包串交易记录问题；  
（3）06-22新增首页显示安网推特内容；新增跨链到BSC；新增pancakeswap买卖SAFE。解决新建钱包数据同步从当前区块开始问题，更新btc浏览器接口；  
（4）08-05新增线性锁仓和查看锁仓记录；新增DAPP列表和Dapp与钱包连接及操作支持；解决BSC->SAFE需依赖于ETH的问题；  
（5）08-15新增safe专区增加各种实用url：safe合约，uniswap，pancakeswap，跨链浏览器，safe@coingecko,safe bep20@coingecko,safe@coinmarketcap; 新增eth接口多账号访问；   
    优化vpn服务；优化safe价格来源；优化dapp显示；解决线性锁仓时间不大于120月；   
（6）0901版本优化点:
    1、telegram：a.中文版支持；b.解决删除会话时闪退问题；
    2、线性锁仓：a.线性锁仓时概率性不成功；b.线性锁仓时交易记录显示锁仓年月日时间不对;c.锁仓交易记录排序偶现错乱
    3、交易记录：a.交易记录页面下切换到其他的app，再次进钱包时闪退;b.更换safe价格接口后的交易记录里没有显示金额;
    4、市场主页：a.统一关注下safe价格来源;b.更换市场行情下第三方接口；
    5、Pancakeswap互兑交易gas值默认改成10，以减少swap交易被机器人套利的可能性，用户可自行改回5；  
（7）0930版本:  
    1、新增助记词导入恢复钱包功能，包括市面上各种HD类钱包以及Imtoken钱包、比特派钱包等；  
    2、优化Telegram权限控制，关闭了对手机电话和通讯录的获取；  
（8）1018版本点:  
    1.新增TokenPacket钱包助记导入恢复钱包;  
    2.新增ETH私钥导入恢复钱包;  
    3.优化telegram中文版下聊天记录时间显示;  
 （9）2023.1.10 v0.28.01.10版本:  
    1. 支持btc锁仓; 
    2. btc钱包恢复;   
    3. 支持nft;  
    4. 支持Solana，ZCash、polygon等公链;  
    5. 还有些其他的功能的修改，如交易记录等; 
    
   (10) Safewallet Updates v0.28.0.1.0302:
    1. Added SAFE blue theme;
    2. Added custom URL on the Dapp page;
    3. Supported SAFE block synchronization rollback;
    4. Optimized currency management interface;
    5. Resolved losing wallets under wallet management;
    6. Modified the gas fee.

  (11) SafeWallet Updates v0.28.0.1.0330b:  
    1. Support safe<=>matic cross-chain functionality;  
    2. Support BCH, DASH, and LTC lock-up features;  
    3. Support wallet recovery with Chinese mnemonic phrases;  
    4. Resolve the issue of doubled transaction amount display;  
    5. Support DApp wallet browser to retain historical access records;  
    6. Optimize VPN on/off state management;  
    7. Optimize display effects under the Safe blue background.  

   2023年2月14日研发规划：   
   
一、v0.28.0.1.02.XX功能： 

1、支持safe区块同步回退；  
2、解决钱包管理下丢钱包问题；  
3、修正bsc下gas值默认5；  
4、增加蓝色主题叫SAFE蓝：在外观主题下增加safe蓝选项，选择后整个界面主色调变成蓝色；  
5、增加dapp页面浏览器输入，可输入自定义URL（参照其他钱包），访问前提出安全警告：您将访问第三方链接，请确保该链接安全可靠，若造成任何后果由您承担；  
6、币的选择界面：  
（1）3个SAFE币整合在一起，SAFE3主链，ERC20，BEP20，  
（2）现在币和区块链分不清楚，参考交易记录界面，有个下拉框，可以按照区块链过滤：列表出我们所有支持的区块；选择所有就是现有列表界面；  

二、v0.28.0.1.03.XX功能：  

1、SAFE跨链MATIC；  

三、v0.28.0.1.04.XX功能：  

1、主流币锁仓：如LTC、DASH、BCH等锁仓、解锁功能；
2、DEFI强化：uniswap, pancakeswap, safeswap增加添加流动性功能；分析各dapp数据，完成数据封装解析，统一展示界面，支持增加、删除流动性；
3、优化前面版本问题；

四、v0.28.0.1.05.XX功能：

1、钱包加密：钱包加密体系修改，使之更安全;
2、优化前面版本问题；
