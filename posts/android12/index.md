# How to Solve the Problem That Android12&#43; Automatically Ends the Process -PhantomProcessKiller

Scene:  Termux: [Process completed (signal 9) - press Enter] and Game Exit etc.  
![](https://i.imgtg.com/2023/07/25/OhfN4B.jpg) 

### Description
The latest Android 12 system has been upgraded recently, but there is a problem at present. It may be that the power saving strategy is too radical. Android 12 introduces a program called PhantomProcessKiller, which will detect programs that use too many CPUs. If the parent process is in the background, it will kill all child processes triggered by it.This makes some software such as Termux almost unusable or leads to a poor gaming experience.

### Demo Tools
An Android Tablet PC(android 12)-Equipment to be repaired , A Smart Phone(android 13)   
[Termux](https://f-droid.org/en/packages/com.termu) (Both devices are in the same LAN).    
## 开始

### 进入工程模式
Open APaid →Settings  →About APaid →Quickly and continuously click Build Number(You will see a sentence )
 ![](https://i.imgtg.com/2023/07/25/Ohf7ig.png)
### Find the Developer Options
 ![](https://i.imgtg.com/2023/07/25/Ohfn3l.jpg)
### Find the Wireless debugging and switch on
![](https://i.imgtg.com/2023/07/25/OhfKma.jpg)
### Gain the Code
Then click Pair device with pairing code,you will see these information.   
 ![](https://i.imgtg.com/2023/07/25/Ohfe2s.jpg)
For example:
IP address and connection port(192.168.1.6:33275)   
IP address and debug port(192.168.1.6:46085)  
Wi-Fi pairing code(813297).   
  ———Then Don&#39;t Close This Page.
 
 ### 更新Termux
``` bash
pkg update
pkg upgrade
```
### Install Git and Tools
``` bash
pkg install  git  
 ```
we need to install adb in termux that supports pair feature. for some reason latest version of adb is not available in both termux and debian apt mirrors. luckly a guy on github called reddix did the hard work of compiling adb with gigs of android source code. to install them use.
``` bash
git clone https://github.com/rendiix/termux-adb-fastboot
```
![](https://i.imgtg.com/2023/07/25/OhfyqN.jpg)
``` bash
cd termux-adb-fastboot
```

``` bash
cp -v binary/$(getprop ro.product.cpu.abi)/bin/\* ~/../usr/bin/
```
![](https://i.imgtg.com/2023/07/25/OhfAbK.jpg)
### Pair with the Debugging Service

``` bash
adb pair IP:&lt;connection port&gt; &lt;Wi-Fi pairing code&gt;*
```
For example
``` bash
adb pair 192.168.1.6:33275 813297
```
### Now connect to the device
``` bash
adb connect &lt;IP address and debug port&gt;
```

``` bash
adb connect 192.168.1.6:46085
```
![](https://i.imgtg.com/2023/07/25/OhfiQb.jpg)
### check
``` bash
adb devices
```
![](https://i.imgtg.com/2023/07/25/OhfZVS.jpg)
// Try repeating previous steps if something happens to work. Settings may turn off wireless debugging sometimes after the first pairing.

### Fix
Finally fix phantom issue with this command
``` bash
adb \
shell \
device\_config \
put activity\_manager \
max\_phantom\_processes 214181594
adb shell device\_config \
set\_sync\_disabled\_for\_tests persistent
```
![](https://i.imgtg.com/2023/07/25/OhfgrC.jpg)
### Side Effects

Increasing phantom process limit causes more process-heavy apps other than termux to run in the background which could cause performance issues when dealing with games or heavy daily drive usage in mid-range phones.

when you feel the stutter and want to make things back to normal use this command.
``` bash
adb shell device\_config \
set\_sync\_disabled\_for\_tests none
```
### 其他文章
[完美解决安卓12 PhantomProcessKiller的办法](https://mi.mbd.baidu.com/r/SuWg6vmK7m?f=cp)

---

> 作者: [Haoran Dong](https://github.com/TEWQ-1314)  
> URL: https://www.depth.su/posts/android12/  

