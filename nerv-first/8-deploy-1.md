通过前面一节，我们已经拥有了一个 AppChain 账户，并且申请了代币。从本节开始来部署一个简单的智能合约到 AppChain 的测试链上。内容比较多，我们分两个部分来完成，本节是第一部分，准备工作。

## 编译

 AppChain是兼容以太坊智能合约的，所以一样都能用 Solidity 写。写完之后，会用到 Solidity 自己的编译环境进行编译，这一步可以用以太坊的智能合约相关的开发工具。

首先下载一个智能合约来练练手。官方的 DApp Demo 仓库：https://github.com/cryptape/dapp-demos/tree/develop/first-forever ，有一个 SimpleStore.sol 文件，就是一个简单的智能合约。为了防止官方项目调整，大家找不到，我自己也把文件托管到了我的仓库中：https://github.com/happypeter/NervFirst/tree/master/contract 。合约的内容暂时我们不关心，就是保存一些简单时间和留言数据。

对于大型项目，可以需要在自己的机器上安装 Solc 也就是 Solidity 编译器。但是咱们这个合约比较小，所以直接用以太坊提供的 remix 环境进行编译即可：https://remix.ethereum.org/ 。

![](https://img.haoqicat.com/2018091203.jpg)

把 SimpleStore.sol 的源码粘贴到 remix 的编辑区域，然后点右侧的 `start to compile` 进行编译。这里需要注意，有的时候需要稍微提高一下合约声明的版本号，才能编译通过。

![](https://img.haoqicat.com/2018091204.jpg)

编译的输出可以通过点 `details` 按钮得到。

这样合约就编译好了。

## 拿到字节码和 ABI

所谓合约部署到区块链，就是把编译后的内容上传到区块链上。真正需要上传的是那些内容呢？一共两个，一个是字节码，另一个就是 ABI 。

关于部署工作，目前 Nervos 还没有给出一个完善的集成环境来一键完成，所以我们来自己写代码把字节码和 ABI 两个东西部署到区块链上。参考官方的 first-forever 项目的思路：https://github.com/cryptape/dapp-demos/tree/develop/first-forever ，整个过程主要使用 Nervos.js 来完成。

deploy/compiled.js

```js
const bytecode = '...'
const abi = [...]
module.exports = {
    abi,
    bytecode
}
```

首先第一步，是把字节码和 ABI 拷贝到一个文件中保存。创建一个 compiled.js 文件，里面导出两项内容，一个是 abi ，另一个是 bytecode 也就是字节码。其中 bytecode 一项，就是 remix 最终编译结果中 `bytecode` 一项下的 `object` 那个字段的值，是一个长长的字符串。而 abi 一项就是一个数组，就直接在 remix 界面中的 `abi` 一项下，直接点 `copy` 图标，然后把拷贝到的内容粘贴到 compiled.js 文件中即可。我在 Github 上也上传了一个真实可用的版本供大家参考：https://github.com/happypeter/NervFirst/blob/master/deploy/compiled.js 。

compiled.js 有了，就相当于咱们要部署的原材料有了。注意，compiled.js 只是在部署合约的时候用一次而已，以后合约真正运行起来，这个文件就没用了。

## 添加配置文件

下一步来添加配置文件。主要就是体现两个知识点，第一点是合约部署是要缴费的，所以配置文件中要给出一个由足够余额的账户。第二点要明确的是上哪个链，我们这里就是上 Nervos AppChain 的测试链。下面来看看具体怎么做。

config.js

```js
const config = {
  chain: 'http://121.196.200.225:1337 ',
  privateKey:
    '0x5d3c73fa94c85bbcb516cb256a4e82c414255a270b5d065179a94aa0d5dc3efe'
}
module.exports = config
```

配置文件中添加了两项内容，chain 就是用来指定测试链的链接，链接在 appChain 的官方文档上可以找到：https://docs.nervos.org/nervos-appchain-docs/#/quick-start/deploy-appchain 。接下来 `privateKey` 也就是私钥这一项，是上集中我们生成的那个账户的私钥。刚才我们说，配置文件中需要账户信息，而这里为啥只给出了私钥，没有给地址？这是因为有了私钥其实就可以运算出地址了，所以地址就不用填写了。

这样配置文件就写好了。

## 总结

这一节完成了部署一个智能合约的第一部分的工作，主要就是准备了要被上传到区块链上的字节码和 ABI ，然后添加了配置文件，其中包括部署合约必不可少的两个条件，一个是有充足余额的账户，另一个是测试链的链接。部署合约后续工作，我们下个小节中继续聊。
