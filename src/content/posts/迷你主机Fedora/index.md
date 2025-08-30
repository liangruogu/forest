---
title: 迷你主机Fedora
published: 2025-08-30
description: '拥抱Fedora'
image: 'https://raw.githubusercontent.com/liangruogu/BlogImages/main/img/%E3%80%90%E5%93%B2%E9%A3%8E%E5%A3%81%E7%BA%B8%E3%80%91%E5%B1%B1%E8%84%89%E8%BF%9C%E6%99%AF-%E5%BC%80%E9%98%94%E5%A4%A9%E5%9C%B0.png'
tags: ["OS", "Linux", "Fedora"]
category: 'Fedora'
draft: false
lang: 'zh_CN'
---

# 前因
[Arch](https://archlinux.org)确实很美好, 但是它属于极客

我们需要几乎从零开始配置一切,包括分盘，输入法，网络，蓝牙，终端，几乎能想到的一切都需要我们自己来，作为一个爱折腾但是没这么能折腾的开发者，我还是觉得Arch目前并不适合我，而且滚动更新的操作系统会让我们在每一次更新系统的时候提心吊胆

经过很长一段时间的思考和纠结，我最后选择了[Fedora](https://fedoraproject.org/)

他真的很稳定，而且安装过程愉快，都是可视化的界面
![](https://raw.githubusercontent.com/liangruogu/BlogImages/main/img/%E6%88%AA%E5%9B%BE%202025-08-30%2014-32-35.png)

# Fedora
目前唯一的遗憾就是语言没有选择英文，导致我的终端现在还有中文的: "图片", "视频" 那些

其实Fedora并不是开始就是专门为开发者定制的，很多东西都是很通用的，所以我们还需要一步步配置他

所有的配置先放在这里: [config](https://gitee.com/ceyes/TerminalConfig)


## Kitty
首先是最重要的终端，几乎每一天打开电脑第一个看到的就是终端
1. 主题
```bash
kitty + kitten themes
```

2. 字体
```text
font_family      family="JetBrainsMonoNL Nerd Font Mono"
font_size        14
```

3. Tab
```text
tab_bar_edge            bottom
tab_bar_style           powerline
tab_powerline_style     slanted
tab_bar_margin_width    0.0
```

然后在Fedora的gnome桌面我绑定了 **alt + r** 快速打开kitty

> 美中不足的是并不能通过kitty设置圆角在gnome里面，只能通过gnome的一个插件实现

## Clash
不配置clash，我们的linux几乎没有用武之地
::github{repo="wnlen/clash-for-linux"}

## Fcitx5
配置中文输入法, 这个的教程很多，不再赘述

## Wofi
然后是软件的快速启动，我选择的是wofi,具体的不说了，直接看配置就好.
![](https://raw.githubusercontent.com/liangruogu/BlogImages/main/img/7a369d4ab259d61d399ecee950baec96.jpg)

## Zed
因为Vscode在Windows和Linux中的一些设置不同，导致我在windows配好的vim快捷键在Fedora里并不生效

而且UI不是很好看在linux里.

所以我选择zed作为我的编辑器,原因有:
1. 原生支持vim(作为一名vim重度用户)
2. Rust编写，速度十分快(不喜欢用Rust写东西，但是喜欢用Rust写的东西, 笑)
3. zed并不支持windows(所以可以成为我买迷你主机的一个原因，xixi)

:::Note
Zed中并没有<leader>键的概念，所有的都是用快捷键完成的。例如我可以设置```ctrl-e```打开左边的文件目录, 而不是nvim中的 ```<leader> e```
:::


## Firfox
> 听说Linux选择Firfox是因为经过了特殊的性能优化
我主要用到了两个东西:

### 插件
**Vimium**

这个插件可以说是 vim综合征患者的解药, 而且vim用户可以无痛适配
1. ?可以打开键盘说明 (刚开始可以看这个)
2. f/F可以标记出所有的link，按下对应字母(不必大写)后可以跳转
3. o/O可以打开一个新的🔗
4. b/B可以打开一个新的书签/收藏
5. jhkl可以移动视图
6. J/K可以左右跳转Tab
7. x/X可以关闭Tab和恢复被关闭的Tab
8. G滚动到底部, gg返回顶部
9. z配合l/h左右移动
10. d/u可以快速上下滚动
11. /可以搜索


**沉浸式翻译**
没得说，确实好用，但是用多了也烦


**油猴脚本**
浏览器必备

### 设置
**垂直标签栏**

常规设置里面我打开了浏览器的垂直标签页，这样可以在我用平铺的时候不占据上方太多空间

因为我有时候会开很多Tab导致上方很拥挤，但是垂直就很清晰了
![](https://raw.githubusercontent.com/liangruogu/BlogImages/main/img/51d49d6b18f78f4976285667cd7a828d.jpg)

**网络**

常规设置最下面有一个网络设置，可以写一个```pac```文件来配置你什么时候需要使用代理

```pac
function FindProxyForURL(url, host) {

    // 如果访问的是本地地址或特定的内网地址，直接连接
    if (isInNet(host, "10.0.0.0", "255.0.0.0") ||
        isInNet(host, "172.16.0.0", "255.240.0.0") ||
        isInNet(host, "192.168.0.0", "255.255.0.0") ||
        isInNet(host, "127.0.0.0", "255.255.0.0") ||
        isInNet(host, "169.254.0.0", "255.255.0.0") ||
        host == "localhost") {
        return "DIRECT";
    }

    // 对于 GitHub、YouTube 或其他海外服务器的访问使用代理
    // 可以添加更多的目标网站域名或正则表达式来匹配这些域名
    if (shExpMatch(host, "*.github.com") ||
        shExpMatch(host, "*.youtube.com") ||
        shExpMatch(host, "*.github.io") ||
        shExpMatch(host, "*.deepl.com") ||
        shExpMatch(host, "*.chatgpt.com") ||
        shExpMatch(host, "*.google.com")) {
        return "PROXY 127.0.0.1:7890"; // 注意替换成你的代理服务器地址和端口
    }

    // 默认操作，对于其他网站直接连接
    return "DIRECT";
}
```

**其他**

像什么主题，下载位置之类的就看自己喜好设置吧


### Music

因为我用酷狗，但是官方并没有提供第三方的Linux安装包

在先后尝试了洛雪、Youtube Music、网页之后，发现了一个用Electron写的酷狗第三方客户端
::github{repo="iAJue/MoeKoeMusic"}

RPM打包的流程大概如下:
1. 克隆仓库
```bash
git clone https://github.com/iAJue/MoeKoeMusic.git
cd MoeKoeMusic
```

2. 下载依赖
```bash
npm run install-all
```

3. Web(Optional)
```bash
npm run dev
```

3. 打包
需要提前下载好对应的打包软件
```bash
npm run electron:build -- --linux --target rpm
```

4. 下载
```bash
sudo dnf install xxxx.rpm
```

:::Note[PS]
说实话，这个安装包真的大到我有点不情愿. 立志使用[Tarui](https://tauri.app/)重写它的后端
:::

## 桌面

桌面底部的Dock栏是Gnome的一个插件
```bash
sudo dnf install gnome-tweak-tool gnome-extensions-app
```

除此之外我还设置了很多快捷键来达到纯键盘流(伪装版)
1. 使用```alt+l/h```左右移动桌面(我真的很喜欢这个gnome的多工作台)
2. ```alt+num```快速制定工作台
3. ```alt+shift+l/h```移动窗口到左右工作台
4. ```alt+num+l/h```同上
5. ```alt+d```关闭窗口
6. ```alt+f```打开wofi快速选择应用打开
7. ```alt+l```熄屏

这样子就可以很大程度上的用gnome模拟Hyprland了

---
:::Note[IMPORTANT]
对了，我还有一个特别喜欢的点: **Fedora的开始界面可以选择桌面环境!!**
:::
在进入时右下角的设置按钮可以选择Hyprland还是Gnome


# 总结

大概的配置就差不多啦, 用vim写中文博客还是太费劲了，要不停的切换shift 😭

Fedora的中文资料真的不多，我也希望可以写更多的资料出来帮助大家，自己也可以在忘记的时候回过来看看.
