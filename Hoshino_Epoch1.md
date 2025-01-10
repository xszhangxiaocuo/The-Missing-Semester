# CFC Studio 共学 Epoch1 指引
---
# Hoshino

> I'm joker king.

## 笔记证明

### 01.06

Study Time: 3h (Allright, I spend most of my time on reading English text, it's so hard for me.)

#### Note

The shell is a textual interface for computer, they allow you to run programs, give them input, and inspect their output in a semi-structured way.

The shell is a programming environment.Running a command in the shell is similar to writing a piece of code that the shell interprets and executes. When a command is entered, the shell searches for an executable program either in the directories listed in the `$PATH` environment variable or in the current directory (if specified explicitly).

#### Exercises

In `shell scripting` and `command-line operations`, the difference between **single quotes**`''` and **double quotes** `""`  lies in how they handle variables, special characters, and escape sequences. 

Everything inside single quotes is treated literally. Variables, escape characters, and special characters are not interpreted; they are taken as plain text.But double quotes allow the interpretation of variables, escape sequences, and command substitutions, while preserving spaces and special characters as part of the string.

![image-20250106220057226](https://minio.drivefly.cn:443/image-hoshino/blog/2025/01/06/image-20250106220057226.png)

This command line performs four operations.Firt, it runs the `./semester` to get some info.Second, `grep` filters the output of `./semester` to include only lines containing the string `last-modified`.Third, `cut` extracts specific fields from the lines filtered by grep(`-d' '` specifies that fields in the line are separated by spaces, `-f2-` instructs `cut` to output everything from the second field onwards).At last, `>` will  redirect the output of the previous commands to a file named `last-modified.txt`.

![image-20250106220743702](https://minio.drivefly.cn:443/image-hoshino/blog/2025/01/06/image-20250106220743702.png) 

### 01.10

Study Time: 2h.

#### Note

The last lecture has said that the `shell` is a programming enviroments, so most shells have their own scripting language with variables, control flow and its own syntax.Therefore, I think using `shell script` is just writing a short piece of code.

> Notice：`shell` and `shell script` are different things. `shell` is an application that provides an interface through which users access the services of the operating system kernel.But `shell script` is a program written for `shell`.
>

Unlike other programming languages we know, in `bash`, whitespace is a special keyword, it is used to split the parameters.And `bash` uses a variety of special variables to refer to arguments, error codes, and other relevant variables.

In `bash`, commands can be used to conditionally execute commands using `&&` (and operator) and `||` (or operator), both of which are short-circuiting operators.

Whenever you place `$( CMD )` it will execute `CMD`, get the output of the command and substitute it in place. A lesser known similar feature is *process substitution*, `<( CMD )` will execute `CMD` and place the output in a temporary file and substitute the `<()` with that file’s name.

When performing comparisons in `bash`, try to use double brackets `[[ ]]` in favor of simple brackets `[ ]`. Chances of making mistakes are lower although it won’t be portable to `sh`. A more detailed explanation can be found [here](http://mywiki.wooledge.org/BashFAQ/031).

The shell *globbing* can help you to provide arguments that are similar.

> - Wildcards - Whenever you want to perform some sort of wildcard matching, you can use `?` and `*` to match one or any amount of characters respectively. For instance, given files `foo`, `foo1`, `foo2`, `foo10` and `bar`, the command `rm foo?` will delete `foo1` and `foo2` whereas `rm foo*` will delete all but `bar`.
> - Curly braces `{}` - Whenever you have a common substring in a series of commands, you can use curly braces for bash to expand this automatically. This comes in very handy when moving or converting files.

Note that scripts need not necessarily be written in bash to be called from the terminal.Because if a text file begin with the `shebang` line(a line starting with `#!`), then the `kernel` will know to execute this script with which interpreter,, so we can also use  a python interpreter by using `#!/usr/local/bin/python`(like this).

It is good practice to write `shebang` lines using the [`env`](https://www.man7.org/linux/man-pages/man1/env.1.html) command that will resolve to wherever the command lives in the system, increasing the portability of your scripts. To resolve the location, `env` will make use of the `PATH` environment variable we introduced in the first lecture. For this example the `shebang` line would look like `#!/usr/bin/env python`.

> When a text file with a `shebang` is used as if it were an executable in a Unix-like operating system, the program loader mechanism parses the rest of the file's initial line as an interpreter directive.

> Some differences between shell functions and scripts that you should keep in mind are:
>
> - Functions have to be in the same language as the shell, while scripts can be written in any language. This is why including a shebang for scripts is important.
> - Functions are loaded once when their definition is read. Scripts are loaded every time they are executed. This makes functions slightly faster to load, but whenever you change them you will have to reload their definition.
> - Functions are executed in the current shell environment whereas scripts execute in their own process. Thus, functions can modify environment variables, e.g. change your current directory, whereas scripts can’t. Scripts will be passed by value environment variables that have been exported using [`export`](https://www.man7.org/linux/man-pages/man1/export.1p.html)
> - As with any programming language, functions are a powerful construct to achieve modularity, code reuse, and clarity of shell code. Often shell scripts will include their own function definitions.