# CFC Studio 共学 Epoch1 指引

---

# [Drive_FLY]

> Great success starts with a ordinary beginnings.

## Note

<!-- Content_START -->

### 01.06

在阅读 PA 手册的时候，被 PA0 中关于使用英语的说明深深吸引住了，这里给它简单摘过来：

> 随着科学技术的发展, 在国际学术交流中使用英语已经成为常态: 顶尖的论文无一不使用英文来书写, 在国际上公认的计算机领域经典书籍也是使用英文编著. 顶尖的论文没有中文翻译版; 如果需要获取信息, 也应该主动去阅读英文材料, 而不是等翻译版出版. "我是中国人, 我只看中文"这类观点已经不符合时代发展的潮流, 要站在时代的最前沿, 阅读英文材料的能力是不可或缺的.
>
> 阅读英文材料, 无非就是"不会的单词查字典, 不懂的句子反复读". 如今网上有各种词霸可解燃眉之急, 但英文阅读能力的提高贵在坚持. "刚开始觉得阅读英文效率低", 是所有中国人都无法避免的经历. 如果你发现身边的大神可以很轻松地阅读英文材料, 那是因为他们早就克服了这些困难. 引用陈道蓄老师的话: 坚持一年, 你就会发现有不同; 坚持两年, 你就会发现大有不同.

讲义里的话简直戳中了我的心窝，自我接触编程以来，时常会因为官网/手册是英文的进而放弃阅读，继续去简中互联网掏屎。事实上如果耐心读下来，往往会发现文档中其实早就将许多问题都说明清楚了，我也不断在尝试切换到英语的阅读环境，但也多次因各种原因无法继续进行。

CoLearning 是曾老师的一次大胆创新与尝试，我也想借着这个机会去做一些新的东西。一步登天不可取，短期掌握听说读写是不符合客观规律的。恰好，本次共学计划的课程文档也不是那么长，也没有太多难以理解的专有名词。那就让我们从基础的阅读开始，尝试认真阅读纯英语的文档，想必应该会有一些收获。

正如我在招新群中所说的那样：种一棵树的最好时间是十年前，其次是现在。永远不要担心准备不够充分，现在就是开始的最好时机。

由于今、明两天还在考试，又不想缺勤，就先以这样的形式占个坑尾吧，复习去喽。

### 01.07

`Bash` => `Bourne-Again SHell`。这个名字还是很有意思的，谍影重重 SHell，按 Wiki 的说法，既指它的前身`Bourne SHell`，也是重生的意思。

我一般都用 XSHell 进行 SSH 连接，所以很少手打 SSH 命令，这就导致有些概念搞不明白。比如`cfc@cfc`，前者是用户名，后者是主机名。这里还提到`$`代表当前非 root 权限，有一说一我还真没注意过，~~我一贯直接上 root~~。

环境变量这个和 Windows 基本就是一模一样。

查看命令的具体路径：which echo

```bash
echo $PATH
/bin/echo $PATH
# Windows
echo $env:PATH
```

