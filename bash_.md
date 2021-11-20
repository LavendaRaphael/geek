#  font
  
  
```bash
sudo cp -r windowsfont/ /usr/local/share/fonts/
sudo fc-cache -f
fc-match Arial
```
  
<https://askubuntu.com/questions/651441/how-to-install-arial-font-and-other-windows-fonts-in-ubuntu>
  
`C:\Windows\Fonts\`
  
#  loop
  
  
##  array
  
  
```bash
x=(0 1 2)
for i in ${x[@]}
  
x='0 1 2'
for i in $x
  
break [n]
continue [n]
```
  
#  apt
  
  
##  basic
  
  
```bash
apt-cache search
apt-cache show <packname>
sudo apt update
sudo apt upgrade
sudo apt remove <>
```
  
#  x11
  
  
##  VcXsrv
  
  
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
去勾选 Native opengl
  
#  赋值
  
  
##  缺省
  
  
`<img src="https://latex.codecogs.com/gif.latex?{a-defaultvalue}`a如果没有定义，则表达式返回默认值，否则返回a的值；`"/>{a:-defaultvalue}`
a没有定义或者为空字符串，则表达式返回默认值，否则返回a的值；
  
##  赋值
  
  
```bash
$()
  
``
```
  
#  vim
  
  
##  替换
  
  
`:%s/old/new/g` 文本替换
  
对特殊字符诸如`<img src="https://latex.codecogs.com/gif.latex?%%20[%20]%20.`等都需要在前面加上转义才可以。注意替换中只需要在需要被查找的部分加上转义字符，后面替换的内容不用加。##%20%20全局替换缩进```vim:set%20ts=8%20sts=8%20noet%20%20%20%20设置tab格数:retab!%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20空格替换为tab:set%20ts=4%20sts=4%20et%20%20%20%20%20%20更换tab个数:retab%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20tab替换空格```&lt;https:&#x2F;&#x2F;www.itranslater.com&#x2F;qa&#x2F;details&#x2F;2123239368239350784&gt;##%20%20杂项```:scriptnames%20#查看配置文件载入列表:set%20textwidth=0%20#禁用自动换行p%20#粘贴y%20#复制v%20#选择````:let%20i=0%20|%20g&#x2F;zcc&#x2F;s&#x2F;&#x2F;&#x5C;=i&#x2F;%20|%20let%20i=i+1`行编号，zcc为替换点#%20%20sed##%20%20行替换`sed%20-i%20&quot;2c%20hello&quot;%20POSCAR`&lt;https:&#x2F;&#x2F;blog.51cto.com&#x2F;xficc&#x2F;1621403&gt;##%20%20替换`sed%20-i%20&#x27;s&#x2F;book&#x2F;books&#x2F;g&#x27;%20file`sed%20i直接编辑，s替换，g全面替换#%20%20if&lt;https:&#x2F;&#x2F;wangdoc.com&#x2F;bash&#x2F;condition.html&gt;##%20%20true%20or%20false写法一`test%20expression`写法二`[%20expression%20]`写法三`[[%20expression%20]]``[[%20&#x27;My%20long%20string&#x27;%20==%20*&quot;My%20long&quot;*%20]]````bashif%20commands;%20then%20%20commandselif%20commands;%20then%20%20commands...else%20%20commandsfi```##%20%20文件是否存在```bashif%20[%20!%20-d%20&quot;"/>var" ]; then
if [ ! -f <img src="https://latex.codecogs.com/gif.latex?{var}.xsd%20];%20then```#%20%20awk##%20%20多字符串匹配```bashawk%20&#x27;&#x2F;abc|123&#x2F;&#x27;%20file```##%20%20字符串函数```bashsubstr(str,%20start,%20l)```&lt;https:&#x2F;&#x2F;www.tutorialspoint.com&#x2F;awk&#x2F;awk_string_functions.htm&gt;##%20%20末尾1无论匹配与否每行都%20print```bashawk%20&#x27;NR-6==0{"/>1=<img src="https://latex.codecogs.com/gif.latex?1&quot;%20&quot;"/>1}1' POSCAR
```
  
<https://qastack.cn/unix/63891/what-is-the-meaning-of-1-at-the-end-of-awk-script>
  
##  正则匹配
  
  
awk '$1 ~ /^D/ {print NR}' POSCAR
awk '$1 !~ /^D/ {print NR}' POSCAR
  
^ 首字符
  
<https://www.cnblogs.com/chengmo/archive/2010/10/11/1847772.html>
  
##  skip blank line and line
  
  
```bash
awk '{
    if (!NF || $1 ~ /^#/)
        print $0;
    else 
        x;
}' xas.dat > xas.sft.dat
```
  
##  逻辑算符
  
  
`awk 'NR-8>=0 && NR-9<=0 {print NR}' POSCAR`
  
```
&&
||
```
  
##  直接编辑
  
  
```bash
awk 'NR-6==0{$1=$1" "$1}1' POSCAR > tmp && mv tmp POSCAR
  
