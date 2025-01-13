# CFC Studio 共学 Epoch1 指引

---

# [DemoJustLuGuo]

## 笔记证明

<!-- Content_START --> 

### 01.06

#### 学习时长：50 分钟

跟着视频在进行基本命令行的学习 (使用 powershell)

在运行 ls -l 命令时 powershell 突然报错：

> Get-ChildItem: Missing an argument for parameter 'LiteralPath'. Specify a parameter of type 'System.String[]' and try again.

百度后发现错误是因为 Powershell 使用-LiteralPath，因为该选项与-l 匹配，但它需要一个参数。（这里应该是 windows 与 linux 命令使用的差异导致的）
查阅命令帮助后发现 powershell 可直接使用 ls 或 dir、gci 等命令列出文件目录

> 或者使用 ls -Path 'C:\Users\YourUsername\Documents'

在此之前使用查看环境变量 echo $PATH命令也遇到了同样的问题，不过在经过弹幕提醒后知道了windows的powershell使用的是$env:path 命令

总结：最近的时间比较紧，今天就先看到这里，使用 powershell 的原因是我忽视了 windows 与 linux 之间的区别，在学习之时被这些奇妙错误搞麻了，目前已老实安装 bash，等考试完后会补上接下来的课程的。

### 01.08

#### 学习时长：50 分钟

安装了 wsl 之后学习完了第一节的内容

基本都是跟着视频在打，蛮不错的，除了 wsl 是虚拟机导致一些内核的改不了之外，其他的没有遇到什么问题。做了课后作业，就先传上来吧，还有一科没考完呢。

```bash
 sakuraauro@DemoJustLuGuo:/tmp/$ cd /tmp
 sakuraauro@DemoJustLuGuo:/tmp/$ mkdir missing
 sakuraauro@DemoJustLuGuo:/tmp$ ls
missing
snap-private-tmp
systemd-private-856d00b5580a4e4ab51e9660bc84158c-polkit.service-7eTcE0
systemd-private-856d00b5580a4e4ab51e9660bc84158c-systemd-logind.service-kBkmIl
systemd-private-856d00b5580a4e4ab51e9660bc84158c-systemd-resolved.service-uWN9Q6
systemd-private-856d00b5580a4e4ab51e9660bc84158c-systemd-timesyncd.service-kXJsTp
systemd-private-856d00b5580a4e4ab51e9660bc84158c-wsl-pro.service-jXoXvM
  sakuraauro@DemoJustLuGuo:/tmp$ cd missing
  sakuraauro@DemoJustLuGuo:/tmp/missing$ touch semester
  sakuraauro@DemoJustLuGuo:/tmp/missing$ ls
semester
  sakuraauro@DemoJustLuGuo:/tmp/missing$ echo '#!/bin/sh' > semester
  sakuraauro@DemoJustLuGuo:/tmp/missing$ echo 'curl --head --silent https://missing.csail.mit.edu' >> sem
ester
  sakuraauro@DemoJustLuGuo:/tmp/missing$ cat semester
#!/bin/sh
curl --head --silent https://missing.csail.mit.edu.com
  sakuraauro@DemoJustLuGuo:/tmp/missing$ /tmp/missing/semester
-bash: /tmp/missing/semester: Permission denied
  sakuraauro@DemoJustLuGuo:/tmp/missing$ sudo /tmp/missing/semester
sudo: /tmp/missing/semester: command not found
  sakuraauro@DemoJustLuGuo:/tmp/missing$ man chmod
  sakuraauro@DemoJustLuGuo:/tmp/missing$ ls -l
total 8
drwxr-xr-x 2 sakuraauro sakuraauro 4096 Jan 8 22:18 missing
-rw-r--r-- 1 sakuraauro sakuraauro 65 Jan 8 22:33 semester
  sakuraauro@DemoJustLuGuo:/tmp/missing$ chmod 777 semester
  sakuraauro@DemoJustLuGuo:/tmp/missing$ ls -l
total 8
drwxr-xr-x 2 sakuraauro sakuraauro 4096 Jan 8 22:18 missing
-rwxrwxrwx 1 sakuraauro sakuraauro 65 Jan 8 22:33 semester
  sakuraauro@DemoJustLuGuo:/tmp/missing$ ./semester
  sakuraauro@DemoJustLuGuo:/tmp/missing$ sudo ./semester(没输出？ 好像还是执行不出来)
  sakuraauro@DemoJustLuGuo:/tmp/missing$ ls -l
total 8
drwxr-xr-x 2 sakuraauro sakuraauro 4096 Jan 8 22:18 missing
-rwxrwxrwx 1 sakuraauro sakuraauro 65 Jan 8 22:33 semester
  sakuraauro@DemoJustLuGuo:/tmp/missing$ cd
  sakuraauro@DemoJustLuGuo:~$ echo '-rwxrwxrwx 1 sakuraauro sakuraauro 65 Jan 8 22:33 semester' > last-modified.txt
  sakuraauro@DemoJustLuGuo:~$ ls -l
total 8
 drwxr-xr-x 2 sakuraauro sakuraauro 4096 Jan 8 21:10 TEST
-rw-r--r-- 1 sakuraauro sakuraauro 62 Jan 8 22:41 last-modified.txt
  sakuraauro@DemoJustLuGuo:~$ cd /sys/class/power_supply/BAT1
  sakuraauro@DemoJustLuGuo:/sys/class/power_supply/BAT1$ cat capacity
94
```
### 01.10