还有这个目录分隔符，也是经常混淆。`/`是斜杠，`\`是反斜杠。UNIX 上使用斜杠而 Windows 使用反斜杠，咱就是处处都不同。那绝对路径相对路径是如何区分的呢？`/`开头的才叫绝对路径。

```bash
# 全路径
pwd
# 当前目录
.
./home
# 上级目录
..
../home
```

命令参数这个有个概念，`-`后面跟的是缩写，如 h，而`--`跟的则是全拼，如 help。大多数场景都是这样的。

还有些有意思的东西，不过今天可能来不及写了，考完试晚上有个聚餐，还是占个坑位吧，晚上再看看来不来得及。

### 01.08

真的是计划赶不上变化，每天都有各种各样杂乱的事情，除了上午花了点时间来写了一点，继续明天再说吧。

更多的时间其实是在看英语。慢慢看下来发现其实说到底就一个词，熟能生巧。词看多了就知道意思了，句看多了就懂了，配合划词翻译，慢慢看呗，有什么难的，兄弟们干！

Bash 中使用空格分割参数，因此一些为了美观手敲空格的习惯在这里要取消掉了。毕竟在大部分语言中空格是没啥作用的（Python 当我没说），更多的是格式上的美观。
单双引号的作用在 Bash 中也有区别，双引号将被解析，而单引号则是原始字符串。

`source`可以用来加载一个`bash`脚本，如果你在脚本中定义了一个函数，`source`以后就可以直接运行它了。除了使用`source`，直接使用`.`也是可以的。

### 01.09

终于是回来了，虽然还是很多杂七杂八的事儿，但总算有空下来的时间了。

`&&`和`||`是`短路运算符`，他的逻辑比较清奇，和编程语言中的与或不太一样。使用`&&`时，当左侧执行成功（0 返回值），才执行右侧。使用`||`时，当左侧执行失败时（非 0 返回值），才执行右侧。

上面的理解其实是错误的，这里的短路运算符和编程语言中的是一致的。使用`&&`时，当左侧为`false`时直接返回`false`。使用`||`时，当左侧为`true`时直接返回`true`。这是一种计算优化。只是我没用短路表达式来实现过条件执行，导致产生了这种错误的想法。

> 如果某个操作看起来像是有更方便的实现方法，一般情况下真的会有

这句话实在是太真实了。对我个人来说，当我使用某个软件、工具时，若有人问：这个工具能不能实现 XX？我想了想可能会说：肯定能啊。往往经过一番寻找还真能实现。那我凭什么来判断？这时候我的思路就是：因为如果我是设计者，我应当会设计这个功能。

`journalctl`可以用来查看`systemd`的日志，我之前用的最多的就是拿来查 Nginx 的日志。

我们知道在 UNIX 中管道符的概念，可以将数据在命令之间传递。一般来说，Nginx 也会在`/var/log/nginx`下面输出一份日志，但是每一份都很大，打开以后从上翻到下很麻烦，怎么办呢？可以用`cat`配合`grep`来做一些过滤。

```bash
journalctl | grep sshd | grep 'authentication failure'
```

但是这还是太多了啊，对于一个成熟的服务器来说，暴露在公网上一天被刷个几千次一点问题都没有。还是不好翻，怎么办？我们可以用分页器。继续管道一个`less`就好了。

```bash
journalctl | grep sshd | grep 'authentication failure' | less
```

还可以把输出的内容保存到文件，轻轻松松。

```bash
journalctl | grep sshd | grep 'authentication failure' > ssh.log
```

继续用分页器看。

```bash
less ssh.log
```

除此之外，如果想要针对特定字符串如：UA、IP 并查看找到的内容前后的日志，可以用`grep`的参数来实现。

```bash
# 查找warning字符，并显示warning所在行的之后5行
cat log.txt | grep 'warning' -A 5
# 之前5行
cat log.txt | grep 'warning' -B 5
# 前后5行
cat log.txt | grep 'warning' -C 5
# 排除warning所在的行的信息
cat log.txt | grep -v 'warning'
```

内容不多，但胜在还在继续。

### 01.10

在简单搜索出需要的内容后，我们还可以用正则表达式来提取需要的内容并格式化输出。

在写正则的时候遇到了一些困难，当然这也见怪不怪了，谁都知道正则不是人写的。

`sed`默认支持的是 BRE(Basic Regular Expression) 基本正则表达式，和 ERE(Extended Regular Expression) 相比只在一些符号上有区别。如果想用 ERE，记得加上扩展选项`-E`。

> https://www.gnu.org/software/sed/manual/html_node/BRE-vs-ERE.html#BRE-vs-ERE
>
> In GNU `sed`, the only difference between basic and extended regular expressions is in the behavior of a few special characters: ‘?’, ‘+’, parentheses, braces (‘{}’), and ‘|’.
>
> With basic (BRE) syntax, these characters do not have special meaning unless prefixed with a backslash (‘\’); While with extended (ERE) syntax it is reversed: these characters are special unless they are prefixed with backslash (‘\’).

在一般的编程语言中应该会使用 PCRE(Perl Compatible Regular Expressions)，比 BRE 要扩展得多，是支持这些元字符的。

这里我们想提取所有登录失败日志的用户名、IP 和端口。具体的表达式就不解释了，可以问 GPT。

如果需要测试正则的话，可以用这个：https://regex101.com/

```bash
journalctl | grep 'Failed password' | sed -E 's/.*Failed password for (invalid user (.*)|(root)) from (.*) port ([0-9]+) ssh2/Username:\2\3 IP:\4:\5/'
```

> Jan 10 11:45:57 CubeCloud-2021818444 sshd[430179]: Failed password for root from 92.255.85.107 port 49690 ssh2
> Jan 10 11:46:01 CubeCloud-2021818444 sshd[430182]: Failed password for invalid user admin from 92.255.85.107 port 60556 ssh2
> Jan 10 11:46:55 CubeCloud-2021818444 sshd[430192]: Failed password for invalid user monitoring from 2.57.122.193 port 55322 ssh2
> Jan 10 11:47:34 CubeCloud-2021818444 sshd[430195]: Failed password for invalid user shakeel from 2.57.122.26 port 59606 ssh2

> Username:root IP:92.255.85.107:49690
> Username:admin IP:92.255.85.107:60556
> Username:monitoring IP:2.57.122.193:55322
> Username:shakeel IP:2.57.122.26:59606

看似问题解决了，但别忘了默认用户除了`root`还有其他的，我们要想一个一劳永逸的办法。前面的`invalid user`才是真正的可选部分是不？那好嘛，我们照着这个改。

```bash
journalctl | grep 'Failed password' | sed -E 's/.*Failed password for ((invalid user )?(.*)) from (.*) port ([0-9]+) ssh2/Username:\3 IP:\4:\5/'
```

搞定！还避免了上一组正则需要同时引用组 2 和组 3 的麻烦。

这么一玩，会发现通过使用管道配合各种工具，数据整理变得简单多了。在过去我都是将日志文件拉到本地再针对性做处理，先来看来似乎有更好的方式。甚至可以基于此编写`bash`脚本做出属于自己业务场景的小工具，妙哉。

### 01.11

忙忙碌碌的赶路人，终于到家了。

提取出用户名还不够，我们想看看哪些用户名是被光顾的常客。这里可以用管道和一些命令组合来实现原来只能用 Excel 实现的功能。

```bash
journalctl
 | grep 'Failed password'
 | sed -E 's/.*Failed password for ((invalid user )?(.*)) from (.*) port ([0-9]+) ssh2/\3/'
 | sort # 将用户名排序 以便使用uniq
 | uniq -c # 按顺序折叠重复的文本并统计
 | sort -nk1 # 对第一列（统计值）进行数字排序（默认空格分割）