#awk 4.1.0
awk -i inplace 'NR-6==0{$1=$1" "$1}1' file1
```
  
<https://stackoverflow.com/questions/16529716/save-modifications-in-place-with-awk>
  
##  if
  
  
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
  
##  内建变量
  
  
NR: 按照记录分隔符读取的数据次数，默认的记录分隔符为换行符，因此默认的就是读取的数据行数
FNR: 每当处理一个新文件的时候，FNR就从1开始计数
NF: 目前的记录被分割的字段的数目
ORS: 输出分割符, 默认 /n
  
##  loop
  
  
```bash
echo "1 2 3 4 5" | awk '{for(i=1;i<=NF;i++) sum+=$i} END{print "sum="sum}'
```
  
<https://zhidao.baidu.com/question/517933140.html>
  
##  数字比较
  
  
`awk 'NR-<=0'`
  
<https://www.cnblogs.com/children/archive/2012/06/28/2567665.html>
  
##  变量
  
  
```bash
var="abc"
awk 'BEGIN{print "'$var'"}'
var="this a test"
awk 'BEGIN{print "'"$var"'"}'
var="this a test"
awk -v awkVar="$var" 'BEGIN{print awkVar}'
```
  
<https://blog.csdn.net/rj042/article/details/72860177>
  
##  替换
  
  
awk '{<img src="https://latex.codecogs.com/gif.latex?1="/>1"abc"}1' test.dat
  
##  printf
  
  
awk '{printf "%15.8f\n", <img src="https://latex.codecogs.com/gif.latex?5&#x2F;2}&#x27;%20a.out#%20%20wsl2##%20%20安装&lt;https:&#x2F;&#x2F;docs.microsoft.com&#x2F;en-us&#x2F;windows&#x2F;wsl&#x2F;install&gt;##%20%20文件系统权限```bashsudo%20vim%20&#x2F;etc&#x2F;wsl.conf``````conf[automount]enabled%20=%20trueroot%20=%20&#x2F;mnt&#x2F;options%20=%20&quot;metadata,umask=22,fmask=11&quot;mountFsTab%20=%20false```&lt;https:&#x2F;&#x2F;www.jianshu.com&#x2F;p&#x2F;f9efb4c1e0bb&gt;##%20%20wsl命令```powershellwsl%20-helpwsl%20-l%20-vwsl%20--updatewsl%20--shutdown```##%20%20link```bashln%20-s%20&#x2F;mnt&#x2F;c&#x2F;Users&#x2F;feife&#x2F;OneDrive&#x2F;group%20~&#x2F;groupln%20-s%20&#x2F;mnt&#x2F;c&#x2F;Users&#x2F;feife&#x2F;OneDrive&#x2F;arxive%20~&#x2F;arxiveln%20-s%20&#x2F;mnt&#x2F;c&#x2F;Users&#x2F;feife&#x2F;OneDrive&#x2F;arxive&#x2F;myscript&#x2F;server.me.sh%20~&#x2F;server.me.shln%20-s%20&#x2F;mnt&#x2F;c&#x2F;Users&#x2F;feife&#x2F;OneDrive&#x2F;mytemp%20~&#x2F;mytemp```##%20%20ubuntu换源`~&#x2F;arxive&#x2F;myscript&#x2F;os_repo_speed_test.sh````bashsudo%20cp%20&#x2F;etc&#x2F;apt&#x2F;sources.list%20&#x2F;etc&#x2F;apt&#x2F;sources.list.baksudo%20sed%20-i%20&#x27;s&#x2F;archive.ubuntu.com&#x2F;ftp.sjtu.edu.cn&#x2F;g&#x27;%20&#x2F;etc&#x2F;apt&#x2F;sources.listsudo%20sed%20-i%20&#x27;s&#x2F;security.ubuntu.com&#x2F;ftp.sjtu.edu.cn&#x2F;g&#x27;%20&#x2F;etc&#x2F;apt&#x2F;sources.listsudo%20sed%20-i%20&#x27;s&#x2F;#http&#x2F;#https&#x2F;g&#x27;%20&#x2F;etc&#x2F;apt&#x2F;sources.listdo-release-upgradesudo%20apt%20updatesudo%20apt%20upgrade```##%20%20ssh###%20%20sshd_conf```bashsudo%20apt%20install%20sshsudo%20cp%20&#x2F;etc&#x2F;ssh&#x2F;sshd_config%20&#x2F;etc&#x2F;ssh&#x2F;sshd_config.bak``````sudo%20vim%20&#x2F;etc&#x2F;ssh&#x2F;sshd_config``````Port%202222PubkeyAuthentication%20yesPasswordAuthentication%20yes```sudo%20service%20ssh%20startip%20addr###%20%20ssh自启&amp;外部局域网访问```bashsudo%20vim%20&#x2F;etc&#x2F;init.wsl``````bash#!&#x2F;bin&#x2F;bashservice%20ssh%20start``````bashsudo%20chmod%20700%20&#x2F;etc&#x2F;init.wsl```&lt;https:&#x2F;&#x2F;juejin.im&#x2F;post&#x2F;6847902218226499598&gt;ps脚本可执行```powershellSet-ExecutionPolicy%20-ExecutionPolicy%20Bypass%20-Scope%20CurrentUser```windows-%20计算机管理%20-%20任务计划程序%20-%20任务计划程序库%20-%20新文件夹%20&#x27;me&#x27;%20-%20导入%20`C:&#x5C;Users&#x5C;laven&#x5C;OneDrive&#x5C;arxive&#x5C;myscript&#x5C;ubuntu.xml`&lt;https:&#x2F;&#x2F;docs.microsoft.com&#x2F;zh-cn&#x2F;powershell&#x2F;module&#x2F;microsoft.powershell.core&#x2F;about&#x2F;about_execution_policies?view=powershell-7.1&gt;&lt;https:&#x2F;&#x2F;www.zhihu.com&#x2F;question&#x2F;40596907&gt;&lt;https:&#x2F;&#x2F;gist.github.com&#x2F;daehahn&#x2F;497fa04c0156b1a762c70ff3f9f7edae&gt;&lt;https:&#x2F;&#x2F;www.hanselman.com&#x2F;blog&#x2F;how-to-ssh-into-wsl2-on-windows-10-from-an-external-machine&gt;##%20%20screen```shellsudo%20screensudo%20chmod%20777%20&#x2F;run&#x2F;screen&#x2F;```&lt;https:&#x2F;&#x2F;github.com&#x2F;microsoft&#x2F;WSL&#x2F;issues&#x2F;1245&gt;##%20%20latexworkshop```bashvim%20.profile``````bashexport%20PATH=~&#x2F;software&#x2F;texlive&#x2F;2021&#x2F;bin&#x2F;x86_64-linux:"/>PATH
```
  
<https://github.com/James-Yu/LaTeX-Workshop/wiki/Install#using-wsl>
  
##  dns
  
  
```shell
sudo apt install resolvconf
sudo vim /etc/resolvconf/resolv.conf.d/base
nameserver 8.8.8.8
sudo resolvconf -u
```
  
<https://www.cnblogs.com/ArsenalfanInECNU/p/11322602.html>
<https://blog.skk.moe/post/which-public-dns-to-use/>
<https://github.com/microsoft/WSL/issues/5420>
  
#  find
  
  
##  避开目录
  
  
```shell
find test -path "test/test4" -prune -o -print
find test -path "test/test4" -a -prune -o -print #等价写法
find test \(-path test/test4 -o -path test/test3 \) -prune -o -name "*.log" -print #多目录
```
  
<https://www.cnblogs.com/peida/archive/2012/11/16/2773289.HTML>
  
##  第一次终止
  
  
find . ... -print -quit
  
<https://qastack.cn/unix/62880/how-to-stop-the-find-command-after-first-match>
  
##  不显示权限不足
  
  
find ./ -name '*libfftw3.a' 2>/dev/null
  
##  -mindepth -maxdepth
  
  
find ./ -mindepth 3 -maxdepth 5 -name passwd
  
<https://blog.csdn.net/genziisme/article/details/78918495>
  
#  grep
  
  
##  多字符匹配
  
  
grep -E '123|abc' filename
  
##  正则表达式
  
  
^ 锚定行的开始 如：'^grep'匹配所有以grep开头的行。
<img src="https://latex.codecogs.com/gif.latex?锚定行的结束%20如：&#x27;grep"/>'匹配所有以grep结尾的行。
  
<https://blog.csdn.net/deyili/article/details/5548603>
  
#  Intel Oneapi
  
  
<https://software.intel.com/content/www/us/en/develop/articles/installing-intel-oneapi-toolkits-via-apt.html>
  
##  local uninstall
  
  
`~/intel/oneapi/installer/installer`
  
##  防止 python 退格乱码
  
  
`sudo apt install libreadline-dev`
  
`python -m pip install readline`
  
#  convert
  
  
convert test.png -draw "font Candice font-size 100 fill dodgerblue  stroke navy  stroke-width 2 text 800,300 'Real'" test_o.png
  
#  gif
  
  
##  ase
  
  
ase gui POSCAR CONTCAR
  
<https://wiki.fysik.dtu.dk/ase/ase/gui/tools.html#render-scene>
  
##  png2gif
  
  
convert -delay 100 temp.*.png temp.gif
  
##  gif2png
  
  
convert -coalesce something.gif something.png
identify -verbose something.gif | grep 'Delay'
  
<https://tex.stackexchange.com/questions/240243/getting-gif-and-or-moving-images-into-a-latex-presentation>
<https://liam.page/2017/08/10/importing-animate-in-LaTeX/>
  
##  mp42png
  
  
ffmpeg -ss 00:00:30 -to 00:00:40 -i test.mp4 test%04d.png
  
##  批量裁切
  
  
mogrify -crop +0+100 -crop -0-60 -format png -path new *.png
  
+left+top    -right-bottom
  
#  git
  
  
##  构建
  
  
```shell
# mypc
git config --global http.proxy http://10.20.221.131:10808
# grouppc
git config --global http.proxy http://10.19.51.34:10809
  