#### 学习时长：1小时

Bash 中的字符串通过 ' 和 " 分隔符来定义，但是它们的含义并不相同。以 ' 定义的字符串为原义字符串，其中的变量不会被转义，而 " 定义的字符串会将变量值进行替换。

>  foo=bar
>
>  echo "$foo"
> 
>  打印 bar
> 
>  echo '$foo'
> 
>  打印 $foo

自己实操的时候没有正确理解这段话
在执行 `echo "mkdir -p "$1""` 时一直奇怪为什么输出只有 `mkdir -p`
实际上正确的写法应该是`echo 'mkdir -p "$1"'`(~~日常铸币~~)

___

这章还讲到了 &&（与操作符） 和 ||（或操作符）  两种运算符，我具体的实操是这样的

```bash
sakuraauro@DemoJustLuGuo:~/TEST$ true || echo 123
sakuraauro@DemoJustLuGuo:~/TEST$ echo $?
0                        ##true返回0，即执行前一个命令成功
sakuraauro@DemoJustLuGuo:~/TEST$ false || echo 123
123                      ##false返回1，即执行前一个命令失败，将执行后一个命令
sakuraauro@DemoJustLuGuo:~/TEST$ true && echo 123
123                      ##true返回0即执行成功，将执行后一个命令
sakuraauro@DemoJustLuGuo:~/TEST$ false && echo 123
sakuraauro@DemoJustLuGuo:~/TEST$ echo $?
1                        ##false返回1即执行失败，不会执行后一个命令
```

___

还讲到了三种通配符，个人实操了一遍感觉确实有助于提升效率。这里就先把它列出来

>1.当你想要利用通配符进行匹配时，你可以分别使用 ? 和 * 来匹配一个或任意个字符。例如，对于文件 foo, foo1, foo2, foo10 和 bar, rm foo? 这条命令会删除 foo1 和 foo2 ，而 rm foo* 则会删除除了 bar 之外的所有文件。
>
>2.花括号 {} - 当你有一系列的指令，其中包含一段公共子串时，可以用花括号来自动展开这些命令。这在批量移动或转换文件时非常方便。

下面是我的示例

```bash
sakuraauro@DemoJustLuGuo:~/TEST$ touch test{1..9}.txt ##创建名为test1到test9的txt文件
sakuraauro@DemoJustLuGuo:~/TEST$ ls
change.sh    hi.txt     test2.txt  test5.txt  test8.txt
document.sh  more       test3.txt  test6.txt  test9.txt
hello.txt    test1.txt  test4.txt  test7.txt
sakuraauro@DemoJustLuGuo:~/TEST$ rm test?.txt  ##删除所有带test(x).txt的文件（好像只在10以内有效？）
sakuraauro@DemoJustLuGuo:~/TEST$ ls
change.sh  document.sh  hello.txt  hi.txt  more
```

以下是另一个示例
```bash
sakuraauro@DemoJustLuGuo:~/TEST$ touch test{1..11}.txt  ##创建名为test1到test11的txt文件
sakuraauro@DemoJustLuGuo:~/TEST$ ls
change.sh    hi.txt     test10.txt  test3.txt  test6.txt  test9.txt
document.sh  more       test11.txt  test4.txt  test7.txt
hello.txt    test1.txt  test2.txt   test5.txt  test8.txt
sakuraauro@DemoJustLuGuo:~/TEST$ rm test?.txt  ##删除所有带test(x).txt的文件
sakuraauro@DemoJustLuGuo:~/TEST$ ls
change.sh    hello.txt  more        test11.txt
document.sh  hi.txt     test10.txt  ##这里test10.txt和test11.txt并没有被删除
sakuraauro@DemoJustLuGuo:~/TEST$ rm test??.txt
sakuraauro@DemoJustLuGuo:~/TEST$ ls
change.sh  document.sh  hello.txt  hi.txt  more  ##把?换成??就可以删除掉了
```
另外，使用`rm test*.txt`命令应该会更方便，不过看使用场景吧。

### 01.12

#### 学习时长：1小时

先补上上一节的作业
```bash

#!/bin/bash

 export new_workspace=""

 marco(){
         new_workspace=$(pwd)
 }

 polo(){
         cd "$new_workspace"
 }
 
 下面是终端输出
 
 sakuraauro@DemoJustLuGuo:~/afterwork$ marco marco.sh
sakuraauro@DemoJustLuGuo:~/afterwork$ cd
sakuraauro@DemoJustLuGuo:~$ polo
sakuraauro@DemoJustLuGuo:~/afterwork$
```