```

排序后还可以使用 `head` 或 tail` 提取一部分内容，如：`head -n10` 提取前 10 行。

紧接着使用 `awk` 提取第二列的内容，并使用 `paste` 将他们按逗号分割的形式输出，完整的命令如下：

```bash
journalctl
| grep 'Failed password'
| sed -E 's/.*Failed password for ((invalid user )?(.*)) from (.*) port ([0-9]+) ssh2/\3/'
| sort
| uniq -c
| sort -nrk1
| head -n10
| awk '{print $2}'
| paste -sd,
```

输出结果是：`root,admin,user,anuj,ubuntu,shaista,test,lenovo,bmp,user1`

这比用 Excel 方便多了！

### 01.12

今天是划水的一天，工作量较小，又想刷个全勤，把之前的 SSH 端口转发的内容拿出来吧。

本地转发：在本地监听端口，通过本机与 SSH 登录机隧道将访问本机指定端口的流量转发到目标机（或目标机可访问的）主机与端口

- 目的：本机可通过 SSH 隧道访问目标机网络受限的资源

- 扩展：本地监听的端口可供本地访问或本地网络环境内的设备访问，目标机同理

- 格式：`-L [本机:]本机端口:目标机:目标机端口 中转机`

- SSH 登录机（中转机）需要能够访问目标机，中转机与目标机可以是同一台

- 通过上述操作，可以做到在只开通 22 端口的前提下访问数据库等端口

- 常用操作：通过中转机使用更好用的本地数据库客户端访问受限网络环境的 MySQL 服务端

- 常用操作：通过中转机连接受限网络环境中的某个远程服务端口

- 举例：在本机监听 50000 端口，访问目标机 3306 端口，通过中转机（这里同目标机）

  ```Bash
  ssh -L [0.0.0.0:]50000:localhost:3306 root@202.202.202.202

  # 当MySQL限制root用户远程登录时 目标机地址应当为localhost 否则与MySQL配置不符
  # 即使202.202.202.202在目标机看来就是localhost 那也是两码事
  ```

远程转发：在 SSH 登录机（远端）监听端口，通过远端与本机的 SSH 隧道将访问远端指定主机与端口的流量转发到本机（或本机可访问的）端口

- 目的：远端可通过 SSH 隧道访问本机网络受限的资源

- 扩展：远端监听的端口可供目标机或目标机网络环境中的设备访问，本机同理

- 格式：`-R [远端机:]远端机端口:本机:本机端口 中转机`

- SSH 登录机需要能够访问最终需要访问的远端机，登录机与远端机可以是同一台

- 通过上述操作，可以做到在只开通 22 端口的前提下让远端服务器访问本机 HTTP 代理端口，实现盾构机

- 常用操作：将位于内网的本机服务通过一台公网机器暴露

- 常用操作：将本地盾构机监听端口代理到远端，供临时遁地

- 常用操作：在内网保护环境中，通过堡垒机向外部机器主动发起转发（外部机器网络受限不可向堡垒机发起连接），外部机器可通过该隧道访问内网其他设备

- 举例：在远端机监听 50000 端口，访问本机 10809 端口，通过中转机（同远端机）

  ```Bash
  ssh -R [0.0.0.0:]50000:localhost:10809 root@202.202.202.202
  ```

- 动态转发：在本机监听端口，通过本机与 SSH 登录机隧道将访问本机监听的流量通过 SSH 登录机转发，无需固定目标机主机与端口
  - 协议：Socks
  - 格式：`-D [本机:]本机端口 中转机`
  - 常用操作：通过该监听端口访问 SSH 登录机网络内的任意资源
- 实现 SSH Tunnel 盾构机
  - 需要注意的是，SSH 隧道默认会通过 IPv6 创建，而 IPv6 的监听地址`[::1]`不包含在 V2RayN 中的`本机`部分，需要开启`允许来自局域网的连接`或强制 SSH 连接建立时使用 IPv4。

<!-- Content_END -->
