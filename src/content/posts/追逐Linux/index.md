---
title: 追逐Linux
published: 2025-07-15
description: '逃离Windows的理想'
image: 'https://raw.githubusercontent.com/liangruogu/BlogImages/main/img/%E3%80%90%E5%93%B2%E9%A3%8E%E5%A3%81%E7%BA%B8%E3%80%91BSOD-Windows.png'
tags: ["OS", "Linux", "Fedora"]
category: 'Fedora'
draft: false
lang: 'zh_CN'
---

## 前因
> 程序员就应该在终端里畅游, 而不是在一卡一卡的windows菜单栏和卡半天的Powershell里饱受折磨

开发环境和生产环境存在差异，导致环境配置和开发流程变得难受, Windows中始终无法使用原生的shell命令,就算WSL2已经很能用了，但是宿主机和wsl之间的文件传输，以及vscode远程连接这两个之间的差距始终无法消除。让我一直无比向往Linux

### 第一次尝试
第一次尝试摆脱Windows是在24年底，我迷恋上了[Arch](https://archlinux.org)

恰好我有一台树莓派4B, 于是我开始尝试将系统烧录到TF卡里，其中涉及到了很多初始化系统的命令，都是按照Youtube博主或者B站UP煮操作的，但是无一幸免，没有一个安装成功的，现在回想起来应该是分盘或者HDMI转Type-C有问题。Arch官方也不再支持ARM架构


### 寒假双系统
买不起笔记本，只能冒险(一定风险)刷双系统，但是在一块固态硬盘上玩实在是不会。

于是偷偷买了一块1T的固态，然后把Arch刷在上面。过程挺顺利的，基本第一次就成功了。只是当时无法完全理解什么是grub,以及BIOS, 我当时可以说是非常兴奋😆, 桌面环境选择了一个非常酷炫的[Hyprland](https://hypr.land),加上我是一名vim用户，可谓是如鱼得水


美中不足的是当时的我并没有过硬的开发技能，所以只能在上面干激动(笑)
![](https://raw.githubusercontent.com/liangruogu/BlogImages/main/img/1bafc8f7edddb688551ae3eb27eeef59.jpg)

### NixOS
其中我还尝试过[NixOS](https://nixos.org/), 它的整体设计都很棒，而且我特别喜欢他的Logo![](https://raw.githubusercontent.com/liangruogu/BlogImages/main/img/%E6%88%AA%E5%9B%BE%202025-08-30%2013-56-37.png)
它的设计理念大概是使用一份配置文件来控制系统中的所有，这样只需要维护一份文件就可以完美复现环境，可移植能力超级强.😊

但可惜的是官方的文档太难入门，我就是看不懂，才退坑的😭

就这样过了一段时间，在同一台笔记本上面使用双系统还是太麻烦，所以我开始盯上了迷你主机

### 迷你主机
到这一步的时候就很纠结了,因为花大几千买一个性能远不足现在笔记本的迷你主机

似乎只有空间和颜值上占据优势。。。🤔

最后扛不住Windows的折磨(笑), 还是拿下了零刻的Ser8 8745HS 准系统
因为给笔记本换了两根16G的内存条，卖掉不划算，所以给它装上啦，最后挑了一根很好的固态给它(听说固态好可以让开机变得很快), 确实快，基本上几秒就打开了.

![](https://raw.githubusercontent.com/liangruogu/BlogImages/main/img/10dec2dd60db59eedb4500c0a85e2c95.jpg)
