# How to Fixs Pixel:&#34;Your Device Is Corrupt....&#34;

### 情况描述
情况描述从安卓 13 回退到安卓 12 时，手机手机后出现这个界面，按下电源键后立刻重启，又回到这一界面，无法进入系统
``` bash
＜ ! ＞Your device is corrupt。It cant be trusted and may work properly
Visit this link on another device:
g.co\ABH
```
![](https://s2.loli.net/2022/07/13/1Q9yPH47pzNcLVU.jpg)
据说是因为更新时候损坏了系统校验，所以无法进入
## 其他网友做法先来看看其他网友的做法
方法 1：手机进入 REC，点击【高级】，点击【终端命令】输入：  
``` bash
 reboot &#34;dm-verity enforcing&#34;
 ```
方法 2：连接电脑后，在电脑打开【ADB 命令行】输入：
``` bash
 adb reboot &#34;dm-verity enforcing&#34;
```
方法 3：[Your device is corrupt. It cant‘t be trusted and may not work propely.](http://t.csdn.cn/ZtuM7)

## 博主的做法：重装系统
### 准备工具
问题的Google Pixel 4A (5G)（其他机型类比）, 一台笔记本电脑，一根可以传输数据的 USB 数据线

### 下载工具包
打开电脑，从 Google 官方下载 [ADB 命令行](https://developer.android.google.cn/studio/releases/platform-tools?hl=zh-cn#downloads)工具包，下载完成之后解压缩，记录下解压后的文件夹目录，例如我这里是 
``` bash
E:\TEMP\platform-tools_r33.0.2-windows\platform-tools
```
 每个人的电脑不一样，自己随机应变
 
### 配置环境变量
桌面上找到 “此电脑”, 鼠标右单击，左单击 “属性” 进入控制面板，点击 “系统高级设置”，设置环境变量。在 “系统变量” 一栏点击 “path” 变量，新建，把刚才复制的路径粘贴。E:\TEMP\platform-tools_r33.0.2-windows\platform-tools 然后保存。不会的朋友可以参考 Google.
![](https://s2.loli.net/2022/07/13/BKimrp47wZSs6fk.jpg)
使用 win&#43;R 调出窗口，输入 cmd 后回车进入命令行，将手机的用数据线与电脑相连
### 进入Fastboot
将手机关机重启，重启时长按电源键和音量加键直到进入 Fastboot model
![](https://s2.loli.net/2022/07/13/if9eRjyrBVCbdX1.jpg)
### 进入工程模式
长按音量加键直到进入工程模式（不同机型可以上网查询如何进入）
![](https://s2.loli.net/2022/07/13/HholnZBXrkm5f6E.jpg)
### 进入Recovery
按住电源键，同时按一下音量加键，进入Android Recovery
### 选择ADB更新
用音量键进行选择，我们这里选择Apply update from ADB. 按电源键确认
![](https://s2.loli.net/2022/07/13/JREKaWeTwmZp1dz.jpg)
### 连接
在电脑命令行输入
``` bash
adb devices
```
回车，这是电脑上会返回你的手机编号，说明成功连接
![](https://s2.loli.net/2022/07/13/JlIXGO2zhuEcAdn.jpg)
### 下载系统镜像
访问你的手机官方镜像站，下载对应的 OTA 包，例如我的手机是 Pixel 4a5g, 访问[谷歌官方网站](https://developer.android.google.cn/about/versions/13/download-ota?hl=zh-cn)下载，注意一定要下载本机型的 OTA 包，且下载包的版本不能低于当前手机系统的版本
![](https://s2.loli.net/2022/07/13/9hnN2pQxmo45S1Y.png)
### 刷入镜像
下载完成后，命令行输入

``` bash
adb sideload
``` 
然后把下载文件拖入命令行窗口，这是它会自动补全 sideload 后面的路径，然后回车，开始写入数据，等待进度到达 100% 后，就可以开机进入系统了
![](https://s2.loli.net/2022/07/13/HVmGMv47I58LYQb.jpg)

---

> 作者: [Haoran Dong](https://github.com/TEWQ-1314)  
> URL: https://www.depth.su/posts/pixelbugs/  