git clone https://github.com/LavendaRaphael/common.git
git clone https://github.com/LavendaRaphael/group.git
git clone https://github.com/LavendaRaphael/course.git
git config --global user.email "feifei.tian.cn@gmail.com"
git config --global user.name "LavendaRaphael"
git config --global -l
git config -l
git remote -v
  
git config --global --unset http.proxy
git config http.proxy socks://10.19.51.34:10808
```
  
##  维护
  
  
```shell
git status
git pull
git add .
git rm test
git commit -m "test"
git push
```
  
<https://docs.github.com/en/free-pro-team@latest/github/using-git/changing-a-remotes-url>
  
##  contribution 不显示
  
  
<https://www.jianshu.com/p/82ee1c341456>
  
  
##  撤销commit
  
  
```shell
git reset HEAD^
```
  
<https://www.cnblogs.com/lfxiao/p/9378763.html>
  
#  alias
  
  
shopt -s expand_aliases
if true;then
 alias echo_hello="echo Hello!"
fi
if true;then
 echo_hello
fi
  
<https://unix.stackexchange.com/questions/531960/why-doesnt-alias-work-inside-if>
  
<https://www.cnblogs.com/fnlingnzb-learner/p/10649971.html>
  
##  chmod递归权限
  
  
chmod -R 700 tianff/
  
##  截取snapshot
  
  
more +2034867 water.pos|head -n 97 >> POSCAR
  
##  linux, bug
  
  
*error：ssh频频中断
*solution：
source environment.sh
environment.sh: set -eo pipefial
  
##  bash
  
  
du -h --max-depth=1 #文件夹占用磁盘大小
  
##  pbs
  
  
qstat -ls
bjobs
pestat |grep SBP
qselect -u <username> | xargs qdel
  
##  bash, mv不包括
  
  
{
shopt -s extglob
cp -r !(Filename1 | FoldernameX | Filename2) Dest/
}
screen -dmS name
screen -ls
screen -r name
<https://www.ibm.com/developerworks/cn/linux/l-cn-nohup/index.html> #screen
printf "crystal_%03d" <img src="https://latex.codecogs.com/gif.latex?x%20#格式输出001ls%20a*&#x2F;t.d%20通配符head%20t.dclear%20清屏sz%20下载rz%20上传more%20逐页显示文件内容cp%20..&#x2F;e.f90%20.%20#拷贝到当前目录gfortran%20e.f90%20-o%20e.x%20#编译fortrancd%20#进入用户主目录cd%20-%20#返回进入此目录之前所在的目录pwd%20#显示当前目录grep%20!%20scf.out%20|%20tail%20-1%20#管道printf%20&quot;%5.4f&#x5C;n&quot;,&quot;123.12345&quot;%20#“%5.4lf”指定输出宽度为5，精度为4，由于实际长度超过5故应该按实际位数输出，小数位数超过4位部分被截去。mpif90%20test.f90%20-o%20test.x%20-llapack%20#链接静态库diff%20log2014.log%20log2013.log%20-yw%20#文件内容比较#%20%20tar压　缩：tar%20-jcv%20-f%20filename.tar.bz2%20要被压缩的文件或目录名称查　询：tar%20-jtv%20-f%20filename.tar.bz2解压缩：tar%20-jxv%20-f%20filename.tar.bz2%20-C%20欲解压缩的目录-j%20%20：透过%20bzip2%20的支持进行压缩&#x2F;解压缩：此时档名最好为*.tar.bz2-z%20%20：透过%20gzip%20%20的支持进行压缩&#x2F;解压缩：此时档名最好为*.tar.gz-v%20%20#Verbosely%20list%20files%20processed.-c%20%20#压缩-t%20%20#查询-f%20%20#压缩文件&lt;http:&#x2F;&#x2F;cn.linux.vbird.org&#x2F;linux_basic&#x2F;0240tarcompress.php&gt;tar%20-ztvf%20&#x2F;root&#x2F;etc.tar.gz%20|%20grep%20&#x27;shadow&#x27;tar%20-zxvf%20&#x2F;root&#x2F;etc.tar.gz%20etc&#x2F;shadow#%20%20LAMMPS&lt;https:&#x2F;&#x2F;github.com&#x2F;lammps&#x2F;lammps&#x2F;blob&#x2F;master&#x2F;cmake&#x2F;README.md#building-with-intel-compilers&gt;mkdir%20lammps&#x2F;buildcd%20lammps&#x2F;buildcmake%20[-D%20OPTION_A=VALUE_A%20-D%20OPTION_B=VALUE_B%20...]%20..&#x2F;cmakemakeBuilding%20with%20Intel%20Compilerscmake%20-D%20CMAKE_C_COMPILER=icc%20-D%20CMAKE_CXX_COMPILER=icpc%20-D%20CMAKE_Fortran_COMPILER=ifort%20..&#x2F;cmakecmake%20-D%20FFT=KISS%20-C%20..&#x2F;cmake&#x2F;presets&#x2F;minimal.cmake%20-D%20CMAKE_C_COMPILER=icc%20-D%20CMAKE_CXX_COMPILER=icpc%20-D%20CMAKE_Fortran_COMPILER=ifort%20..&#x2F;cmake#%20%20杂项##%20%20casecase%20expression%20in%20%20%20%20%20%20pattern_1)%20%20%20%20%20%20%20%20%20%20statements%20%20%20%20%20%20%20%20%20%20;;%20%20%20%20%20%20pattern_2)%20%20%20%20%20%20%20%20%20%20statements%20%20%20%20%20%20%20%20%20%20;;%20%20%20%20%20%20pattern_3|pattern_4|pattern_5)%20%20%20%20%20%20%20%20%20%20statements%20%20%20%20%20%20%20%20%20%20;;%20%20%20%20%20%20pattern-n)%20%20%20%20%20%20%20%20%20%20statements%20%20%20%20%20%20%20%20%20%20;;%20%20%20%20%20%20*)%20%20%20%20%20%20%20%20%20%20statements%20%20%20%20%20%20%20%20%20%20;;%20%20esac##%20%20sort去重cat%20test&gt;%20a&gt;%20b&gt;%20asort%20-u%20test&gt;%20a&gt;%20b##%20%20array###%20%20forx=(0%201%202)for%20i%20in"/>{x[@]}
  
x='0 1 2'
for i in <img src="https://latex.codecogs.com/gif.latex?x###%20%20maxecho"/>{#x[@]}
  
###  seq
  
  
x=<img src="https://latex.codecogs.com/gif.latex?(seq%200%200.001%200.01)###%20%20star```ls"/> f1 f2
  
