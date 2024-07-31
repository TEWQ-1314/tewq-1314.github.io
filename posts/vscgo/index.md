# VSCode在 Windows&amp;Linux下配置Go语言开发环境

###VSC 简介

VSCode 的全称是 Visual Studio Code，是微软于 2015 年发布的一款免费开源的现代化轻量级代码编辑器。

### 下载VSC


VsCode 的官网为：[VSC 官网](https://code.visualstudio.com)进入官网如下：
![](https://i.imgtg.com/2023/07/25/OhlGJs.jpg)
VsCode 文件大概大小在 *60M,* 下载完成之后，根据提示进行选择和安装即可。

// 如果是 32 位处理器，请下载 Windows×32，Linux 同理。这里推荐下载稳定版

### 安装VSC

Windows 端为 msi 或 exe 安装包，相信大家都能搞定

Linux 根据系统包管理器选择，如果不明白可以去 Google 相应的方法，比如 deb 包使用
``` bash
dpkg -i xxxxxx.deb
```

### 设置语言为中文（英文用户忽略）

下载完  VsCode，有些人不习惯用英文版，这时候我们要选择汉化语言包。其设置如下：

#### 修改配置文件

使用快捷键 Ctrl &#43; Shift &#43; P  或者选择 VsCode 菜单栏 View 点击 Command Palette，进入一个查找框。然后在框里搜索 【configure】会显示如下情况 
![](https://i.imgtg.com/2023/07/25/OhlQlK.png)

刚刚安装完，是仅有 *”locale”:”en”*，这时我们将其替换成 zh-CN，然后保存重启。

#### 下载中文包

如果我们在完成第一步的情况下，当前语言还是英文，则说明我们安装包不携带汉化包， 需要我们自己去下载。

按快捷键 Ctrl &#43; Shift &#43; X 进入第三包插件下载，搜索【chinese】，如下：（Linux 需要根据软件设置一步一步找到这个选项）
![](https://i.imgtg.com/2023/07/25/Ohl0Ta.png)
然后重启便汉化完成。这时我们可以在计算机硬盘或优盘上创建一个专门存放 Go 代码的文件夹，这样方便管理。建议路径为纯英文

### 下载 Go 语言包

Golang 官网地址为：https://golang.org 或者 https://golang.google.cn 以及 Go 语言中文网

选择你所需要的 Go 语言版本， 推荐下载 *.zip* 压缩包 *. 或者.msi* 也可以。（ 注意对应的

windows/linux 以及系统架构）

![](https://i.imgtg.com/2023/07/25/OhldcN.jpg)
![](https://i.imgtg.com/2023/07/25/OhlVMC.jpg)


这里以 *.zip* 为例，下载之后解压得到一个 go 文件夹

![](https://i.imgtg.com/2023/07/25/Oh9rdS.png)

此时，我们进去 DOS 检查 go 是否安装成功。（Linux 直接跳到下一步）Win&#43;R 输入 cmd 回车        进        去        命        令        行

![](https://i.imgtg.com/2023/07/25/OhlfLi.png)

在我们解压缩后的 go 文件夹里有一个 bin 子文件夹，进去 bin 文件夹后复制当前路径，如

F:/go/bin

![](https://i.imgtg.com/2023/07/25/Ohl2Px.png)

复制之后回到命令行，输入 cd 粘贴目录如 
``` bash
cd   F:/go/bin 
```
然后回车。

![](https://i.imgtg.com/2023/07/25/OhllXX.png)

输入 go 文件所在盘盘符加冒号，如 f: 然后回车

![](https://i.imgtg.com/2023/07/25/Ohl6lj.png)

输入 dir 回车，此时会显示几个文件，和 bin 文件夹里的一样
![](https://i.imgtg.com/2023/07/25/Ohljzt.png)
然后，输入
``` bash
go version 
```
然后回车，如果成功输出，则说明安装成功。

![](https://i.imgtg.com/2023/07/25/OhlIcY.png)
### 配置环境变量（msi 安装的用户应该可以跳过）

我们需要配置三个基础环境变量，GOROOT，Path，GOPATH 1）主屏幕点击计算机，单击鼠标左键，点击属性。
![](https://i.imgtg.com/2023/07/25/OhlCOv.jpg)
点击高级系统设置，点击环境变量
![](https://i.imgtg.com/2023/07/25/OhlwNq.png)

这时会出现两个变量类型，一个是 Administration  用户变量，另一个是系统变量。
我们在系统变量下面，点击新建
![](https://i.imgtg.com/2023/07/25/Oh9MLc.png)

变量名为 GOROOT 变量值填你的 go 解压之后的文件所在目录，如 F:/go 点击确定，第一个变量就配置好了。

![](https://i.imgtg.com/2023/07/25/Oh9Our.png)

然后，Path 环境变量就不用新建，一遍电脑里都有，在系统变量里找到 Path，选中后点编辑，输入
``` bash
;%GOROOT%\bin
```
![](https://i.imgtg.com/2023/07/25/Oh9TTI.png)
点击确定。
系统变量，点击新建，变量名为 GOPATH 变量值为你将来存放 go 程序的目录，比如我在 F 盘里新建一个名为 Go project 的文件夹来存放我的 go 代码。那么变量值就为 Goproject 文件夹所在目录 F:/Goproject 点击确定，这样就配置好了。
![](https://i.imgtg.com/2023/07/25/Oh9UvD.png)
现在检测是否配置成功，Win&#43;R，输入 cmd 进去命令行，输入
``` bash
go version
```
回车，如果有输出，则配置成功。

![](https://i.imgtg.com/2023/07/25/Oh9kO6.png)

Linux 端直接进入命令行，编辑 */etc/profile* 文件
``` bash
vim /etc/profile
```
将上面提到的目录直接写入例如
``` bash
export GOROOT=/usr/local/go
export GOPATH=/home/bruce/goProject export PATH=$PATH:$GOROOT/bin
export PATH=$PATH:$GOPATH/bin
```
目录根据实际情况更改，然后保存文件并执行
``` bash
source /etc/profile
```
更新

然后同样执行
``` bash
go version
```
来检查

这时，我们就可以用 VSC 写出 golang 的 hello，world 了。

### 输出 Hello，World

打开 VSCode，点击左上角文件→打开文件夹，我们在配置 GOPATH 变量时，不是创 建了一个名为 Goproject 的文件夹吗，此时就打开那个文件夹。可以在 Goproject 下创建子文件夹。也可以直接存放代码，不过这样不便于管理。
![](https://i.imgtg.com/2023/07/25/Oh9xNP.jpg)
用 VScode 打开文件夹后，我们新建一个 hello.go 文件。然后再输入 hello，world 的代码。输完后 F5 点击保存
（可以安装 go 插件并在 vsc 内调试，但也局限于 vsc)

在确保代码正确的前提下，如果代码有问题他会提示错误。我们 Win&#43;R，输入 cmd 然后回车进去命令提示行，输入 cd hello.go 的目录，比如你刚才的 hello.go 放在 F 盘的 Goproject     里 ， 那 么 你 就 输 入

``` bash
cd    F:/Goproject
```
然 后 回车。
![](https://i.imgtg.com/2023/07/25/Oh9zEb.png)
![](https://i.imgtg.com/2023/07/25/Oh9iFg.png)
输入 
``` bash
dir 
```
回车，（Linux 是 *ls)* 查看目录，里面就有我们这的 hello.go 文件
![](https://i.imgtg.com/2023/07/25/OhlY7L.png)
输入

``` bash
go build hello.go
```
然后回车（通用）
![](https://i.imgtg.com/2023/07/25/Oh919s.png)
Linux 建议使用

``` bash
go run
```
直接输出


再输入 dir，这时是不是生成了一个 hello.exe 文件（Linux 下可能是一个可执行文件）
![](https://i.imgtg.com/2023/07/25/Oh9KaN.png)
输入 hello.exe 然后回车，这时，如果正确，他就会输出 hello,world Linux 输入
``` bash
chmod &#43;x hello
.hello
```
恭喜，你写出了震惊世界的 hello，world


---

> 作者: [Haoran Dong](https://github.com/TEWQ-1314)  
> URL: https://www.depth.su/posts/vscgo/  

