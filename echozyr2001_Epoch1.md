# CFC Studio 共学 Epoch1 指引
---
# [echozyr2001]

## 笔记证明

<!-- Content_START --> 
### 01.06

> 学习时间：70 min

---

**主流 shell：** Bash、Zsh、Fish

**主流终端模拟器：** iTerm2、Alacritty、Hyper、Kitty、Terminus、Ghostty

---

“shell 是一个编程环境，所以它具备变量、条件、循环和函数”（之前没有从这个角度理解过）

如此理解的话，我们可以对比 lua、python 等脚本语言的执行环境。

---

```bash
-rw-r--r--
```

rwx 每三个字符构成一组。分别代表了文件所有者，用户组以及其他所有人具有的权限。

最前面的字符用来表示文件属性，`d` 表示目录，`l` 表示链接文件，`-` 表示普通文件。这三个字符可以分别对应一个二进制位，每一组的权限就可以用 `0～7` 来表示。

曾经遇到过一个问题，对于 `.pem` 这样的私钥文件，你必须将其权限设置为 `600` 才能使用（即 `-rw-------`），不然会遇到文件权限过大无法执行的问题。

---

**单引号与双引号在bash中的区别？**

> reference:
> 
> https://www.gnu.org/software/bash/manual/html_node/Quoting.html

**shell 是如何知晓这个文件需要使用 sh 来解析呢？**

> reference:
> 
> https://en.wikipedia.org/wiki/Shebang_(Unix)
>
> 在类 Unix 系统中像使用可执行文件那样使用一个文本文件时，程序加载器机制会将文件初始行进行解析，其中 `#!` 这部分被称为 `shebang`，除此之外的其他部分将被解析为指令。
>
> 例如，如果脚本以路径 `path/to/script` 命名，并且以 `#!/bin/sh` 开头，则指示程序加载器运行程序 `/bin/sh` ，传递 `path/to/script` 作为第一个参数。

---

**shell 的配置**

1. 安装 zsh

2. 安装插件管理器
  * 轻量化 zinit： https://github.com/zdharma-continuum/zinit
  * 重量级oh-my-zsh：https://ohmyz.sh/

3. 主题配置使用 starship：https://starship.rs/zh-CN/

---

文章中提到在 `echo` 这样的命令遇到空格时，需要使用 `"` 或转义字符，但是我发现在我的终端中，可以正常使用。

```zsh
➜  The-Missing-Semester git:(main) ✗ echo $SHELL       
/bin/zsh
➜  The-Missing-Semester git:(main) ✗ echo hello world           
hello world
```

起初我以为这是 `zsh` 的特殊功能，但是我发现在 ubuntu 上也是同样的结果

```bash
ubuntu@instance-20241225-1836:~$ echo $SHELL
/bin/bash
ubuntu@instance-20241225-1836:~$ echo hello world
hello world
```

在使用 `$ touch hello world` 时创建了 `hello` 和 `world` 两个文件，初步认为是 `echo` 命令的特殊。

---

讲环境变量部分，让我想到了 python 的虚拟环境

```bash
# This file must be used with "source bin/activate" *from bash*
# You cannot run it directly

deactivate () {
    # reset old environment variables
    if [ -n "${_OLD_VIRTUAL_PATH:-}" ] ; then
        PATH="${_OLD_VIRTUAL_PATH:-}"
        export PATH
        unset _OLD_VIRTUAL_PATH
    fi
    if [ -n "${_OLD_VIRTUAL_PYTHONHOME:-}" ] ; then
        PYTHONHOME="${_OLD_VIRTUAL_PYTHONHOME:-}"
        export PYTHONHOME
        unset _OLD_VIRTUAL_PYTHONHOME
    fi

    # Call hash to forget past commands. Without forgetting
    # past commands the $PATH changes we made may not be respected
    hash -r 2> /dev/null

    if [ -n "${_OLD_VIRTUAL_PS1:-}" ] ; then
        PS1="${_OLD_VIRTUAL_PS1:-}"
        export PS1
        unset _OLD_VIRTUAL_PS1
    fi

    unset VIRTUAL_ENV
    unset VIRTUAL_ENV_PROMPT
    if [ ! "${1:-}" = "nondestructive" ] ; then
    # Self destruct!
        unset -f deactivate
    fi
}

# unset irrelevant variables
deactivate nondestructive

# on Windows, a path can contain colons and backslashes and has to be converted:
case "$(uname)" in
    CYGWIN*|MSYS*)
        # transform D:\path\to\venv to /d/path/to/venv on MSYS
        # and to /cygdrive/d/path/to/venv on Cygwin
        VIRTUAL_ENV=$(cygpath "/Users/echo/CodeFile/Python/venv")
        export VIRTUAL_ENV
        ;;
    *)
        # use the path as-is
        export VIRTUAL_ENV="/Users/echo/CodeFile/Python/venv"
        ;;
esac

_OLD_VIRTUAL_PATH="$PATH"
PATH="$VIRTUAL_ENV/bin:$PATH"
export PATH

VIRTUAL_ENV_PROMPT="venv"
export VIRTUAL_ENV_PROMPT

# unset PYTHONHOME if set
# this will fail if PYTHONHOME is set to the empty string (which is bad anyway)
# could use `if (set -u; : $PYTHONHOME) ;` in bash
if [ -n "${PYTHONHOME:-}" ] ; then
    _OLD_VIRTUAL_PYTHONHOME="${PYTHONHOME:-}"
    unset PYTHONHOME
fi

if [ -z "${VIRTUAL_ENV_DISABLE_PROMPT:-}" ] ; then
    _OLD_VIRTUAL_PS1="${PS1:-}"
    PS1="(venv) ${PS1:-}"
    export PS1
fi

# Call hash to forget past commands. Without forgetting
# past commands the $PATH changes we made may not be respected
hash -r 2> /dev/null
```

