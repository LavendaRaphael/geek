# Windows

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Windows](#windows)
  - [重装前](#重装前)
  - [ssh-client](#ssh-client)
  - [wsl2](#wsl2)
    - [硬盘存储占用无法释放](#硬盘存储占用无法释放)
    - [安装](#安装)
    - [文件系统权限](#文件系统权限)
    - [wsl命令](#wsl命令)
    - [link](#link)
      - [ssh自启](#ssh自启)
      - [外部局域网访问](#外部局域网访问)
    - [screen](#screen)
    - [latexworkshop](#latexworkshop)
  - [proxy](#proxy)
    - [Win-gui](#win-gui)
      - [v2rayN](#v2rayn)
      - [SwitchOmega](#switchomega)
      - [SSR](#ssr)
      - [clash](#clash)
  - [词典](#词典)
    - [有道](#有道)
  - [reader](#reader)
    - [smartraPDF](#smartrapdf)
  - [aria2](#aria2)
  - [bugs](#bugs)
  - [cmd](#cmd)
    - [调用cmd](#调用cmd)
    - [mklink](#mklink)
  - [Chromeos](#chromeos)
  - [邮件客户端](#邮件客户端)
  - [文献管理](#文献管理)
    - [endnote](#endnote)
      - [shortage](#shortage)
      - [notes](#notes)
    - [sciwheel](#sciwheel)
    - [Mendeley](#mendeley)
  - [andoid emulator](#andoid-emulator)
    - [ss代理应用](#ss代理应用)
    - [浏览器代理](#浏览器代理)
    - [雷电4.0](#雷电40)
    - [mumu 6.0](#mumu-60)
    - [AVD](#avd)
    - [vs-emulator](#vs-emulator)
  - [word](#word)
    - [bug](#bug)
  - [anjian](#anjian)
    - [notes](#notes-1)

<!-- /code_chunk_output -->


## 重装前

- Originlab deactive
- SwichOmega bakup
- eudic bakup
- xshell
- anjian
- sharpkeys
- tampermonkey
- displayfusion

## ssh-client

- xshell
  - 无wsl支持
  - vim 显示异常
- Windterm
  - vim显示
  - 文献传输
- MobaXterm

## wsl2

### 硬盘存储占用无法释放

<https://loesspie.com/2021/01/27/wsl2-compact-disk-win10/>

### 安装

<https://docs.microsoft.com/en-us/windows/wsl/install>

### 文件系统权限

```bash
sudo vim /etc/wsl.conf
```

```conf
[automount]
options = "metadata,umask=22,fmask=11,uid=1000,gid=1000"
```

<https://www.jianshu.com/p/f9efb4c1e0bb>

### wsl命令

```powershell
wsl -help
wsl -l -v
wsl --update
wsl --shutdown
```

### link

```bash
ln -s /mnt/c/Users/feife/OneDrive/Research ~/Research
ln -s /mnt/c/Users/feife/OneDrive/Doc ~/Doc
ln -s /mnt/c/Users/feife/OneDrive/Doc/script/server.me.sh ~/server.me.sh
ln -s /mnt/c/Users/feife/OneDrive/SynTemp ~/SynTemp
```

#### ssh自启

```bash
sudo vim /etc/init.wsl
```

```bash
#!/bin/bash
service ssh start
```

```bash
sudo chmod 700 /etc/init.wsl
```

<https://juejin.im/post/6847902218226499598>

#### 外部局域网访问

ps脚本可执行

```powershell
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope CurrentUser
```

windows

- 计算机管理 - 任务计划程序 - 任务计划程序库 - 新文件夹 'me' - 导入 `C:\Users\laven\OneDrive\arxive\myscript\ubuntu.xml`

<https://docs.microsoft.com/zh-cn/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.1>
<https://www.zhihu.com/question/40596907>
<https://gist.github.com/daehahn/497fa04c0156b1a762c70ff3f9f7edae>
<https://www.hanselman.com/blog/how-to-ssh-into-wsl2-on-windows-10-from-an-external-machine>

### screen

```shell
sudo screen
sudo chmod 777 /run/screen/
```

<https://github.com/microsoft/WSL/issues/1245>

### latexworkshop

```bash
vim .profile
```

```bash
export PATH=~/software/texlive/2021/bin/x86_64-linux:$PATH
```

<https://github.com/James-Yu/LaTeX-Workshop/wiki/Install#using-wsl>

## proxy

### Win-gui

#### v2rayN

#### SwitchOmega

- 莫名屏蔽 journal web

#### SSR

- 没有官方客户端
- 无法批量ping

#### clash

- git代理: 关闭 service mode, socks代理失效

## 词典

### 有道

转圈圈

## reader

### smartraPDF

字符不显示
底色红

## aria2

<https://github.com/aria2/aria2/>
<http://aria2c.com/usage.html>
<https://zhuanlan.zhihu.com/p/21831960>

## bugs

无法加载页面

error 代码: 0x000001F7

解决

<https://answers.microsoft.com/zh-hans/windows/forum/all/microsoft/4a6df569-dd2c-4718-862f-9d66b4b48889>

开启自动代理

win+r WSReset.exe

## cmd

### 调用cmd

```
cmd /Cl
```

### mklink
<https://liam.page/2018/12/10/mklink-in-Windows/>
删除虚拟的链接目录，并不会删除远程文件夹真实文件，注意千万不能用del，del会删除远程的真实文件。

```cmd
rmdir d:\recivefiles
rmdir d:\develop
```

## Chromeos

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

## 邮件客户端

foxmail

来信图标不消除

em client

文字检索功能失效

网易邮箱

联系人

outlook uwp

插入图片显示异常

## 文献管理

### endnote

#### shortage

- 文献缩写不规范，格式老旧更新慢
- 没有浏览器插件

#### notes

- output style
  - modify
- Journals term list
  - update手动添加
  - <https://woodward.library.ubc.ca/research-help/journal-abbreviations/>
  - <https://jcr.incites.thomsonreuters.com/JCRLandingPageAction.action>
  - <https://www.ncbi.nlm.nih.gov/nlmcatalog/journals>

### sciwheel

- word插件卡的不能自理
- 删除文献删不干净
- 导出bib有问题

### Mendeley

- word插件，PRB 引用格式不符
- 排序自动被重置
- 文献看不到归属分组

## andoid emulator

### ss代理应用

Proxifier
服务器：127.0.0.1
代理规则：联网软件
缺陷：模拟器内浏览器无法通过代理

### 浏览器代理

Wifi代理获取pc本地ip
ipconfig

### 雷电4.0

按键精灵ui闪退

### mumu 6.0

按键精灵不定时失效
adb kill-server
adb connect 127.0.0.1:7555

### AVD

magisk：<https://www.youtube.com/watch?reload=9&v=FuUrjEvQ1UU>
模拟器打不开

### vs-emulator

文件传输找不到adb.exe

## word

### bug

调格式恶心
删除线
表格首行缩进
公式字体莫名改变

## anjian

### notes

pc端3.3.1需要管理员身份运行，而且wifi无法扫描到设备

wifi连接扫描不到设备尝试断开ss

抓图在安卓9.0失效

开启模拟器root使按键精灵获取root，然后关闭root正常运行
