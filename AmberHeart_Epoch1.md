# CFC Studio 共学 Epoch1 指引
---
# [AmberHeart]

## 笔记证明

<!-- Content_START -->

### 01.11

#### 今日学习时间:40min
#### 学习内容小结:Windows和Linux的差异,很大


Let's study Shell!


先前有在Windows尝试用过PowerShell，大概是Shell的一种分支?


终端→显示Shell的窗口


拓展联想：cmd属于shell的一种吗?查找后：√


your platform plus like 'terminal' 发现已有打开后是类似powershell的界面?


该查找cmd,powerShell,terminal三者间的区别了


区别大概是：

①PowerShell以系统性管理任务进程为主,而Windows terminal则属于终端模拟器应用程序？

②PowerShell侧重于管理,Windows terminal则以开发,模拟环境为主？

test

①尝试使用echo输出带有空格的字符串

②尝试使用‘+’

③执行echo 283 + pro 输出如下

>283

>+

>pro

思考:echo的执行是将变量自前向后依次输出？

查找后发现用法近似感觉像是Python中的print,也可以执行程序


执行echo $path无输出

>查找后发现windows系统应执行echo $ENv:path

>输出成功


执行which echo报错

>which为linux命令

>查找后发现Windows类似命令Get-command

>输出成功


执行cd /home报错

>估计是绝对路径下linux与windows文件夹不同产生的差异问题,不打算进一步查询


执行cd -报错

>linux与windows的差异问题 老实用绝对路径回去了


执行ls -l报错

>老套的差异问题 查到-LiteralPath似乎有近似作用但是需要参数


执行ls 出现以下内容

>d-----      ...

>d-----      ...

>d-r---      ...

>dar---      ...

>d-r---      ...

>dar--l      ...

不同于linux的前缀 查找后发现下列关系

d 目录

r 可读

w 可写

a 全体用户

吧大概

l什么意思没查到就是了


总结:大部分时间和精力花在了解决Linux与Windows的系统差异上,等安装wsl整好bash后提速应该就会很快了,总之摸鱼摸爽了

总结:摸了

### 01.12

#### 今日学习时间：90min
#### 学习内容小结：感觉还行
#### 问题：作业中最后一part里：记事本中无内容的原因是什么（大致代码如下）
```bash
SHHis@AmberHeart:/tmp# cat ./missing/semester.txt | grep -i last-modified | cut --delimiter=":" -f2 >> ./last-modified.txt
SHHis@AmberHeart:/tmp# cat last-modified.txt
```

#### 以下是今天的学习内容

配置了wsl,大概能够试着以Linux的环境进行后续学习了

先试着找了找路径在哪

>root@AmberHeart:~# cd ..
>root@AmberHeart:/# ls
>bin   dev  home  lib    lib64   lost+found  mnt  proc  run   snap  sys  usr
>boot  etc  init  lib32  libx32  media       opt  root  sbin  srv   tmp  var

大概是知道了,但是上课神游好奇@前面的root能不能改名

查了下要用gedit,装了下改了下好了<br><br>

然后顺带学了一点markdown的语法,接下来试着用自己喜欢的格式做笔记<br><br>

```bash
SHHis@AmberHeart:~# cd -
-bash: cd: OLDPWD not set
SHHis@AmberHeart:~# echo hello
hello
SHHis@AmberHeart:~# echo nichika > SHHis.txt
SHHis@AmberHeart:~# cat SHHis.txt
nichika
SHHis@AmberHeart:~# cat < SHHis.txr
-bash: SHHis.txr: No such file or directory
SHHis@AmberHeart:~# cat < SHHis.txt
nichika
SHHis@AmberHeart:~# cat < SHHis.txt > CoMETIK.txt
```
所以执行的方式类似于从左到右的顺序?

