# 后台部署说明

本项目后台主要由FISCO BCOS区块链网络及其组件， Webase管理平台及其组件构成。 具体的部署说明及步骤如下：

## 一、FISCO BCOS 区块链网络部署说明
本项目采用FISCO BCOS v3.11.0版本作为区块链底层，搭建单群组4节点链。

FISCO BCOS是由深圳市金融区块链发展促进会（以下简称“金链盟”）开源工作组牵头研发的金融级、国产安全可控的区块链底层平台。作为最早开源的国产联盟链底层平台之一，FISCO BCOS于2017年面向全球开源。

具体部署说明请参考：[FISCO BCOS AIR 部署说明] (https://fisco-bcos-doc.readthedocs.io/zh-cn/latest/docs/tutorial/air/build_chain.html)

## 二、FISCO BCOS Truora预言机部署说明
Truora是一个基于FISCO BCOS平台的预言机服务，支持FISCO BCOS2.x和3.x版本。

Truora通过在链下运行的Java服务，监听链上预言机合约事件，发起链下相关的资源访问和计算任务，并将结果返回到链上预言机合约，供链上使用。

具体部署说明请参考：[FISCO BCOS Truora预言机 部署说明] (https://truora.readthedocs.io/zh-cn/main/deploy.html)

## 三、Webase管理平台部署说明
WeBASE（WeBank Blockchain Application Software Extension） 是在区块链应用和FISCO-BCOS节点之间搭建的一套通用组件。围绕交易、合约、密钥管理，数据，可视化管理来设计各个模块，开发者可以根据业务所需，选择子系统进行部署。

本项目采用Webase v3.0作为节点管理平台，各中间件的版本如下：

Webase Node manager: v3.1.1

Webase Web: v3.1.1

Webase Front:v3.1.1

Webase Signature:v3.1.1

具体部署说明请参考：[Webase部署说明] (https://webasedoc.readthedocs.io/zh-cn/latest/docs/WeBASE/install.html)

## 四、Web3工具部署调用合约相关说明
# 1、开启Web3相关配置
在节点目录下，找到配置项config.ini，修改相关配置如下：

```
[web3_rpc]
    enable=false
    listen_ip=0.0.0.0
    listen_port=8545
    thread_count=16 
```

在FISCO BCOS节点控制台下，输入以下指令，开启Balance功能及其预编译功能

```
setSystemConfigByKey feature_balance 1
setSystemConfigByKey feature_balance_precompiled 1
```

在FISCO BCOS节点控制台下，使用链管理员账户，对测试账户充值足够的balance，以使用相关功能
```
addBalance 钱包地址 充值数量 充值单位
```
# 2、使用MetaMask向FISCO BCOS发送请求