通过修改 `bashrc` 等文件，来配置启动项，这些命令会在终端启动时自动执行。

```bash
export NVM_DIR="$HOME/.nvm"
  [ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh"  # This loads nvm
  [ -s "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion

# export https_proxy=http://127.0.0.1:1082 http_proxy=http://127.0.0.1:1082 all_proxy=socks5://127.0.0.1:1082
export https_proxy=http://127.0.0.1:7897 http_proxy=http://127.0.0.1:7897 all_proxy=socks5://127.0.0.1:7897
export PATH="/opt/homebrew/opt/llvm/bin:$PATH"
export LIBRARY_PATH="$LIBRARY_PATH:$(brew --prefix)/lib"

alias python="python3"

alias c="clear"
alias i="cd ~/CodeFile"
alias ir="cd ~/CodeFile/Rust"
alias in="cd ~/CodeFile/node"
alias cb="cargo build"
alias cr="cargo run"
export DVM_DIR="/Users/echo/.dvm"
export PATH="$DVM_DIR/bin:/Users/echo/go/bin:$PATH"

source /Users/echo/.docker/init-zsh.sh || true # Added by Docker Desktop
```

对于单个用户来说，它们一般在用户的 home 目录下 `.bashrc` 或 `.zshrc`。对于全局来一般在 `/etc/profile` 或 `/etc/bashrc`。

>  linux 配置环境变量如此简单，windows 就是 💩

---

`cd -` 命令，回到上一次的目录，可以用来在两个目录中跳转。

`ctrl l` 代替 `clear` 用来清屏。

`tee` 命令感觉很实用，有时间可以深入了解一下。

### 01.07

> 学习时间：60 min

---

**大多数 shell 都有自己的一套脚本语言，包括变量、控制流和自己的语法。**

据我所知，特别是 fish 的脚本语言与 bash 有很大不同。我们在写脚本时添加 `#!/bin/sh` 就能消除由于使用的 shell 不同导致脚本无法通用的问题。

---

高级 Bash 脚本编写指南：https://tldp.org/LDP/abs/html/special-chars.html

> `$0` - 脚本名
> 
> `$1` 到 $9 - 脚本的参数。 $1 是第一个参数，依此类推。
> 
> `$@` - 所有参数
> 
> `$#` - 参数个数
> 
> `$?` - 前一个命令的返回值
> 
> `$$` - 当前脚本的进程识别码
> 
> `!!` - 完整的上一条命令，包括参数。常见应用：当你因为权限不足执行命令失败时，可以使用 sudo !! 再尝试一次。
>
> `$_` - 上一条命令的最后一个参数。如果你正在使用的是交互式 shell，你可以通过按下 Esc 之后键入 . 来获取这个值。

---

tldr 命令：比 man 更简短的手册查询

---

||：“逻辑或” 操作，只有当左侧命令失败（退出状态码非 0）时，才会执行右侧命令。（两条命令中至少执行一个？）

&&：“逻辑与” 操作，只有当左侧命令成功（退出码为 0）时，才会执行右侧命令。（两台命令都要执行？）

---

<(CMD) 的作用是将命令 CMD 的输出提供给需要文件名作为输入的程序，而不是直接通过管道 | 传递数据。

> 没用过，抽时间熟悉

---

