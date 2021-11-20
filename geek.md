# 重装前

- Originlab deactive
- SwichOmega bakup
- eudic bakup
- xshell
- anjian
- sharpkeys
- tampermonkey
- displayfusion

# proxy

## Win-gui

### SwitchOmega

- 莫名屏蔽 journal web

### ssr

没有官方客户端
无法批量ping

### clash

git代理: 关闭 service mode

## Android

开数据容易架梯子，连pc热点容易架梯子
商店“正在等待下载”，关闭迅雷引擎

## Shop

### anycast

<https://sgi.anycast.gay/user>
20/month

### stc
<http://stc-hk.com/>
0.8/G
v2ray/ss

### renzheyun
<https://renzhe.cloud/user>
9.9/month
clash/ssr
速度不稳定

# 词典

## 有道

转圈圈

# reader

## smartraPDF

字符不显示
底色红

# aria2

<https://github.com/aria2/aria2/>
<http://aria2c.com/usage.html>
<https://zhuanlan.zhihu.com/p/21831960>

# win10

## 禁用insert
<https://www.howtogeek.com/666698/how-to-disable-the-insert-key-in-windows-10/>
<https://github.com/randyrants/sharpkeys/>

## bugs

无法加载页面
error 代码: 0x000001F7
解决
<https://answers.microsoft.com/zh-hans/windows/forum/all/microsoft/4a6df569-dd2c-4718-862f-9d66b4b48889>
开启自动代理
win+r WSReset.exe

# cmd

## 调用cmd

```
cmd /C
```

## mklink
<https://liam.page/2018/12/10/mklink-in-Windows/>
删除虚拟的链接目录，并不会删除远程文件夹真实文件，注意千万不能用del，del会删除远程的真实文件。

```cmd
rmdir d:\recivefiles
rmdir d:\develop
```

# Chromeos

安装chromeos教程
<http://www.rojter.tech/?p=39>
修复WiFi、声音
<https://github.com/arnoldthebat/chromiumos/issues/153>
vim 与vi的兼容性问题
<https://blog.csdn.net/qdujunjie/article/details/38922187>
解除只读权限
<https://tieba.baidu.com/t/p/119453937445>
如何在普通电脑上安装Chrome OS？
<https://shimo.im/docs/eu9vbnsVFZkebgNI>
chomeos镜像
<https://cros-updates-serving.appspot.com/>
Developer Information for Chrome OS Devices - The Chromium Projects
<https://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices>
crostini-enabled-devices - Crostini
<https://www.reddit.com/r/Crostini/wiki/getstarted/crostini-enabled-devices>
chromiumos镜像
<https://arnoldthebat.co.uk/wordpress/>
recovery镜像
<https://dl.google.com/dl/edgedl/chromeos/recovery/recovery.conf>

# 邮件客户端

[foxmail
来信图标不消除
[em client
文字检索功能失效
[网易邮箱
联系人
[outlook uwp
插入图片显示异常

# 手机显示器

## twomon usb

停更，无法链接

## twomon xe

付费

## Duet display

付费，无最新crack

## wred xdisplay

停更

# 文献管理

## endnote

文献缩写不规范，格式老旧更新慢
没有浏览器插件
1.output style
modify
2.Journals term list
update手动添加
<https://woodward.library.ubc.ca/research-help/journal-abbreviations/>
<https://jcr.incites.thomsonreuters.com/JCRLandingPageAction.action>
<https://www.ncbi.nlm.nih.gov/nlmcatalog/journals>

## sciwheel

word插件卡的不能自理
删除文献删不干净
导出bib有问题

## Mendeley

word插件，PRB 引用格式不符

# andoid emulator

## ss代理应用

Proxifier
服务器：127.0.0.1
代理规则：联网软件
缺陷：模拟器内浏览器无法通过代理

## 浏览器代理

Wifi代理获取pc本地ip
ipconfig

## 雷电4.0

按键精灵ui闪退

## mumu 6.0

按键精灵不定时失效
adb kill-server
adb connect 127.0.0.1:7555

## AVD

magisk：<https://www.youtube.com/watch?reload=9&v=FuUrjEvQ1UU>
模拟器打不开

## vs-emulator

文件传输找不到adb.exe

# word

## bug

调格式恶心
删除线
表格首行缩进
公式字体莫名改变

# anjian

## notes

pc端3.3.1需要管理员身份运行，而且wifi无法扫描到设备
wifi连接扫描不到设备尝试断开ss
抓图在安卓9.0失效
开启模拟器root使按键精灵获取root，然后关闭root正常运行

# materials studio

## 旋转分子

SHIFT+右键  旋转
ALT+右键    平移

## 内存占用高

关闭结构窗口

## 输入卡死

### solution

在微软拼音输入法的“中”(或“英”)字上右击鼠标，然后点“设置”，在弹出界面中点“常规”，在新界面中向下滚动到底部，有个兼容性，打开兼容性，然后就OK了。

### reason

win10v2004微软拼音不兼容

<http://muchong.com/t-14325407-1>

## 经验教程
<http://muchong.com//t-11279111-1>

## 图像重影问题

MS界面→tools→options→Graphics ：
查看其中的选项是否勾选，如果没有勾选，全部勾选，重启MS；
如果已经勾选，现全部不勾选，重启MS。

## 下载安装破解
<https://www.zdfans.com/html/48131.html>

# cluster

## bug

### error

提交的任务一直显示run，并行程序却没有真正执行，标准输出中相关的内容什么都没有

### solution

mpi通信需要你的账号在计算节点之前可以ssh免密登录，但是你的.ssh目录不明原因被修改了导致节点互访出现问题

# VESTA

*晶胞transform时先remove symmetry
