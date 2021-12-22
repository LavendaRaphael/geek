# bash

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=3 orderedList=false} -->

<!-- code_chunk_output -->

- [bash](#bash)
  - [font](#font)
  - [loop](#loop)
    - [array](#array)
  - [apt](#apt)
    - [basic](#basic)
  - [x11](#x11)
    - [VcXsrv](#vcxsrv)
  - [赋值](#赋值)
    - [缺省](#缺省)
    - [赋值](#赋值-1)
  - [vim](#vim)
    - [替换](#替换)
    - [换行替换](#换行替换)
    - [全局替换缩进](#全局替换缩进)
    - [杂项](#杂项)
  - [sed](#sed)
    - [行替换](#行替换)
    - [替换](#替换-1)
  - [if](#if)
    - [true or false](#true-or-false)
    - [文件是否存在](#文件是否存在)
  - [awk](#awk)
    - [多字符串匹配](#多字符串匹配)
    - [字符串函数](#字符串函数)
    - [末尾1](#末尾1)
    - [正则匹配](#正则匹配)
    - [skip blank line and line](#skip-blank-line-and-line)
    - [逻辑算符](#逻辑算符)
    - [直接编辑](#直接编辑)
    - [if](#if-1)
    - [内建变量](#内建变量)
    - [loop](#loop-1)
    - [数字比较](#数字比较)
    - [变量](#变量)
    - [替换](#替换-2)
    - [printf](#printf)
  - [ubuntu换源](#ubuntu换源)
  - [ssh](#ssh)
  - [dns](#dns)
  - [find](#find)
    - [避开目录](#避开目录)
    - [第一次终止](#第一次终止)
    - [不显示权限不足](#不显示权限不足)
    - [-mindepth -maxdepth](#-mindepth-maxdepth)
  - [grep](#grep)
    - [多字符匹配](#多字符匹配)
    - [正则表达式](#正则表达式)
  - [Intel Oneapi](#intel-oneapi)
    - [version manage](#version-manage)
    - [防止 python 退格乱码](#防止-python-退格乱码)
  - [convert](#convert)
  - [gif](#gif)
    - [ase](#ase)
    - [png2gif](#png2gif)
    - [gif2png](#gif2png)
    - [mp42png](#mp42png)
    - [批量裁切](#批量裁切)
  - [git](#git)
    - [构建](#构建)
    - [维护](#维护)
    - [contribution 不显示](#contribution-不显示)
    - [撤销commit](#撤销commit)
  - [alias](#alias)
    - [chmod递归权限](#chmod递归权限)
    - [截取snapshot](#截取snapshot)
    - [bash](#bash-1)
    - [pbs](#pbs)
    - [bash, mv不包括](#bash-mv不包括)
  - [tar](#tar)
  - [杂项](#杂项-1)
    - [case](#case)
    - [sort](#sort)
    - [array](#array-1)
    - [退格乱码](#退格乱码)
    - [中止](#中止)
    - [判断](#判断)
    - [while](#while)
    - [传参](#传参)
    - [奇怪字符](#奇怪字符)
    - [提取目录名](#提取目录名)
    - [root](#root)
    - [zip](#zip)
    - [calculation](#calculation)
    - [字符串截取](#字符串截取)
    - [查杀进程](#查杀进程)
    - [bashrc](#bashrc)
    - [screen](#screen)
    - [chmod](#chmod)

<!-- /code_chunk_output -->

## font

```bash
sudo cp -r windowsfont/ /usr/local/share/fonts/
sudo fc-cache -f
fc-match Arial
```

<https://askubuntu.com/questions/651441/how-to-install-arial-font-and-other-windows-fonts-in-ubuntu>

`C:\Windows\Fonts\`

## loop

### array

```bash
x=(0 1 2)
for i in ${x[@]}

x='0 1 2'
for i in $x

break [n]
continue [n]
```

## apt

### basic

```bash
apt-cache search
apt-cache show <packname>
sudo apt update
sudo apt upgrade
sudo apt autoremove
sudo apt remove <>
```

## x11

### VcXsrv

libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
去勾选 Native opengl

## 赋值

### 缺省

`${a-defaultvalue}`
a如果没有定义，则表达式返回默认值，否则返回a的值；
`${a:-defaultvalue}`
a没有定义或者为空字符串，则表达式返回默认值，否则返回a的值；

### 赋值

```bash
$()

``
```

## vim

### 替换

`:%s/old/new/g` 文本替换

对特殊字符诸如`$ % [ ] .`等都需要在前面加上转义才可以。
注意替换中只需要在需要被查找的部分加上转义字符，后面替换的内容不用加。

### 换行替换

`\r`

### 全局替换缩进

`:set ts=8 sts=8 noet`    设置tab格数

`:retab!`                 空格替换为tab

`:set ts=4 sts=4 et`      更换tab个数

`:retab`                  tab替换空格

<https://www.itranslater.com/qa/details/2123239368239350784>

### 杂项

`:scriptnames` #查看配置文件载入列表

`:set textwidth=0` #禁用自动换行

`p` #粘贴

`y` #复制

`v` #选择

`:let i=0 | g/zcc/s//\=i/ | let i=i+1`

行编号，zcc为替换点

## sed

### 行替换

`sed -i "2c hello" POSCAR`

<https://blog.51cto.com/xficc/1621403>

### 替换

`sed -i 's/book/books/g' file`
sed i直接编辑，s替换，g全面替换

## if

<https://wangdoc.com/bash/condition.html>

### true or false

写法一

`test expression`

写法二
`[ expression ]`

写法三
`[[ expression ]]`

`[[ 'My long string' == *"My long"* ]]`

```bash
if commands; then
  commands
elif commands; then
  commands...
else
  commands
fi
```

### 文件是否存在

```bash
if [ ! -d "$var" ]; then
if [ ! -f ${var}.xsd ]; then
```

## awk

### 多字符串匹配

```bash
awk '/abc|123/' file
```

### 字符串函数

```bash
substr(str, start, l)
```

<https://www.tutorialspoint.com/awk/awk_string_functions.htm>

### 末尾1

无论匹配与否每行都 print

```bash
awk 'NR-6==0{$1=$1" "$1}1' POSCAR
```

<https://qastack.cn/unix/63891/what-is-the-meaning-of-1-at-the-end-of-awk-script>

### 正则匹配

```bash
awk '$1 ~ /^D/ {print NR}' POSCAR
awk '$1 !~ /^D/ {print NR}' POSCAR
```

`^` 首字符

<https://www.cnblogs.com/chengmo/archive/2010/10/11/1847772.html>

### skip blank line and line

```bash
awk '{
    if (!NF || $1 ~ /^#/)
        print $0;
    else 
        x;
}' xas.dat > xas.sft.dat
```

### 逻辑算符

`awk 'NR-8>=0 && NR-9<=0 {print NR}' POSCAR`

```
&&
||
```

### 直接编辑

```bash
awk 'NR-6==0{$1=$1" "$1}1' POSCAR > tmp && mv tmp POSCAR

#awk 4.1.0
awk -i inplace 'NR-6==0{$1=$1" "$1}1' file1
```

<https://stackoverflow.com/questions/16529716/save-modifications-in-place-with-awk>

### if

```bash
awk '{
    if (s){
        s;
        s
    };
    else if (s)
        s;
    else
        s;
    s
}' f
```

<https://blog.csdn.net/qq_31382921/article/details/55094907>

### 内建变量

NR: 按照记录分隔符读取的数据次数，默认的记录分隔符为换行符，因此默认的就是读取的数据行数
FNR: 每当处理一个新文件的时候，FNR就从1开始计数
NF: 目前的记录被分割的字段的数目
ORS: 输出分割符, 默认 /n

### loop

```bash
echo "1 2 3 4 5" | awk '{for(i=1;i<=NF;i++) sum+=$i} END{print "sum="sum}'
```

<https://zhidao.baidu.com/question/517933140.html>

### 数字比较

`awk 'NR-<=0'`

<https://www.cnblogs.com/children/archive/2012/06/28/2567665.html>

### 变量

```bash
var="abc"
awk 'BEGIN{print "'$var'"}'
var="this a test"
awk 'BEGIN{print "'"$var"'"}'
var="this a test"
awk -v awkVar="$var" 'BEGIN{print awkVar}'
```

<https://blog.csdn.net/rj042/article/details/72860177>

### 替换

```bash
awk '{$1=$1"abc"}1' test.dat
```

### printf

```sh
awk '{printf "%15.8f\n", $5/2}' a.out
```

## ubuntu换源

`ubuntumirror_test.sh`

```bash
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo sed -i 's/archive.ubuntu.com/ftp.sjtu.edu.cn/g' /etc/apt/sources.list
sudo sed -i 's/security.ubuntu.com/ftp.sjtu.edu.cn/g' /etc/apt/sources.list
sudo sed -i 's/#http/#https/g' /etc/apt/sources.list
do-release-upgrade
sudo apt update
sudo apt upgrade
```

## ssh

```bash
sudo apt install ssh
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

```
sudo vim /etc/ssh/sshd_config
```

```
Port 2222
PubkeyAuthentication yes
PasswordAuthentication yes
```

```sh
sudo service ssh start
ip addr
```

## dns

```shell
sudo apt install resolvconf
sudo vim /etc/resolvconf/resolv.conf.d/base
nameserver 8.8.8.8
sudo resolvconf -u
```

<https://www.cnblogs.com/ArsenalfanInECNU/p/11322602.html>
<https://blog.skk.moe/post/which-public-dns-to-use/>
<https://github.com/microsoft/WSL/issues/5420>

## find

### 避开目录

```shell
find test -path "test/test4" -prune -o -print
find test -path "test/test4" -a -prune -o -print #等价写法
find test \(-path test/test4 -o -path test/test3 \) -prune -o -name "*.log" -print #多目录
```

<https://www.cnblogs.com/peida/archive/2012/11/16/2773289.HTML>

### 第一次终止

```sh
find . ... -print -quit
```

<https://qastack.cn/unix/62880/how-to-stop-the-find-command-after-first-match>

### 不显示权限不足

```sh
find ./ -name '*libfftw3.a' 2>/dev/null
```

### -mindepth -maxdepth

```sh
find ./ -mindepth 3 -maxdepth 5 -name passwd
```

<https://blog.csdn.net/genziisme/article/details/78918495>

## grep

### 多字符匹配

```sh
grep -E '123|abc' filename
```

### 正则表达式

`^` 锚定行的开始 如：`'^grep'`匹配所有以grep开头的行。
`$` 锚定行的结束 如：`'grep$'`匹配所有以grep结尾的行。

<https://blog.csdn.net/deyili/article/details/5548603>

## Intel Oneapi

<https://software.intel.com/content/www/us/en/develop/articles/installing-intel-oneapi-toolkits-via-apt.html>

### version manage

`~/intel/oneapi/installer/installer`  
`sudo apt autoremove`

### 防止 python 退格乱码

`sudo apt install libreadline-dev`

`python -m pip install readline`

## convert

```sh
convert test.png -draw "font Candice font-size 100 fill dodgerblue  stroke navy  stroke-width 2 text 800,300 'Real'" test_o.png
```

## gif

### ase

```sh
ase gui POSCAR CONTCAR
```

<https://wiki.fysik.dtu.dk/ase/ase/gui/tools.html#render-scene>

### png2gif

```sh
convert -delay 100 temp.*.png temp.gif
```

### gif2png

```sh
convert -coalesce something.gif something.png
identify -verbose something.gif | grep 'Delay'
```

<https://tex.stackexchange.com/questions/240243/getting-gif-and-or-moving-images-into-a-latex-presentation>
<https://liam.page/2017/08/10/importing-animate-in-LaTeX/>

### mp42png

```sh
ffmpeg -ss 00:00:30 -to 00:00:40 -i test.mp4 test%04d.png
```

### 批量裁切

```sh
mogrify -crop +0+100 -crop -0-60 -format png -path new *.png

+left+top    -right-bottom
```

## git

### 构建

```shell
git config --global http.proxy http://

git clone https://github.com/LavendaRaphael/common.git
git clone https://github.com/LavendaRaphael/group.git
git clone https://github.com/LavendaRaphael/course.git
git config --global user.email "feifei.tian.cn@gmail.com"
git config --global user.name "LavendaRaphael"
git config --global -l
git config -l
git remote -v

git config --global --unset http.proxy
git config http.proxy socks://
```

### 维护

```shell
git clone -b release --depth 1000 https://github.com/plumed/plumed2.git plumed2
git status
git pull
git add .
git rm test
git commit -m "test"
git push
```

<https://docs.github.com/en/free-pro-team@latest/github/using-git/changing-a-remotes-url>

### contribution 不显示

<https://www.jianshu.com/p/82ee1c341456>

### 撤销commit

```shell
git reset HEAD^
```

<https://www.cnblogs.com/lfxiao/p/9378763.html>

## alias

```sh
shopt -s expand_aliases
if true;then
 alias echo_hello="echo Hello!"
fi
if true;then
 echo_hello
fi
```

<https://unix.stackexchange.com/questions/531960/why-doesnt-alias-work-inside-if>

<https://www.cnblogs.com/fnlingnzb-learner/p/10649971.html>

### chmod递归权限

```sh
chmod -R 700 tianff/
```

### 截取snapshot

```sh
more +2034867 water.pos|head -n 97 >> POSCAR
```

### bash

```sh
du -h --max-depth=1 #文件夹占用磁盘大小
```

### pbs

```sh
qstat -ls
bjobs
pestat |grep SBP
qselect -u <username> | xargs qdel
```

### bash, mv不包括

```sh
shopt -s extglob
cp -r !(Filename1 | FoldernameX | Filename2) Dest/
screen -dmS name
screen -ls
screen -r name
```

<https://www.ibm.com/developerworks/cn/linux/l-cn-nohup/index.html> #screen

```sh
printf "crystal_%03d" $x #格式输出001

ls a*/t.d #通配符
head t.d
clear #清屏
sz #下载
rz #上传
more #逐页显示文件内容
cp ../e.f90 . #拷贝到当前目录
gfortran e.f90 -o e.x #编译fortran
cd #进入用户主目录
cd - #返回进入此目录之前所在的目录
pwd #显示当前目录
grep ! scf.out | tail -1 #管道
printf "%5.4f\n","123.12345" #“%5.4lf”指定输出宽度为5，精度为4，由于实际长度超过5故应该按实际位数输出，小数位数超过4位部分被截去。
mpif90 test.f90 -o test.x -llapack #链接静态库
diff log2014.log log2013.log -yw #文件内容比较
```

## tar

压　缩：`tar -jcv -f filename.tar.bz2 要被压缩的文件或目录名称`
查　询：`tar -jtv -f filename.tar.bz2`
解压缩：`tar -jxv -f filename.tar.bz2 -C 欲解压缩的目录`
`-j`  ：透过 bzip2 的支持进行压缩/解压缩：此时档名最好为`*.tar.bz2`
`-z`  ：透过 gzip  的支持进行压缩/解压缩：此时档名最好为`*.tar.gz`
`-v`  #Verbosely list files processed.
`-c`  #压缩
`-t`  #查询
`-f`  #压缩文件
<http://cn.linux.vbird.org/linux_basic/0240tarcompress.php>

```sh
tar -ztvf /root/etc.tar.gz | grep 'shadow'
tar -zxvf /root/etc.tar.gz etc/shadow
```

## 杂项

### case

```sh
case expression in  
    pattern_1)  
        statements  
        ;;  
    pattern_2)  
        statements  
        ;;  
    pattern_3|pattern_4|pattern_5)  
        statements  
        ;;  
    pattern-n)  
        statements  
        ;;  
    *)  
        statements  
        ;;  
esac
```

### sort

去重

```sh
cat test
a
b
a
sort -u test
a
b
```

### array

#### for

```sh
x=(0 1 2)
for i in ${x[@]}

x='0 1 2'
for i in $x
```

#### max

```sh
echo ${#x[@]}
```

#### seq

```sh
x=$(seq 0 0.001 0.01)
```

#### star

```sh
ls
$ f1 f2

x=(f*)
echo ${x}
$ f1

x=(f\*)
echo ${x}
$ f1 f2
```

### 退格乱码

#### python

```sh
sudo apt install libreadline-dev
```

<https://blog.csdn.net/weixin_45309916/article/details/108758168>

#### bash read

```sh
stty erase ^H
```

<https://blog.imdst.com/bash-shell-tui-ge-jian-luan-ma/>

### 中止

```sh
exit
```

### 判断

```sh
true
```

### while

```sh
while true
do

done
```

### 传参

```sh
$1
```

`shift` 参数减一

### 奇怪字符

```sh
cat -v test.sh #查看
cat old_filename | tr -d "\r" > new_filename 行尾 ^M 替换

sed 's/<copy and paste>/<type what you want>/g' -i <datfile> #普遍替换
```

### 提取目录名

```sh
dirname a/b
basename a/b
```

### root

`sudo -s` 打开root shell
`su`      切换到root

### zip

```sh
zip -r filename.zip folder
```

### calculation

```sh
answer=$(((3 / 2) + (3 % 2 > 0))) #取整
```

#### bc

```sh
bc <<< "3.4+7/8-(5.94*3.14)"
echo "scal=4;0.0527*$x+1"|bc
```

#### minus

```sh
bc <<< "(-1)-(-1)"
```

### 字符串截取

```sh
${string: start :length} 从 string 字符串的左边第 start 个字符开始，向右截取 length 个字符。
${string: start} 从 string 字符串的左边第 start 个字符开始截取，直到最后。
${string: 0-start :length} 从 string 字符串的右边第 start 个字符开始，向右截取 length 个字符。
${string: 0-start} 从 string 字符串的右边第 start 个字符开始截取，直到最后。
${string#*chars} 从 string 字符串第一次出现*chars 的位置开始，截取 *chars 右边的所有字符。
${string##*chars} 从 string 字符串最后一次出现 *chars 的位置开始，截取*chars 右边的所有字符。
${string%chars*} 从 string 字符串第一次出现*chars 的位置开始，截取 *chars 左边的所有字符。
${string%%chars*} 从 string 字符串最后一次出现 *chars 的位置开始，截取*chars 左边的所有字符。
```

<http://c.biancheng.net/view/1120.html>

<https://kodango.com/a-strange-echo-result>

### 查杀进程

```sh
ll /proc/PID
kill -s 9 PID
```

<https://blog.csdn.net/spring21st/article/details/50561550>

### bashrc

#### 问题

SFTP无法连接

#### 来源

`.bashrc`中存在`echo`导致scp和sftp连接失败

#### 解决

```sh
if [ $TERM == "xterm" ] || [ $TERM == "xterm-256color" ]; then
  cat ~/0example/README
fi
```

<https://qastack.cn/server/485487/use-bashrc-without-breaking-sftp>

### screen

<https://www.cnblogs.com/mchina/archive/2013/01/30/2880680.html>

```sh
screen -S yourname -> 新建一个叫yourname的session
screen -ls -> 列出当前所有的session
screen -r yourname -> 回到yourname这个session
screen -d -r yourname -> 结束当前session并回到yourname这个session
C-a d -> detach，暂时离开当前session，将目前的 screen session (可能含有多个 windows) 丢到后台执行，并会回到还没进 screen 时的状态，此时在 screen session 里，每个 window 内运行的 process (无论是前台/后台)都在继续执行，即使 logout 也不影响。
```

### chmod

```
4 r
2 w
1 x
750 drwxr-x--- dir
640 -rw-r----- other
750 -rwxr-x--- .sh
```