使用 `?` 和 `*` 来匹配一个或任意个字符。`*` 通配符知道，但是使用 `?` 匹配单个字符还是第一次了解。

`{}` 当命令中有公共子串时，可以用来简化命令。例如：

```bash
convert image.{png,jpg}
# 会展开为
convert image.png image.jpg

cp /path/to/project/{foo,bar,baz}.sh /newpath
# 会展开为
cp /path/to/project/foo.sh /path/to/project/bar.sh /path/to/project/baz.sh /newpath
```

---

`env` 命令，用于显示系统中存在的所有环境变量，用在 `shebang` 中可以增加脚本的通用性。

就拿 Python 来说，毕竟不是所有人都会讲它安装在相同的目录中，`#!/usr/bin/env python` 就能解决这个问题。

---

shellcheck 强大的 sh 脚本检查器

```
#!/bin/bash

# 检查PID文件是否存在
if [ ! -f zkrock.pid ]; then
  echo "PID file not found. Is zkrock running?"
  exit 1
fi

# 读取PID
PID=$(cat zkrock.pid)

# 停止进程
kill $PID

# 等待进程结束
sleep 1

# 检查进程是否成功停止
if ps -p $PID > /dev/null; then
   echo "Failed to stop zkrock. Force stopping..."
   kill -9 $PID
fi

# 删除PID文件
rm zkrock.pid

echo "Zkrock stopped."
```

检查出来有下面这些可以优化的地方

```
In stop.sh line 13:
kill $PID
     ^--^ SC2086 (info): Double quote to prevent globbing and word splitting.

Did you mean:
kill "$PID"


In stop.sh line 19:
if ps -p $PID > /dev/null; then
         ^--^ SC2086 (info): Double quote to prevent globbing and word splitting.

Did you mean:
if ps -p "$PID" > /dev/null; then


In stop.sh line 21:
   kill -9 $PID
           ^--^ SC2086 (info): Double quote to prevent globbing and word splitting.

Did you mean:
   kill -9 "$PID"
```

---

视频里讲了很多工具，我认为比较重要的是 `fzf` 和 `ripgrep`。有很多实用插件都是基于它们实现的。

---

课后练习暂时不做了

### 01.08

> 学习时间：70 min

---

`sed` 是一个流编辑器，可以用来替换文本中的内容，替换的命令为 `s` : `s/REGEX/SUBSTITUTION/`（这在 vim 中也很常用）

其中 `REGEX` 部分是正则表达式，`SUBSTITUTION` 是用于替换匹配结果的文本。

```bash
ssh myserver journalctl
 | grep sshd
 | grep "Disconnected from"
 | sed 's/.*Disconnected from //'
```

---

正则表达式在线调试工具：https://regex101.com/

正则表达式这部分让我想到了之前在学编译原理时还想自己实现一个正则解析器，收藏了很多资料但一直没有开始。等空下来可以去实现来玩玩。

正则表达式在某些情况下会非常复杂，它**是**万能的又**不是**万能的，若你要解析 `json` 等结构，有更好的工具可以使用，不用强求去使用正则。

---

平时的数据处理，我几乎只会使用 `cat` `tail` `grep`

`awk` 编程语言介绍：https://backreference.org/2010/02/10/idiomatic-awk/

推荐一个网站 **Learn x in y minutes（y 分钟学习 x）**：https://learnxinyminutes.com/

---

MLK DAY 马丁·路德·金纪念日 它们居然还会放假

---

数据处理这部分讲了很多工具的使用，没有太多可以记录的东西，主要是了解这些工具，日后遇到一些情况就可以使用它们。

工具一定是越用越熟练的，平时也需要有意识地去使用这些数据处理的工具。就算不用课程中讲到的工具，python、lua 等更现代的脚本语言也是一个很好的选择。

### 01.09

> 学习时间：60 min

---

vscode neovim 插件 https://marketplace.visualstudio.com/items?itemName=asvetliakov.vscode-neovim

一些配置

```json
{
  "vscode-neovim.neovimExecutablePaths.linux": "/usr/bin/nvim",
  "vscode-neovim.neovimInitVimPaths.linux": "$HOME/.config/nvim/init.lua",
  "vscode-neovim.compositeKeys": {
    "jk": {
      "command": "vscode-neovim.lua",
      "args": [
        "vim.api.nvim_input('<ESC>')\nrequire('vscode-neovim').action('workbench.action.files.save')"
      ]
    }
  },
}
```

---

- 行： 0 （行初）， ^ （第一个非空格字符）， $ （行尾）
- 屏幕： H （屏幕首行）， M （屏幕中间）， L （屏幕底部）

