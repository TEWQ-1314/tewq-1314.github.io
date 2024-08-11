# 在安卓手机上利用Git搭建博客 (完整)



  ##  简介
本文将使用ZeroTermux＋GitHub ＋ Hexo搭建博客 
  ### ZeroTermux
  [Termux](https://termux.dev/)是一个Android终端仿真器和Linux环境应用程序，直接工作，无需根目录或设置。一个最小的基本系统被自动安装-额外的软件包可以使用APT软件包管理器来使用。不需要root，运行于内部存储（不在SD卡上). ZeroTermux是Termux的整合版，内置了许多有用的工具
  
特性：

安全：使用 OpenSSH 的 ssh 客户端访问远程服务器。在一个开源解决方案中，Termux 将标准包与精确的终端仿真结合
在 Bash、FISH 或 Zsh 和 Nano、Emacs 或 Vim 之间选择。GREP 通过你的短信收件箱。使用 cURL 访问 API 端点，并使用 rsync 在远程服务器上存储联系人列表的备份  

自定义：通过从 Debian 和 UbuntuGNU/Linux 中知道的 APT 包管理系统安装你想要的东西  

移植性：Termux 中提供的软件包与 Mac 和 Linux 上的软件包相同
最新版本的 Perl、Python、Ruby 和 Node.js 都是可用的  

扩大规模：连接蓝牙键盘，并将设备连接到外部显示器，如果需要，Termux 支持键盘快捷键，并有完整的鼠标支持  

可修补的：通过使用 Clang 编译 C 文件进行开发，并使用 CMake 和 pkg-config 构建自己的项目。如果陷入困境并需要调试，GDB 和 strace 都是可用的  
  
来自[开源中国](https://www.oschina.net/p/termux?hmsr=aladdin1e1#:~:text=%E7%89%B9%E6%80%A7%EF%BC%9A,strace%20%E9%83%BD%E6%98%AF%E5%8F%AF%E7%94%A8%E7%9A%84)    

[官方下载地址](https://github.com/termux/termux-app#f-droid) [ZeroTermux](https://github.com/hanxinhao000/ZeroTermux)
  ### Github
[GitHub](https://github.com)是一个面向开源及私有软件项目的托管平台，因为只支持Git作为唯一的版本库格式进行托管，故名GitHub。GitHub拥有1亿以上的开发人员，400万以上组织机构和3.3亿以上资料库
  ### Hexo
  [Hexo](https://hexo.io) was originally created and maintained by Tommy Chen in 2012. Since then, it has helped thousands of people to build their dream website/blog.
## 下载相关软件包
### 更新
使用
 ``` bash
apt update
```
 ``` bash
apt ugrade
```
 更新软件包
###  换源
 如果你在国内，建议先更换成国内源，更容易避免很多麻烦
#### 法一
可以直接执行以下命令
``` bash
sed -i &#39;s@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main@&#39; $PREFIX/etc/apt/sources.list

sed -i &#39;s@^\(deb.*games stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/game-packages-24 games stable@&#39; $PREFIX/etc/apt/sources.list.d/game.list

sed -i &#39;s@^\(deb.*science stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/science-packages-24 science stable@&#39; $PREFIX/etc/apt/sources.list.d/science.list

pkg update
```
#### 法二
手动修改配置文件
请使用内置或安装在 Termux 里的文本编辑器，例如 vi / vim / nano 等直接编辑源文件，不要使用 RE 管理器等其他具有 ROOT 权限的外部 APP 来修改 Termux 的文件

编辑 
 ``` bash
$PREFIX/etc/apt/sources.list
```
修改为如下内容
 ``` bash
# The termux repository mirror from TUNA:
deb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main
 ```
编辑
 ``` bash
 $PREFIX/etc/apt/sources.list.d/science.list 
 ```
修改为如下内容
 ``` bash
# The termux repository mirror from TUNA:
deb https://mirrors.tuna.tsinghua.edu.cn/termux/science-packages-24 science stable
```
编辑 
 ``` bash
$PREFIX/etc/apt/sources.list.d/game.list 
```
修改为如下内容
 ``` bash
# The termux repository mirror from TUNA:
deb https://mirrors.tuna.tsinghua.edu.cn/termux/game-packages-24 games stable
```
####  法三
查看当前源列表
``` bash
apt sources
```
//使用清华大学的源
``` bash
pkg install tsinghua.sources
tsinghua.sources
```
//使用中科大的源
``` bash
pkg install ustc.sources
ustc.sources
```
//使用阿里云的源
``` bash
pkg install aliyun.sources
aliyun.sources
```

在ZeroTermux中，我们使用
 ``` bash
pkg install 包名
```
来进行安装，例如我们会用到的
 ``` bash
pkg install vim
```
 ``` bash
pkg install git
```
 ``` bash
pkg install openssh
```
## 登录GitHub并建立博客仓库
参考文章[Github Page](https://pages.github.com/)

## 将仓库连接到本地
参考文章[How to Edit and Upload Code on Local Device to Github](https://www.depth.su/2023/07/25/2/)  

这一步不知道是否可以省略，大家有兴趣可以试着跳过这一步，看后来部署时是否会报错，欢迎评论区留言

## 安装Hexo
### 安装 Node JS
因为Hexo使用的是npm的仓库，所以需要先安装Node JS
``` bash
pkg install nodejs

```
### 换源（大陆用户）
``` bash
npm config set registry https://registry.npm.taobao.org
```
### 更新
``` bash
npm upgrade -g
```

检查是否有新版本，并执行相应的更新命令（它会提示你如何更新）  
例如
![](https://pic.imgdb.cn/item/64d2ee7d1ddac507ccbdf1b3.jpg)

``` bash
npm install -g npm@9.8.1
```
### 正式安装
 ``` bash
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```
我这里网络不好有一些报错，不过最后还是完成了安装，这时我们可以通过
``` bash
http://localhost:4000/
```
来查看是否安装成功
![](https://pic.imgdb.cn/item/64d2ef8a1ddac507ccc01257.jpg)
## 设置主题
Hexo有许多好看实用的[主题](https://hexo.io/themes/)，有时间的朋友可以花时间慢慢探索，这里以[Aomori](https://github.com/lh1me/hexo-theme-aomori)为例。 
可以使用Aomori官方给出的指令
``` bash
npm i hexo-theme-aomori --save
```
并且编辑blog目录下的_config.yml
``` bash
theme: aomori
```
你可以参考你的主题的文档或你的WEB开发知识，不断完善你的网站
## 新建文章

Hexo使用markdown来编写文章，你可以在网上找到很多教程，不得不承认这比HTML方便很多。 

若新建名为page的文章。
在blog目录下输入
``` bash
hexo new page
```
这会在blog/soure/_posts下生成对应的page.md

## 撰写文章
在手机上我们建议使用第三方文本编辑器来编写 ，有语法高亮首选，例如QuickEdit Text Editor，termux一般会在系统文件夹里提供一个可供访问的端口，这样即使手机未取得root权限也能编辑该md文件，例如
![](https://pic.imgdb.cn/item/64d2efac1ddac507ccc05e29.jpg)

## 调试
输入
``` bash
hexo clean
```
清除缓存  

输入
``` bash
hexo g
```
将md文件自动转换成网页  
输入
``` bash
hexo s
```
开启本地端口，这时你可以通过
``` bash
http://localhost:4000/
```
来查看你的网站和文章是否有格式错误并进行调整

## 部署
修改blog目录下的网站配置文件_config.yml，编辑以下内容
 ``` bash

# URL

url: https://your-username.github.io

root: /

 

# Deployment

deploy:

  type: git

  repository: https://github.com/your-username/your-username.github.io.git

  branch: master
  
  ```
  把上述的链接地址修改成你自己的
  然后输入
   ``` bash
hexo d

```
  输入用户名和密码就可以完成部署，这时使用访问对应的GitHub Page网页就是你的博客了
## 常见报错及提醒
### Git
执行git命令出现错误一般是网络问题，使用代理或换个网络一般就能解决
### NPM
同git，如果出现进度条长时间不动可以试试把后台删了重新执行该命令
### [VIM](https://www.vim.org/)
基本命令  

以下是一些基本的Vim命令：
|  ESC &#43;                       |      作用                                                                                              |
|  :-                               |     :-----------                                                                                      |
| i                                 |     在当前光标位置插入文本。                                                           |
|  x                               |     删除当前光标所在位置的字符。                                                    |
|  :w                             |     保存文件。                                                                                     |
|  :q                              |     退出Vim编辑器。                                                                           |
|  :q!                             |     强制退出Vim编辑器，不保存文件。                                              |
|  :wq                           |     保存文件并退出Vim编辑器。                                                         |
|  :wq!                          |    强制保存并退出。                                                                           |
|  dd                             |    删除当前行。                                                                                  | 
|  yy                              |    复制当前行。                                                                                  |
|  p                                |    粘贴已复制或删除的文本。                                                            |
|  u                                |    撤销上一次操作。                                                                           |
|  r                                 |    替换当前光标所在位置的字符。                                                     |
|  c                                 |     删除从当前光标位置到指定位置的文本并进入插入模式。            |
|   v                                |    进入可视模式，选择文本。                                                            |
|  :s/&lt;old&gt;/&lt;new&gt;/g     |    将当前行中的&lt;old&gt;替换为&lt;new&gt;。                                              |
|  :%s/&lt;old&gt;/&lt;new&gt;/g    |    将整个文件中的&lt;old&gt;替换为&lt;new&gt;。                                           |

### Markdown
常用语法
#### 标题
``` bash
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

```
#### 文本
就按普通文本一样直接写
#### 链接
``` bash
[链接文字](链接地址)
```
#### 图片
图片名字可有可无，图片地址你可以使用网站素材文件夹里图片的地址，也可以使用在线图床的网址
``` bash
![图片名字](图片地址)
```

其他语法请自寻查找，另外markdown有着十分严格的语法规定，所以在编辑文件时请注意你的缩进，例如我在文章中添加一个多余缩进，再执行hexo＋ g命令，则会出现报错
``` bash
╭─u0_a276 at localhost in ~/blog 23-08-09 - 10:47:20
╰─○ hexo g
INFO  Validating config
INFO  Start processing
ERROR Process failed: _posts/hello-world.md
YAMLException: end of the stream or a document separator is expected (1:10)

 1 |    →title: Hello World
--------------^
    at generateError (/data/data/com.termux/files/home/blog/node_modules/js-yaml/lib/loader.js:183:10)
    at throwError (/data/data/com.termux/files/home/blog/node_modules/js-yaml/lib/loader.js:187:9)
    at readDocument (/data/data/com.termux/files/home/blog/node_modules/js-yaml/lib/loader.js:1645:5)
    at loadDocuments (/data/data/com.termux/files/home/blog/node_modules/js-yaml/lib/loader.js:1688:5)
    at Object.load (/data/data/com.termux/files/home/blog/node_modules/js-yaml/lib/loader.js:1714:19)
    at parseYAML (/data/data/com.termux/files/home/blog/node_modules/hexo-front-matter/lib/front_matter.js:69:23)
    at parse (/data/data/com.termux/files/home/blog/node_modules/hexo-front-matter/lib/front_matter.js:50:12)
    at /data/data/com.termux/files/home/blog/node_modules/hexo/lib/plugins/processor/post.js:93:18
    at tryCatcher (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/util.js:16:23)
    at Promise._settlePromiseFromHandler (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise.js:544:35)
    at Promise._settlePromise (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise.js:604:18)
    at Promise._settlePromise0 (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise.js:649:10)
    at Promise._settlePromises (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise.js:729:18)
    at Promise._fulfill (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise.js:673:18)
    at PromiseArray._resolve (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise_array.js:127:19)
    at PromiseArray._promiseFulfilled (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise_array.js:145:14)
    at PromiseArray._iterate (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise_array.js:115:31)
    at PromiseArray.init [as _init] (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise_array.js:79:10)
    at Promise._settlePromise (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise.js:601:21)
    at Promise._settlePromise0 (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise.js:649:10)
    at Promise._settlePromises (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise.js:729:18)
    at Promise._fulfill (/data/data/com.termux/files/home/blog/node_modules/bluebird/js/release/promise.js:673:18)
INFO  Files loaded in 182 ms
INFO  0 files generated in 66 ms
╭─u0_a276 at localhost in ~/blog 23-08-09 - 10:48:30
╰─○
```
此时只需要删除或添加它提到的地方的缩进就可以了
### 部署时报错
部署时输入GitHub用户名和GitHub密码后出现如下报错
 ``` bash
╭─u0_a276 at localhost in ~/ET 23-08-09 - 11:10:41
╰─○ hexo d
INFO  Validating config
INFO
  ===================================================================
      #####  #    # ##### ##### ###### #####  ###### #      #   #
      #    # #    #   #     #   #      #    # #      #       # #
      #####  #    #   #     #   #####  #    # #####  #        #
      #    # #    #   #     #   #      #####  #      #        #
      #    # #    #   #     #   #      #   #  #      #        #
      #####   ####    #     #   ###### #    # #      ######   #
                            4.9.0
  ===================================================================
INFO  Deploying: git
INFO  Clearing .deploy_git folder...
INFO  Copying files from public folder...
INFO  Copying files from extend dirs...
On branch master
nothing to commit, working tree clean
Username for &#39;https://github.com&#39;: inagiaden
Password for &#39;https://inagiaden@github.com&#39;:
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for &#39;https://github.com/inagiaden/inagiaden.github.io.git/&#39;
FATAL Something&#39;s wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
Error: Spawn failed
    at ChildProcess.&lt;anonymous&gt; (/data/data/com.termux/files/home/ET/node_modules/hexo-util/lib/spawn.js:51:21)
    at ChildProcess.emit (node:events:513:28)
    at ChildProcess._handle.onexit (node:internal/child_process:291:12)
╭─u0_a276 at localhost in ~/ET 23-08-09 - 11:11:23
╰─○
```
这是因为2021年后，使用第三方上传密码时需要专用的密码
#### 解决办法
登录GitHub--&gt;  Settings --&gt; Developer Settings -&gt; Personal access tokens --&gt; Tokens --&gt; Generate new token --&gt; Generate new token (classic) --&gt; Note: ZeroTermux  Expiration：No expiration Select scopes：select all --&gt;Generate  token  
复制出现的密码（建议固定到剪切板，因为只出现一次）输入密码时将此输入就行了
#### 注意
每一次部署，hexo都会清空原来的GitHub Page仓库，所以请不要直接用浏览器向GitHub Page仓库手动添加文件

---

> 作者: [Haoran Dong](https://github.com/TEWQ-1314)  
> URL: https://www.depth.su/posts/git-blog/  

