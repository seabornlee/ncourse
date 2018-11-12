React 是当下最为流行的 Web 开发框架之一，尤其在开发区块链 DApp 领域非常的流行。对 Web 前端不太了解的同学上手 React 的时候会一下子感觉懵掉，因为 React 是前端工程化的产物，开发过程中涉及到非常多的工具的使用。本节中，Peter 把 React 开发环境给大家拆解一下，看看都有哪些知识点。

## React 开发环境的全貌

我们先说说开发环境的全貌。总体来讲是这样，React 开发环境本身依赖于 Nodejs ，安装和使用 Nodejs 就需要开发者对命令行有一定的了解。所以我们本节的三个关键词是：React ，Nodejs 和命令行。

先聊聊 React 本身。React ，reactjs.org 是 Facebook 公司推出的一套开发 Web App 的框架，所谓 Web App 就是一个可以运行在浏览器里的 App ，例如 taobao.com ，facebook.com ，github.com 都是 Web App 。

Nodejs 和命令行稍后我们详细点聊。除了这两个之外，成熟的 React 开发者，几乎一定会用到的工具就是 Git 版本控制工具，以及 Github.com 。不会版本控制工具，很难开发稍微大一点的项目，所以 Git 一定要学。Github.com 不仅仅是对 Git 版本控制工具的一个备份和配合，同时 Github.com 本身也是一个优秀的项目协作平台，是世界上最大的开源代码集结地。另外，React 开发者都会使用一款非常高效的编辑器，目前 Peter 个人认为最棒的是 VScode ，另外两款也很流行的就是 Vim 和 Atom 了，强烈推荐 VScode 。

总之，上手 React ，需要我们要会用 Nodejs ，命令行，Git/Github 还有 VScode 编辑器。其中 Git/Github 还有编辑器的学习可以先放放，但是 Nodejs 和命令行是绕不过去的。

## Linux/Mac 命令行

接下来聊聊命令行。

真正的开发者应该是会命令行的，而真正的命令行应该是 Unix 命令行。可以选择使用苹果的 Mac 系统，或者使用 Linux 的某个发行版，例如 Ubuntu ，这些系统都是 Unix 或者叫 Unix-Like 系统，都自带 Bash ，Bash 是最为常见的 Unix 命令行软件。

Peter 自己最早用 Ubuntu 做主力开发机，用了五六年。后来做前端多了，发现还是 Mac 系统更适合一些。Linux 系统，开发 C/C++ 这些偏底层的语言还是非常不错的，但是问题是很多软件装不上，例如 Sketch 和 PhotoShop 这些前端开发经常用的工具，另外一个就是 Linux 跟有的硬件配合好，但是跟有的硬件配合就不好，出了问题就要自己折腾，这个是很耗时间的。所以做 Web 开发推荐 Mac 。

系统有了，命令行就有了，关于命令行的学习，推荐我自己发起翻译的《快乐的 Linux 命令行》：http://billie66.github.io/TLCL/ 。上手早期，可以结合 React 实际工作流来学，不用面面俱到。学会如何用命令安装 nodejs ，如何跟 Github 通信等等常用操作也就够了。

关于命令行，我们先聊到这里。

## Nodejs

接下来进入最后一部分，聊聊 Nodejs 。主要聊的是 Nodejs 在前端开发中的作用。

首先说 Nodejs 不仅仅可以用来写服务器脚本，也可以辅助前端开发。如果我们到 nodejs.org 上看一下官网说明。就会知道 Nodejs 是一个 JS 的运行环境。以前 JS 只能运行在浏览器中，有了 Nodejs ，JS 代码就可以在机器上直接运行了。没错，Nodejs 最早设计的目的就是把它用服务器上，所以 Nodejs 本身有对服务器编程的很多专门的支持，非常适合来实现高性能服务器。但是，Nodejs 也一样可以安装在我们的开发机上，用来辅助前端开发。

React 的开发环境会依赖于 Nodejs ，主要由两个原因。首先，React 开发环境自动化程度很高，底层的自动化脚本很多都是 JS 写的，而这部分 JS 代码不是在浏览器中执行的，而是在 Nodejs 之上运行的。第二个原因是 React 开发过程中需要用 npm 来装包。软件开发早已过了自己写所有代码的时代，所以 React 开发过程中也要安装很多代码包，代码包简称”包“，英文叫 Package ，里面有可能是源码，也有可能是编译后的二进制。React 项目装包的命令是 npm 。npm 的全称是 Node Package Manager 。安装 Nodejs 之后，系统上就有了 npm 命令，可以用

```
npm install xxx
```

来安装 xxx 包了。Peter 有时候在视频中会用到 yarn 命令来装包，yarn 命令发挥的作用跟 npm 命令是一样的，安装的也是 npm 包，当然 yarn 有自己的一些独特优势。

总之，React 开发者对 Nodejs 不能太陌生。

## 总结

Peter 要介绍给各位的 React 开发环境的结构剖析，内容就是这些了。总结一下，React 的开发环境还是相对复杂的，上手之前绕不过去的两个坑就是命令行和 Nodejs ，所以建议大家学习 React 的时候，如果感觉处处碰壁，可以先单独的把命令行和 Nodejs 学习一下。