---

**宏**

`q{字符}` 来开始在寄存器 `{字符}` 中录制宏

`q` 停止录制

`@{字符}` 重放宏

---

因为本身比较熟悉 `vim` 的操作，所以这部分直接快速掠过了，仅记录了一些之前没用过以及觉得比较重要的内容。

然后花了一点时间来配置 `neovim`。（`neovim` 是更现代化的 `vim` 可以使用 `lua` 语言来进行配置）简单做些记录。

`neovim` 目前已经有很多成熟的配置 [Lazyvim](https://www.lazyvim.org/)、[NvChad](https://nvchad.com/)

初次尝试 `neovim` 可以选择其一进行体验，它们的官网中都提供了插件配置的教程，想要切换也非常简单，只需要删除或重命名 `~/.config/nvim` 文件夹，然后换上新的配置即可。

```bash
➜  ~ ls ~/.config | grep "nvim"
nvim
nvim.astron-back
nvim.lazy-back
nvim.self-back
nvim.tar.gz
```

我计划基于 https://github.com/nvim-lua/kickstart.nvim 进行配置，因为 `Lazyvim` 与 `NvChad` 的配置非常庞大与复杂（在 1c1g 的服务器上甚至能把内存干满），有很多我不需要的功能，一些快捷键也不是我习惯的，并且定制其中一些插件会非常复杂，牵一发而动全身。

`kickstart` 是一个非常精简的 neovim 初始配置。但也不是直接将它克隆下来然后做定制。而是从零开始配置，参考它的文件结构以及配置内容。

这样才能做到在最小的化的安装下尽可能满足自己的要求，日后做修改也非常容易，毕竟配置是自己一个字一个字写的。

### 01.10

> 学习时间：70 min

今天主要是在尝试对 `neovim` 进行配置，花了 20 分钟在 `learnxinyminutes` 上快速过了一遍 `lua` 语言，剩下时间主要在熟悉 `kickstart` 项目。

### 01.11

> 学习时间：70 min

主要在回顾本周内容，也有一些新的想法记录在下面：

---

`tee` 命令可以用来用做两个命令之间的连接。

> Read from `stdin` and write to `stdout` and files (or commands).

---

`foobar` 文化，在你不知道如何命名时通常使用它们，类似中文环境下的小明、小红。

---

常用文件描述符：

* `0` 表示 `stdin`
* `1` 表示 `stdout`
* `2` 表示 `stderr`
* `/dev/null` 表示空文件

`stdout` 和 `stderr` 默认都是将信息输出到终端上，但是它们还是有区别。

```C
int main(){
  fprintf(stdout,"Hello ");
  fprintf(stderr,"World!");
  return0;
}
```

上面这段代码的输出是 `World!Hello `。

在默认情况下，`stdout` 是行缓冲的，他的输出会放在一个 `buffer` 里面，只有到换行的时候，才会输出到屏幕。而 `stderr` 是无缓冲的，会直接输出。

---

在不知道脚本运行文件的位置时，使用 `#!/usr/bin/env <CMD>`

---

**到底什么是 Shell**

shell 直译过来是 “外壳”，它是一种特殊的用户程序，给用户提供了使用操作系统服务的接口。shell 接受用户输入的人类可读的命令，并将其转换为内核可以理解的内容，当用户启动终端时，shell 就会启动。

shell 有两类：命令行 shell（CLI） 和图形 shell（GUI）。

shell 也是一种编程语言，与我们常见的脚本语言 python、lua 类似，它们都有一个交互式编程环境，这个环境叫做 `REPL`（Read-Eval-Print-Loop）。我们使用 shell 其实就是在使用它的 REPL。

---

继续 `neovim` 的配置

### 01.12

> 学习时间：120 min

`kill` 命令经常用，但是不知道使用 `-9` 选项有什么作用，下面是 GPT 给我的答案：

>  kill 命令可以发送多种信号给进程，默认情况下，它发送 SIGTERM 信号（信号编号 15），这是请求进程正常结束的信号。以下是一些常用的信号：
>
> * SIGTERM (15)：请求进程正常终止，允许进程清理资源和文件等。进程可以选择忽略这个信号。
> * SIGKILL (9)：强制立即终止进程，无法被进程捕获或忽略。通常用于终止无法正常结束的进程。
> * SIGINT (2)：通常由用户通过按下 Ctrl + C 发送给前台进程，用于中断进程。
> * SIGHUP (1)：通常用于通知进程重新加载配置文件，或者由于连接丢失而终止进程。
> * SIGSTOP (19)：暂停（挂起）进程，不能被进程捕获或忽略。与 SIGCONT 相反，后者用于恢复暂停的进程。

> `SIGKILL` 是一个特殊的信号，它不能被进程捕获并且它会马上结束该进程。不过这样做会有一些副作用，例如留下孤儿进程。（不知道竟然还会有这样的问题。）

---

`Ctrl-Z` 会暂停一个进程。

`fg` 和 `bg` 命令可以恢复暂停的工作。它们分别表示在前台继续或在后台继续。

`jobs` 命令会列出当前终端会话中尚未完成的全部任务。

---

**tmux 使用与配置**

之前用过一段时间 tmux 但是觉得操作挺复杂，并且没有配置好，就没有使用了。后面还是应该用起来。

tmux 快速入门教程 https://hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/

---

**Dotfiles**

> 我们应该如何管理这些配置文件呢，它们应该在它们的文件夹下，并使用版本控制系统进行管理，然后通过脚本将其 符号链接 到需要的地方。

这也是我管理配置文件的方式。

**配置的可移植性**

之前有考虑过这个问题，但是也是觉得太复杂了就没有去弄

```shell
if [[ "$(uname)" == "Linux" ]]; then {do_something}; fi

# 使用和 shell 相关的配置时先检查当前 shell 类型
if [[ "$SHELL" == "zsh" ]]; then {do_something}; fi

# 您也可以针对特定的设备进行配置
if [[ "$(hostname)" == "myServer" ]]; then {do_something}; fi
```

---

关于 ssh 密钥，通常我们使用 `ssh-copy-id` 命令来实现免密登陆，可以避免手动复制错误导致的问题。

---

关于上传文件到服务器中，我发现居然大部分人还不知道有 `scp` 命令。

---

pgrep 与 pkill，我们不用先去查进程号，可以直接通过进程名来查找与终止进程

---

使用 `dotfiles` 管理配置文件，我们需要手动 `ln -s` 去链接配置文件，也可以使用一些用于管理配置文件的工具：https://dotfiles.github.io/utilities/

---

**ssh 参数**

`-N` 就是不执行远端命令，适用于端口转发的情况，`-f` 是让 ssh 在执行命令前切换到后台运行。

后台进行端口转发 `ssh -fN -L 9999:localhost:8888 user@remotehost`

---

**一个有趣的问题**

> https://unix.stackexchange.com/questions/185793/why-is-it-while-kill-0-pid-and-not-until-kill-0-pid

我们需要明确的是：**在 Shell 中 ‘0’ 表示成功，非零表示失败**。

在 bash 脚本中 `while` 命令不是寻找布尔值，而是寻找返回码 `0`，这表明命令执行成功。因此，在 `while` 命令的情况下，返回 `0` 的命令是**真**，其他任何值都是**假的**。

```bash
while compound-list-1
do
    compound-list-2
done
```

将执行 `compound-list-1`，如果它具有非零退出状态，则 `while` 命令将完成。否则，将执行 `compound-list-2`，并重复该过程。

### 01.13

> 学习时间： 60 min

---

```
feat	    新特性，新功能
fix	      修bug
docs	    更新文档
style	    修改代码风格、代码格式（不影响代码运行的变动）
refactor	重构代码（既不是新增功能，也不是修改bug，可以理解为觉得原本写太烂了，重新写了一遍）
perf	    优化性能、优化体验
test	    测试
chore	    构建过程或者辅助工具的变动
revert	  回滚版本
merge	    代码合并
sync	    同步主线或分支
```

比较好用的一个查看提交记录的命令 `git log --graph --all --decorate --oneline`

---

简单来讲，git 存储的是 `object` 的有向无环图（DAG），

**基本结构**

```text
type blob = array<byte>

type tree = map<string, tree | blob>

type commit = struct {
    parents: array<commit>
    author: string
    message: string
    snapshot: tree
}

type object = blob | tree | commit
```

**寻址结构**

```text
objects = map<string, object>

def store(object):
    id = sha1(object)
    objects[id] = object

def load(id):
    return objects[id]
```

**引用**

```text
references = map<string, string>

def update_reference(name, id):
    references[name] = id

def read_reference(name):
    return references[name]

def load_reference(name_or_id):
    if name_or_id in references:
        return load(references[name_or_id])
    else:
        return load(name_or_id)
```

> 当您输入某个指令时，请思考一下这条命令是如何对底层的图数据结构进行操作的。

---

如何编写良好的 git commit message：https://cbea.ms/git-commit/

---

一个使用 Rust 实现的轻量 git 项目：https://github.com/MrBeanCpp/MIT

---

<!-- Content_END -->