```bash
SHHis@AmberHeart:~# ls -l
total 20
drwxr-xr-x 2 root root 4096 Jan 13 00:38 283
drwxr-xr-x 2 root root 4096 Jan 13 00:41 283pro
-rw-r--r-- 1 root root    8 Jan 13 01:00 CoMETIK.txt
-rw-r--r-- 1 root root   16 Jan 13 01:02 SHHis.txt
drwx------ 4 root root 4096 Jan 13 00:50 snap
SHHis@AmberHeart:~# ls -l /
total 2272
lrwxrwxrwx   1 root root       7 May 31  2023 bin -> usr/bin
drwxr-xr-x   2 root root    4096 May 31  2023 boot
drwxr-xr-x  16 root root    3540 Jan 13 00:50 dev
drwxr-xr-x  99 root root    4096 Jan 13 00:53 etc
drwxr-xr-x   2 root root    4096 Apr 15  2020 home
-rwxrwxrwx   1 root root 2260248 Nov 10 00:26 init
lrwxrwxrwx   1 root root       7 May 31  2023 lib -> usr/lib
lrwxrwxrwx   1 root root       9 May 31  2023 lib32 -> usr/lib32
lrwxrwxrwx   1 root root       9 May 31  2023 lib64 -> usr/lib64
lrwxrwxrwx   1 root root      10 May 31  2023 libx32 -> usr/libx32
drwx------   2 root root   16384 Jan 13 00:31 lost+found
drwxr-xr-x   2 root root    4096 May 31  2023 media
drwxr-xr-x   6 root root    4096 Jan 13 00:31 mnt
drwxr-xr-x   2 root root    4096 May 31  2023 opt
dr-xr-xr-x 301 root root       0 Jan 13 00:32 proc
drwx------   7 root root    4096 Jan 13 01:00 root
drwxr-xr-x  24 root root     740 Jan 13 00:49 run
lrwxrwxrwx   1 root root       8 May 31  2023 sbin -> usr/sbin
drwxr-xr-x  11 root root    4096 Jan 13 00:50 snap
drwxr-xr-x   2 root root    4096 May 31  2023 srv
dr-xr-xr-x  11 root root       0 Jan 13 00:30 sys
drwxrwxrwt  11 root root    4096 Jan 13 00:50 tmp
drwxr-xr-x  14 root root    4096 May 31  2023 usr
drwxr-xr-x  13 root root    4096 May 31  2023 var
SHHis@AmberHeart:~# tail -nl
tail: invalid number of lines: ‘l’
SHHis@AmberHeart:~# ls -l / | tail -n1
drwxr-xr-x  13 root root    4096 May 31  2023 var
SHHis@AmberHeart:~# ls -l / | tail -n3 > robot.txt
SHHis@AmberHeart:~# cat robot.txt
drwxrwxrwt  11 root root    4096 Jan 13 00:50 tmp
drwxr-xr-x  14 root root    4096 May 31  2023 usr
drwxr-xr-x  13 root root    4096 May 31  2023 var
SHHis@AmberHeart:~# curl --head --silent google.com
```
然后他死了,大概是google.com需要梯子的问题<br><br>

于是试了试别的网址