```bash
#!/usr/bin/env bash  

 standard_out="standard_out.txt"
 standard_error="standard_error.txt"
 success_count=0
 while true;do
          n=$(( RANDOM % 100 ))

 if [[ n -eq 42 ]]; then
    echo "Something went wrong" >> "$standard_out"
    >&2 echo "The error was using magic numbers" >> "$standard_error"
    exit 1
 fi

 echo "Everything went according to plan" >> "$standard_out"
 if [ $? -ne 0 ]; then  
        echo "脚本在失败前共运行了 $success_count 次"
        break
   fi
    ((success_count++))
done

cat "$standard_out"
cat "$standard_error"
```

学习了vim编辑器的使用
基本上 vim 共分为这几种模式：
1.正常模式：在文件中四处移动光标进行修改
2.插入模式：插入文本
3.替换模式：替换文本
4.可视化模式（一般，行，块）：选中文本块
5.命令模式：用于执行命令

下面是一些从讲义上摘抄下来的内容，上手这个还是需要点时间的，抄下来方便自己查看

>你可以按下 <ESC>（退出键）从任何其他模式返回正常模式。在正常模式，键入 i 进入插入 模式，R 进入替换模式，v 进入可视（一般）模式，V 进入可视（行）模式，<C-v> （Ctrl-V, 有时也写作 ^V）进入可视（块）模式，: 进入命令模式。

___

>在正常模式下键入 : 进入命令行模式。 在键入 : 后，你的光标会立即跳到屏幕下方的命令行。 这个模式有很多功能，包括打开，保存，关闭文件，以及 退出 Vim。
>
>:q 退出（关闭窗口）
>
>:w 保存（写）
>
>:wq 保存然后退出
>
>:e {文件名} 打开要编辑的文件
>
>:ls 显示打开的缓存
>
>:help {标题} 打开帮助文档
>
>:help :w 打开 :w 命令的帮助文档
>
>:help w 打开 w 移动的帮助文档

___

>基本移动: hjkl （左， 下， 上， 右）     **卧槽这个左下上右太抽象了，哪怕左上下右也行啊**
>
>词： w （下一个词）， b （词初）， e （词尾）
>
>行： 0 （行初）， ^ （第一个非空格字符）， $ （行尾）
>
>屏幕： H （屏幕首行）， M （屏幕中间）， L （屏幕底部）
>
>翻页： Ctrl-u （上翻）， Ctrl-d （下翻）
>
>文件： gg （文件头）， G （文件尾）
>
>行数： :{行数}<CR> 或者 {行数}G ({行数}为行数)
>
>杂项： % （找到配对，比如括号或者 /* */ 之类的注释对）
>
>查找： f{字符}， t{字符}， F{字符}， T{字符}
>
>查找/到 向前/向后 在本行的{字符}
>
>, / ; 用于导航匹配
>
>搜索: /{正则表达式}, n / N 用于导航匹配

___

>i 进入插入模式
>
>但是对于操纵/编辑文本，不单想用退格键完成
>
>O / o 在之上/之下插入行
>
>d{移动命令} 删除 {移动命令}
>
>例如，dw 删除词, d$ 删除到行尾, d0 删除到行头。
>
>c{移动命令} 改变 {移动命令}
>
>例如，cw 改变词
>
>比如 d{移动命令} 再 i
>
>x 删除字符（等同于 dl）
>
>s 替换字符（等同于 xi）
>
>可视化模式 + 操作
>
>选中文字, d 删除 或者 c 改变
>
>u 撤销, <C-r> 重做
>
>y 复制 / “yank” （其他一些命令比如 d 也会复制）
>
>p 粘贴
>
>更多值得学习的: 比如 ~ 改变字符的大小写

___

### 01.13

#### 学习时长：1小时

本节课讲的内容是使用ssh获取远程服务器的日志文件，通过搜索、过滤来找到并整理需要的数据
说实话这一节讲的内容有点密了，这里就先整理出自己认为有用的

sed编辑器

主要是运用s（替换命令）。s 命令的语法如下：s/REGEX/SUBSTITUTION/, 其中 REGEX 部分是我们需要使用的正则表达式，而 SUBSTITUTION 是用于替换匹配结果的文本。

正则表达式

>. 除换行符之外的 “任意单个字符”
>
>* 匹配前面字符零次或多次
>
>+ 匹配前面字符一次或多次
>
>[abc] 匹配 a, b 和 c 中的任意一个
>
>(RX1|RX2) 任何能够匹配 RX1 或 RX2 的结果
>
>^ 行首
>
>$ 行尾

sed 的正则表达式有些时候是比较奇怪的，它需要你在这些模式前添加 \ 才能使其具有特殊含义。或者，您也可以添加 -E 选项来支持这些匹配。~~（你怎么知道我刚刚实操就被坑了）~~

感觉就这些需要重点记一下（其实是后面用方便直接打开看，就不用一个个点网页看语法使用示例了），其他的看了但是总感觉云里雾里的，说实话还是更喜欢把自己的实操记录的输出复制上来，可以更直观的看到我写了什么，为什么这么写。

~~（还有感觉这正则表达式不像是人发明出来的）~~

<!-- Content_END -->