x=(f*)
echo <img src="https://latex.codecogs.com/gif.latex?{x}"/> f1
  
x=(f\*)
echo <img src="https://latex.codecogs.com/gif.latex?{x}"/> f1 f2
```
  
##  退格乱码
  
  
###  python
  
  
sudo apt install libreadline-dev
  
<https://blog.csdn.net/weixin_45309916/article/details/108758168>
  
###  bash read
  
  
stty erase ^H
  
<https://blog.imdst.com/bash-shell-tui-ge-jian-luan-ma/>
  
##  中止
  
  
exit
  
##  判断
  
  
true
  
##  while
  
  
while true
do
  
done
  
##  传参
  
  
```
<img src="https://latex.codecogs.com/gif.latex?1```shift%20参数减一##%20%20奇怪字符```cat%20-v%20test.sh%20#查看cat%20old_filename%20|%20tr%20-d%20&quot;&#x5C;r&quot;%20&gt;%20new_filename%20行尾%20^M%20替换sed%20&#x27;s&#x2F;&lt;copy%20and%20paste&gt;&#x2F;&lt;type%20what%20you%20want&gt;&#x2F;g&#x27;%20-i%20&lt;datfile&gt;%20#普遍替换```##%20%20提取目录名dirname%20a&#x2F;bbasename%20a&#x2F;b##%20%20rootsudo%20-s%20打开root%20shellsu%20%20%20%20%20%20切换到root##%20%20zipzip%20-r%20filename.zip%20folder##%20%20calculationanswer="/>(((3 / 2) + (3 % 2 > 0))) #取整
  
