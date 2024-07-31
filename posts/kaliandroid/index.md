# 如何在Android设备上安装Kali Linux系统(不ROOT)

本文是通过在Android上构建Linux Arm64系统版本实现，所以仅对Android设备有效，因为Android是基于Linux开源的，所以可以安装Linux发行版。
准备工作  

      Termux，Play商店或[ZeroTermux](https://od.ixcmstudio.cn/repository/main/ZeroTermux/)代替
      VNC Viewer ,Play商店
      Android手机，不用ROOT
      20G空余内存(最低10G),4G以上运行内存
      流畅的网络环境
本教程以Kali Linux为例，至于其他Linux发行版，感兴趣的朋友可以上网查查. 
## 官方版本
### 更新Termux
打开Termux，输入。
``` bash
pkg update
pkg upgrade
```
![](https://i.imgtg.com/2023/07/25/OhYkOL.jpg)
更新软件包. 

### 下载脚本
下载wget(下载工具)，使用
``` bash
apt install wget
```
![](https://i.imgtg.com/2023/07/25/OhYxNi.jpg)
如果下载过程中有询问就输入y然后回车

Kali Linux Android官方的下载指令是
``` bash
wget -O install-nethunter-termux https://offs.ec/2MceZWr
```

等待它下载完我们会得到一个叫install-nethunter-termux的脚本
### 执行脚本
我们输入
``` bash
 chmod &#43;x install-nethunter-termux
```
把它转换成可执行文件，然后 输入
``` bash
./install-nethunter-termux
```
然后它会询问，我们输入y然后回车.之后会出现这么个界面，输入y之后回车等待下载完成（要有耐心，和一个流畅的网络，中途可能会下载失败，我们只需要重新开始就行了）
### 下载镜像
他会自动执行下载，等待它下载完成，下载期间请勿退出应用，这一步非常重要！！！！
完成之后你只需要输入其中一个就能启动kali linux
### 启动
nethunter （缩写：nh）开启 kali命令行，注意开启的是普通权限的命令行

nethunte -r （缩写：nh -r）开启的是管理员root的命令行
### 使用VNC连接桌面
现在运行图形画界面,首先输入nh -r，因为Nethunter默认安装了图形画界面，所以我们只需要通过kex passwd设置密码，然后输入kex开启VNC服务。
注意我们要记住这里的  RFB PORT 我这里为5902（先记着，待会有用） 有些人可能不一样，也许是5901
然后打开VNC Viewer，点击右下角＋号，然后Address输入刚才的RFB PORT，:5902 然后name随便起，点击Create
![](https://i.imgtg.com/2023/07/25/OhYzLX.jpg)
然后其他设置就像图上这样就行了，View only一定要关掉！然后输入刚才设置的密码就行了。如何具体设置和使用，网上也有教程的，这里就不详细讲了。到处kali系统就安装好了，如何有需要的朋友，也可以使用apt install kali-linux-everything来安装完整系统，前提是内存充足

进去kali桌面后，VNC提供了键盘，鼠标等，详细使用请上网查.

## 第三方脚本（推荐）
Tmoe是一个很好的linux安装脚本而且有很多辅助功能，基本都是傻瓜式安装，但是有很多坑
首先项目地址如下:
``` bash
https://gitee.com/mo2/linux/blob/master/share/doc/zh/lite.md
```
这是Moe大佬写的脚本，可以方便地让我们在安卓上部署linux环境的工具。其功能相当丰富，可以一键安装linux发行版及图形环境(包括KDE等重量级环境!!!)，此外包含了很多工具，主要都是一键下载，里面集成了局域网音频传递工具下载(可以让你体验到有声的vnc)，zsh终端下载等等。此外，它是图形化TUI，还是比较方便新人的。
那么请按以下教程来安装和使用它。
第一请设置termux，给予访问存储权限。
然后输入以下命令
``` bash
bash -c &#34;$(curl -Lv gitee.com/mo2/linux/raw/master/debian.sh)&#34;
```
他会开始自动下载依赖与工具。下载很快，几秒钟就好了，然后就会进入图形界面了。应该不需要过多介绍了，请记住一个原则，不懂如何操作就直接一路enter下去，部分地方需要你输入y(尤其是换源时)。建议语言选择第三项简体中文(部分内容仍为繁体。。。)此外建议选择切换为北外源。

Tmoe拥有更高的自由度，你可以随意更换桌面系统，更换VNC方式等等，还集成了很多有用的工具


---

> 作者: [Haoran Dong](https://github.com/TEWQ-1314)  
> URL: https://www.depth.su/posts/kaliandroid/  