```bash
SHHis@AmberHeart:~# curl --head --silent baidu.com
HTTP/1.1 200 OK
Date: Sun, 12 Jan 2025 17:07:04 GMT
Server: Apache
Last-Modified: Tue, 12 Jan 2010 13:48:00 GMT
ETag: "51-47cf7e6ee8400"
Accept-Ranges: bytes
Content-Length: 81
Cache-Control: max-age=86400
Expires: Mon, 13 Jan 2025 17:07:04 GMT
Connection: Keep-Alive
Content-Type: text/html

SHHis@AmberHeart:~# curl --head --silent baidu.com | grep -i content-length
Content-Length: 81
SHHis@AmberHeart:~# curl --head --silent baidu.com | grep -i content-length | cut --delimiter=' ' -f2
81
SHHis@AmberHeart:~# curl --head --silent shinycolors.enza.fun
HTTP/1.1 301 Moved Permanently
Server: CloudFront
Date: Sun, 12 Jan 2025 17:09:31 GMT
Content-Type: text/html
Content-Length: 167
Connection: keep-alive
Location: https://shinycolors.enza.fun/
X-Cache: Redirect from cloudfront
Via: 1.1 b20771afac2acd15ec58304838134668.cloudfront.net (CloudFront)
X-Amz-Cf-Pop: NRT20-P1
X-Amz-Cf-Id: Sp7n_KUHHKK2OoGNN7PAfqQBdrW3h4AU63h1-X8huxG_vX9wbmWDLw==

SHHis@AmberHeart:~# curl --head --silent shinycolors.enza.fun | grep -i content-length | cut --delimiter=' ' -f2
167
SHHis@AmberHeart:~# curl --head --silent granbluefantasy.com
SHHis@AmberHeart:~# curl --head --silent granbluefantasy.jp
HTTP/1.1 301 Moved Permanently
Server: CloudFront
Date: Sun, 12 Jan 2025 17:10:46 GMT
Content-Type: text/html
Content-Length: 167
Connection: keep-alive
Location: https://granbluefantasy.jp/
X-Cache: Redirect from cloudfront
Via: 1.1 ded1ee0f770839d2b2fb7225385749c6.cloudfront.net (CloudFront)
X-Amz-Cf-Pop: TPE50-C1
X-Amz-Cf-Id: aerUs3oVKRI4OInPIJE328GCEyg9NrLn0cal_H5OfiXfTheWf5fcyQ==

SHHis@AmberHeart:~# curl --head --silent granbluefantasy.jp | grep -i content-length | cut --delimiter=' ' -f2
167
```
接下来是内核相关的内容,因为是虚拟机所以没什么多少可尝试的
```bash
SHHis@AmberHeart:~# cd /sys
SHHis@AmberHeart:/sys# ls
block  bus  class  dev  devices  firmware  fs  kernel  module
SHHis@AmberHeart:/sys# ls
block  bus  class  dev  devices  firmware  fs  kernel  module
SHHis@AmberHeart:/sys# cd class/
SHHis@AmberHeart:/sys/class# ls
bdi    cuse     hidraw  ipvtap   misc  pci_bus       ppp  rtc          scsi_generic  tty  vfio
block  devlink  input   macvtap  nd    phy           pps  scsi_device  scsi_host     uio  virtio-ports
bsg    drm      iommu   mem      net   power_supply  ptp  scsi_disk    thermal       vc   vtconsole
SHHis@AmberHeart:/sys/class# cd backlight/
-bash: cd: backlight/: No such file or directory
SHHis@AmberHeart:/sys/class# cd -
/sys
SHHis@AmberHeart:/sys# cd --
```

然后尝试了用xdg-open打开先前的文件

```bash
SHHis@AmberHeart:~# xdg-open SHHis.txt

Command 'xdg-open' not found, but can be installed with:

apt install xdg-utils
```

看起来是没有安装xdg-utils的原因?尝试了安装

```bash
SHHis@AmberHeart:~# apt install xdg-utils
...
...
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-9/gcc-9-base_9.4.0-1ubuntu1~20.04.1_amd64.deb  404  Not Found [IP: 91.189.91.83 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-9/cpp-9_9.4.0-1ubuntu1~20.04.1_amd64.deb  404  Not Found [IP: 91.189.91.83 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

报错了,似乎是没有更新apt-get?尝试了更新

```bash
SHHis@AmberHeart:~# apt-get update
...
...
Reading package lists... Done
```

大概是成功了的样子,再尝试安装了一下xdg-utils,这次成功了

```bash
...
...
Processing triggers for libc-bin (2.31-0ubuntu9.9) ...
/sbin/ldconfig.real: /usr/lib/wsl/lib/libcuda.so.1 is not a symbolic link