###  bc
  
  
bc <<< "3.4+7/8-(5.94*3.14)"
echo "scal=4;0.0527*<img src="https://latex.codecogs.com/gif.latex?x+1&quot;|bc###%20%20minusbc%20&lt;&lt;&lt;%20&quot;(-1)-(-1)&quot;##%20%20字符串截取```"/>{string: start :length} 从 string 字符串的左边第 start 个字符开始，向右截取 length 个字符。
<img src="https://latex.codecogs.com/gif.latex?{string:%20start}%20从%20string%20字符串的左边第%20start%20个字符开始截取，直到最后。"/>{string: 0-start :length} 从 string 字符串的右边第 start 个字符开始，向右截取 length 个字符。
<img src="https://latex.codecogs.com/gif.latex?{string:%200-start}%20从%20string%20字符串的右边第%20start%20个字符开始截取，直到最后。"/>{string#*chars} 从 string 字符串第一次出现*chars 的位置开始，截取 *chars 右边的所有字符。
<img src="https://latex.codecogs.com/gif.latex?{string##*chars}%20从%20string%20字符串最后一次出现%20*chars%20的位置开始，截取*chars%20右边的所有字符。"/>{string%chars*} 从 string 字符串第一次出现*chars 的位置开始，截取 *chars 左边的所有字符。
<img src="https://latex.codecogs.com/gif.latex?{string%%chars*}%20从%20string%20字符串最后一次出现%20*chars%20的位置开始，截取*chars%20左边的所有字符。```&lt;http:&#x2F;&#x2F;c.biancheng.net&#x2F;view&#x2F;1120.html&gt;&lt;https:&#x2F;&#x2F;kodango.com&#x2F;a-strange-echo-result&gt;##%20%20查杀进程ll%20&#x2F;proc&#x2F;PIDkill%20-s%209%20PID&lt;https:&#x2F;&#x2F;blog.csdn.net&#x2F;spring21st&#x2F;article&#x2F;details&#x2F;50561550&gt;##%20%20bashrc###%20%20问题SFTP无法连接###%20%20来源.bashrc中存在echo导致scp和sftp连接失败###%20%20解决```if%20["/>TERM == "xterm" ] || [ $TERM == "xterm-256color" ]; then
  cat ~/0example/README
fi
```
  
  
<https://qastack.cn/server/485487/use-bashrc-without-breaking-sftp>
  
##  screen
  
  
<https://www.cnblogs.com/mchina/archive/2013/01/30/2880680.html>
  
screen -S yourname -> 新建一个叫yourname的session
screen -ls -> 列出当前所有的session
screen -r yourname -> 回到yourname这个session
screen -d -r yourname -> 结束当前session并回到yourname这个session
C-a d -> detach，暂时离开当前session，将目前的 screen session (可能含有多个 windows) 丢到后台执行，并会回到还没进 screen 时的状态，此时在 screen session 里，每个 window 内运行的 process (无论是前台/后台)都在继续执行，即使 logout 也不影响。
  
##  chmod
  
  
4 r
2 w
1 x
750 drwxr-x--- dir
640 -rw-r----- other
750 -rwxr-x--- .sh
  