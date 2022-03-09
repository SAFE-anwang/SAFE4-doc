SafeSwap

SafeSwap是运行于SAFE4、ETH、BSC上的去中心加密货币兑换安码应用，由安码合约、网站safeswap.anwang.org、对外接口等三个部分组成，是安网生态的重要成员。  

SafeSwap前期仅在ETH、BSC运行，安网4上线后再行部署，主要功能类似于uniswap和sushiswap，规划如下：  

（1）币种兑换：  以USDT、ETH、wSAFE(Wrapped SAFE, 在ETH、BSC上的SAFE)为基础货币，初始包括wSAFE/ETH，wSAFE/USDT两个交易对，用户可自行兑换；  

（2）添加流动性：用户可自行添加ERC20币种与wSAFE、USDT、ETH的流动性，价值1:1；可从uniswap和sushiswap中导入流动性；可获得交易费用分成；  

（3）TOKEN工厂：根据名称、简称、LOGO部署ERC20合约生成新币种，同时1：1在safeswap中抵押wSAFE和新币种添加流动性；初始抵押5000个wSAFE？与等值新币种；新币种价值如何确定？

（4）流动性挖矿：带wSAFE的交易对，根据SAFE TVL和交易量比例可挖xSAFE（SafeSwap的社区代币？不确定）；  

（5）质押生息：  质押wSAFE，产出wSAFE，用部分未发放的挖矿收益给利息，利息比例应该是主节点收益率的一半；自行领取，ETH交易费用自已出；   