```

然后就是回归到用xdg-open打开SHHis.txt了

>SHHis@AmberHeart:~# xdg-open SHHis.txt
打开后出现类似这样的画面
```bash
nichika
nichika
~
~
~
~
~
~
"SHHis.txt" 2L,16C                  1,1     All
```
大概是成功打开记事本了<br><br>

研究了一下发现左下角可以实行命令，右下角是光标所在点<br><br>

发现可以在这里更改记事本内容试着更改了然后百度了如何退出<br><br>

试着输入:q!退出后发现并没有保存修改的内容,大概是因为强制退出<br><br>

以下是作业：<br><br>

```bash
SHHis@AmberHeart:~# ls
283  283pro  CoMETIK.txt  SHHis.txt  man  robot.txt  snap
SHHis@AmberHeart:~# echo $SHELL
/bin/bash
SHHis@AmberHeart:~# cd /tmp
SHHis@AmberHeart:/tmp# mkdir missing
SHHis@AmberHeart:/tmp# man touch
SHHis@AmberHeart:/tmp# touch missing/semester.txt
SHHis@AmberHeart:/tmp# echo "#!/bin/sh" >> missing/semester.txt
-bash: !/bin/sh: event not found
SHHis@AmberHeart:/tmp# echo '#!/bin/sh' >> missing/semester.txt
SHHis@AmberHeart:/tmp# echo 'curl --head --silent https://missing.csail.mit.edu' >> missing/semester.txt
SHHis@AmberHeart:/tmp# cat missing/semester.txt
#!/bin/sh
curl --head --silent https://missing.csail.mit.edu
SHHis@AmberHeart:/tmp# ./missing
-bash: ./missing: Is a directory
SHHis@AmberHeart:/tmp# ./missing/semester
-bash: ./missing/semester: No such file or directory
SHHis@AmberHeart:/tmp# ./missing/semester.txt
-bash: ./missing/semester.txt: Permission denied
SHHis@AmberHeart:/tmp# man chmod
SHHis@AmberHeart:/tmp# man chmod
SHHis@AmberHeart:/tmp# chmod u+x missing/semester.txt
SHHis@AmberHeart:/tmp# ./missing/semester.txt
HTTP/2 200
server: GitHub.com
content-type: text/html; charset=utf-8
last-modified: Sat, 21 Dec 2024 16:53:01 GMT
access-control-allow-origin: *
etag: "6766f26d-205d"
expires: Sun, 12 Jan 2025 18:11:45 GMT
cache-control: max-age=600
x-proxy-cache: MISS
x-github-request-id: 8DBD:17396:383F968:3992BFC:67840386
accept-ranges: bytes
age: 0
date: Sun, 12 Jan 2025 18:01:45 GMT
via: 1.1 varnish
x-served-by: cache-lax-kwhp1940061-LAX
x-cache: MISS
x-cache-hits: 0
x-timer: S1736704906.531356,VS0,VE97
vary: Accept-Encoding
x-fastly-request-id: 19e7286566136e29ca3c507c6b7e7059b6057aa9
content-length: 8285
SHHis@AmberHeart:/tmp# cat missing/semester.txt | grep -i last-modified | cut --delimiter=':' -f2 >> ./last-modified.txt
SHHis@AmberHeart:/tmp# cat last-modified.txt

SHHis@AmberHeart:/tmp# chmod u+x missing/semester.txt
SHHis@AmberHeart:/tmp# cat missing/semester.txt | grep -i last-modified | cut --delimiter=":" -f2 >> ./last-modified.txt
SHHis@AmberHeart:/tmp# cat last-modified.txt

SHHis@AmberHeart:/tmp# cat .missing/semester.txt | grep -i last-modified | cut --delimiter=':' -f2 >> ./last-modified.txt
cat: .missing/semester.txt: No such file or directory
SHHis@AmberHeart:/tmp# cat ./missing/semester.txt | grep -i last-modified | cut --delimiter=":" -f2 >> ./last-modified.txt
SHHis@AmberHeart:/tmp# cat last-modified.txt

