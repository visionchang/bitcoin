# 比特币相关知识汇总

### 基本知识点脑图    
- [BTC.pdf](https://github.com/john-zh/bitcoin/blob/master/BTC.pdf)    

### 相关资源
- [区块链演示 demo](https://anders.com/blockchain/blockchain.html)
- [区块浏览器](https://www.blockchain.com/explorer)
- [UTXO 模型与账户模型详解](https://draveness.me/utxo-account-models)
- [私钥生成公钥过程演示](http://bi3d.com)
- [助记词生成演示](https://iancoleman.io/bip39/#english)
- [js 库](https://github.com/bitcoinjs/bitcoinjs-lib)

### 钱包方案

- [bip32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)    
  定义 **Hierarchical Deterministic wallet (简称 "HD Wallet")**，是一个系统可以从单一个 **seed 产生一树状结构储存多组 keypairs（私钥和公钥）**。好处是可以方便的备份、转移到其他相容装置（因为都只需要 seed），以及分层的权限控制等。
- [bip39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)    
  将 **seed** 用方便记忆和书写的单字表示。一般由 **12 个单字**组成，称为 mnemonic code(phrase)，中文称为助记词或助记码。例如：
  `
  rose rocket invest real refuse margin festival danger anger border idle brown
  `
- [bip44](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki)    
  基于 BIP32 的系统，赋予树状结构中的各层特殊的意义。让同一个 seed 可以支援**多币种、多帐户**等。各层定义如下：
    `
    m / purpose' / coin_type' / account' / change / address_index
    `
  其中的 `purporse'` 固定是 `44'`，代表使用 BIP44。而 `coin_type'` 用来表示不同币种，例如 Bitcoin 就是` 0'`，Ethereum 是 `60'`。
- [slip44](https://github.com/satoshilabs/slips/blob/master/slip-0044.md)    
  基于`bip44`，目前已注册的`coin_type'`
- [bip141](https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki)    
  - 定义 **隔离见证（segwit）**。隔离见证就是把 **脚本签名（scriptSig）** 信息从 **基本结构（base block）* 里拿出来，放在一个新的数据结构当中。做验证工作的节点和矿工也会验证这个新的数据结构里的脚本签名，以确保交易是有效的。    
  - 隔离见证可以缓解现在比特币拥堵问题，另外闪电网络也基于更多用户使用隔离见证地址。    
  - 隔离见证地址一般以3开头例如：`3JvL6Ymt8MVWiCNHC7oWU6nLeHNJKLZGLN`
