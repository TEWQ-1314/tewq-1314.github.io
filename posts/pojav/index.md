# How to Play Minecraft:Java 1.17 on Android/PojavLauncher

// Because my English level is limited, please forgive me for speaking in Chinese.You can use Google to translate this article, there may be some errors.I am deeply sorry for the trouble you have caused!  
前言：对于不少想要在安卓手机上体验MC:JAVA版的MC玩家，这里我将尽力阐述详细的做法，如果有任何的问题，欢迎留言或发邮件，测试时最新版为1.17，如有差别联系询问。
  ![](https://i.imgtg.com/2023/07/25/OhYqPK.jpg)
## 示例1.16.5
一，MC:Java 1.17及以后（由于1.17及以后的MC版本使用的Java版本与之前不同，所以我将分开叙述）
准备：PojavLauncher app，Jre17/aarch64

### 下载PojavLauncher
注意！！：这里请不要使用Google play下载，请访问开发者的[github网站](https://github.com/PojavLauncherTeam/PojavLauncher/actions?query=branch%253Av3_openjdk)以下载最新版的app，而且此版本会导致手机非常卡顿，甚至无法进入游戏！！目前不建议使用  

如果你不是很擅长github可以在这里下载稳定版的
app-debug-norruntime.apk，注意是app-debug-norruntime.apk而不是app-debug.apk。
首先点击链接，然后滑倒最底端，如图点击最新版，然后再滑倒最底部，下载app-debug-norruntime.apk
![](https://i.imgtg.com/2023/07/25/OhYMLg.png)

### 下载Java
下载临时[Jre17版本](https://github.com/PojavLauncherTeam/android-openjdk-build-multiarch/actions?query=branch%253Abuildjre16)因为目前1.17是测试项目，不是很稳定
详细过程可以参考[Pojav官方文档](https://pojavlauncherteam.github.io/updates/117.html)
注意绿色打勾的文件才能使用，此时下载文件需要登录github,账号自己注册
![](https://i.imgtg.com/2023/07/25/OhYOuB.png)
![](https://i.imgtg.com/2023/07/25/OhYozs.png)
注意，要下载对应的版本

基本上所有人都应该选择下载jre17-aarch64,极少数人要根据自己手里架构下载对应版本。
![](https://i.imgtg.com/2023/07/25/OhVw7l.jpg)
下载好软件和jre后，首先打开PojavLauncher软件，它会让你导入运行库，你就选择你下载的文件，因为下载的是zip文件，识别的是tar.gz文件，所以可能要点两次才能成功。

然后将渲染器切换到 gl4es 1.1.5 - OpenGL ES 3。
你就可以享受MC:Java 1.17了！！

以上是比较正规的做法，其实在官方github上的Action上有许多开发者上传的安装包中兼容了Jre17,直接下载这种未发布版本也是一种尝鲜的好办法，但我相信不久之后官方会推出稳定的1.17版本，现在还是1.16.5之类的玩玩就行了。



## MC:Java 1.17以前的版本
  
此时我们建议使用Google play下载PojavLauncher，不用下载其他文件，打开软件可直接下载对应的jar进行游戏。

###注释:  
1,经本人验证，PojavLauncher界面和其他方面比Mcinabox好。  

2, Google play下载的PojavLauncher对于1.16.5等版本的支持较好，可以流畅游玩。而配置过的1.17版本的软件几乎所有版本的优化都不是很好，不建议玩家尝试.  
  
3,对于无法使用微软登录PojavLauncher的用户，可能是因为你你的账号没有购买正版MC:Java.
报错提示：
``` bash
(java.lang.RuntimeException: Can&#39;t login a demo account!  

MSA Error: 404: Not Found, error stream:
{
  &#34;path&#34; : &#34;/minecraft/profile&#34;,
  &#34;errorType&#34; : &#34;NOT_FOUND&#34;,
  &#34;error&#34; : &#34;NOT_FOUND&#34;,
  &#34;errorMessage&#34; : &#34;The server has not found anything matching the request URI&#34;,
  &#34;developerMessage&#34; : &#34;The server has not found anything matching the request URI&#34;
}
 at net.kdt.pojavlaunch.authenticator.microsoft.Msa.throwResponseError(Msa.java:292)
 at net.kdt.pojavlaunch.authenticator.microsoft.Msa.checkMcProfile(Msa.java:256)
 at net.kdt.pojavlaunch.authenticator.microsoft.Msa.acquireMinecraftToken(Msa.java:200)
 at net.kdt.pojavlaunch.authenticator.microsoft.Msa.acquireXsts(Msa.java:167)
 at net.kdt.pojavlaunch.authenticator.microsoft.Msa.acquireXBLToken(Msa.java:122)
 at net.kdt.pojavlaunch.authenticator.microsoft.Msa.acquireAccessToken(Msa.java:75)
 at net.kdt.pojavlaunch.authenticator.microsoft.Msa.&lt;init&gt;(Msa.java:35)
 at net.kdt.pojavlaunch.authenticator.microsoft.MicrosoftAuthTask.doInBackground(MicrosoftAuthTask.java:72)
 at net.kdt.pojavlaunch.authenticator.microsoft.MicrosoftAuthTask.doInBackground(MicrosoftAuthTask.java:22)
 at android.os.AsyncTask$3.call(AsyncTask.java:394)
 at java.util.concurrent.FutureTask.run(FutureTask.java:266)
 at android.os.AsyncTask$SerialExecutor$1.run(AsyncTask.java:305)
 at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1167)
 at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:641)
 at java.lang.Thread.run(Thread.java:923)
```

![](https://i.imgtg.com/2023/07/25/OhVCOb.jpg)  

4,所有的教程都是针对目前而言(2021.8.8),对于之前或之后的适用性无法保证
5,有些细节被省略，不懂得玩家可以发邮件或留言，一定尽力解决问题



---

> 作者: [Haoran Dong](https://github.com/TEWQ-1314)  
> URL: https://www.depth.su/posts/pojav/  