(一直输出空白不知道是什么问题,试着找了找权限和别的问题)
SHHis@AmberHeart:/tmp# ls -l
total 24
-rw-r--r-- 1 root root    2 Jan 13 02:16 last-modified.txt
drwxr-xr-x 2 root root 4096 Jan 13 01:50 missing
-rw-r--r-- 1 root root    0 Jan 13 01:46 semester
-rw-r--r-- 1 root root    0 Jan 13 01:48 semester.txt
drwx------ 4 root root 4096 Jan 13 00:50 snap-private-tmp
drwx------ 3 root root 4096 Jan 13 00:32 systemd-private-1082091ed04b42e6adc2d449ff635cf9-ModemManager.service-q97nSi
drwx------ 3 root root 4096 Jan 13 00:32 systemd-private-1082091ed04b42e6adc2d449ff635cf9-systemd-logind.service-KUc6Vi
drwx------ 3 root root 4096 Jan 13 00:32 systemd-private-1082091ed04b42e6adc2d449ff635cf9-systemd-resolved.service-EO3Tai
SHHis@AmberHeart:/tmp# ls -l ./missing/semester.txt
-rwxr--r-- 1 root root 61 Jan 13 01:54 ./missing/semester.txt
SHHis@AmberHeart:/tmp# file ./missing/semester.txt
./missing/semester.txt: POSIX shell script, ASCII text executable
(还是失败,放弃了)
SHHis@AmberHeart:/tmp# echo ' Sat,21 Dec 2024 16:53:01 GMT' > last-modified.txt
SHHis@AmberHeart:/tmp# cat last-modified.txt
 Sat,21 Dec 2024 16:53:01 GMT
SHHis@AmberHeart:/tmp# echo '今天就学习到这，下次再见捏'
今天就学习到这，下次再见捏。
```

### 01.13
#### 今日学习时长:45分钟
#### 学习总结：相关变量参数、格式以及试了试vim

Bash字符串中''不被转义，“”会被转义字符所替换 例如$<br><br>

执行过程中的空格有其致命性,使用时需注意<br><br>

```bash
foo=bar
#可以正常执行
foo = bar
#直接报错
```
接下来是一些可以用于脚本执行中的参数<br><br>
```bash
$0脚本名 $1-$9对应的第几个参数

$#参数数量 $@所有参数 $?参数正确性返回值

!!上一个参数 类似于方向键↑大概 可以用sudo !!来获得权限执行上一个命令

$_ 可以用于提取脚本中最后一个参数 $$脚本的执行进程识别码
```

此外命令可以配合||和&&使用 相当于or和and<br><br>

true返回码固定为0 false为1<br><br>

感觉在实操过程中熟悉一下就ok了<br><br>

```bash
SHHis@AmberHeart:~# false || echo "BangDream!"
BangDream!
SHHis@AmberHeart:~# true && echo '!! means BangDream!'
!! means BangDream!
```
此外尝试试着用vim看看够不够熟练
```bash
SHHis@AmberHeart:~# vim BangDream.sh
BangDream(){
        mkdir -p "$1"
        cd "$1"
        false || echo "$1" >> BangDream.txt
        true && echo "$1 is a part of BangDream" >> BangDream.txt
}
SHHis@AmberHeart:~# BangDream mikoto
BangDream: command not found
SHHis@AmberHeart:~# source BangDream.sh
SHHis@AmberHeart:~# BangDream mikoto
SHHis@AmberHeart:~/mikoto# cat BangDream.txt
mikoto
mikoto is a part of BangDream
```
稍微研究了一下,看起来是成功了<br><br>

今天事情有点多比较赶,就学到这吧
```bash
SHHis@AmberHeart:~/mikoto# echo "$(true&&cat BangDream.txt | grep -i mikoto | cut -d' ' -f1)向各位说下次见"
mikoto
mikoto向各位说下次见
```

<!-- Content_END -->