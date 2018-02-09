+++
title = "Skycoin BBS开发 更新＃1"
tags = [
    "Development",
    "BBS",
    "CXO",
]
bounty = 3
date = "2017-08-05"
categories = [
    "Development Updates",
]
description = "Skycoin BBS 的第一个开发更新。"
+++

## An Introduction

BBS(Bulletin Board System) 代表电子布告栏系统。虽然传统的BBS系统不再被广泛使用，BBS现在现代成为了社会服务的代表。


Skycoin BBS是skycoin生态系统的第一个Web应用程序之一。 Skycoin试图彻底改变互联网，使其去中心化，并默认地使用加密协议。

Skycoin BBS 的根基是一个名为CXO（Skycoin生态系统的一部分），一个点对点，自我复制的网络数据库。它具有像Golang 对象一样，不可变的树结构。所有对象都通过自己的哈希值一起定义图式引用。每棵树都有一个树根对象和对公/私钥对签名。要更新树，树根有增量的版本称为“序列”。这种设计实现快速，高效的带宽数据复制。


## 数据结构

Skycoin BBS（0.2版本 - 正在开发）的数据结构包含不同的板，主题和帖子。板和帖子都可以给与正／负评。
这是大概CXO树的样子：

![](https://raw.githubusercontent.com/skycoin/bbs/v0.2/doc/cxo_data_structure.jpg)

这是一个简化图。

所有提交的对象（主题，帖子和投票），都可以通过提交用户的公钥提供的签名和进行验证。

每根包含用于表示／存储每一个板的数据。 Board－Page包含“内容”; 板的本身，主题和帖子。主题是由“主题”对象的哈希所反映，而帖子同样被“帖子”本身的哈希所翻译。因此，帖子和主题一经提交就不能能被修改。

Thread－Votes－Pages，Post－Votes－Pages存储了投票的内容。该Vote－Page的“引用（ref）”字段包含相关内容的哈希值。在“投票”字段存储了扳票中的指定的内容。 Vote－Pages是由BBS节点到存储的结构，所以能够迅速的获得“投票概览”。

投票和内容是分开存储以减少因为每一次投票而改变的树的节点数目。它还允许通过投票的编译器得到更容易票数据操作。

## 发布

目前，我们只发布了一个稳定的Skycoin BBS。目前的功能是十分基本的，但CXO数据结构比上面所指的更复杂。内容增加和投票产生使得那个根在每个动作之上以倍数增长。

BBS（目前正在开发）的0.2版，不仅提高了性能和代码的清晰度，同时也将实现以下新的特点：

* 改进内容加载 - 我们将利用客户端和服务器之间的WebSocket连接（S）的，允许实时更新，更有效的内容加载。
* 内容投票/观看改善 - 无论从用户的角度来看，或是实际表现和流动性。垃圾邮件的报告也将陆续展开。
* 权限 - 现在可以设置权限限制谁可以执行有一些操作（如提交内容/投票权）。屏蔽／拉黑用户的功能也将会推出。

## Participate

欢迎加入我们的[电报小组](https://t.me/skycoinbbs).
已得到最新Skycoin BBS的开发消息。 
Skycoin BBS是開源的。源代碼可以遊覽[這裏](https://github.com/skycoin/bbs)。需要注意的是0.2版本的開發是在“V0.2”分支。
