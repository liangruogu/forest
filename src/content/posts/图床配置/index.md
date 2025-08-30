---
title: 博客图床
published: 2025-04-27
description: 'Picgo Github 仓库 配置图床'
image: 'https://raw.githubusercontent.com/liangruogu/BlogImages/main/img/2025-8-30-1.png'
tags: ["图床"]
category: '技术'
draft: false
lang: 'zh_CN'
---

## 前由

因为有博客嘛， 而且弄在了Github Page上，仓库容量限制为1GB 所以不能放很多图片在上面

尝试过很多: 阿里云的OOS, Cloudflare, 以及一些免费图床

但是都有风险, OOS上的图片链接不能直接暴露，否则会被有心之人刷爆掉、Cloudflare同理，虽然它的免费额度比较大，但是还是有

免费图床的话就是担心跑路，所以还的是自己做一个稳定的好

## Github repo

### 创建仓库
首先创建一个仓库，仓库名任意，最好创建一个空白的ReadMe和一个img/文件夹

这样就可以有一个主分支(后面会用到)

### 申请Token

[Github](https://github.com)

1. 登陆后，点击右上角的头像
2. Settings
3. 左侧导航最下面的Developer settings
4. Personal access tokens
5. Tokens(classic)
6. Generate new token
7. Generate new token (classic)
8. 设置一下(如果不确定就选择no expiration date 然后权限都勾选上)

> 保存好Token, 后续会用到

## PicGo
[PicGo](https://github.com/Molunerfinn/PicGo/releases) 下载需要的版本,例如我现在的主机是Linux发行版(Fedora)所以可以下载通用的AppImage(后续也可以自己编译成rpm)


### 配置PicGo
1. 图床设置选择Github
2. 配置仓库名称: 用户名/仓库名称
3. 分支选择main
4. 设定Token填入你刚刚创建的
5. 在PicGo设置里勾选上上传后自动复制URL


### 测试PicGo
👌 接下来只需要拖动图片到上传区就可以上传了
![](https://raw.githubusercontent.com/liangruogu/BlogImages/main/img/%E6%88%AA%E5%9B%BE%202025-08-30%2013-28-23.png)
这个唯一的缺点就是加载速度不会很快，但是既然博客都在Github上了，加载图片应该也是轻轻松松的(笑)
