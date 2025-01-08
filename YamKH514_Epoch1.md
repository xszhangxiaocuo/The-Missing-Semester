# CFC Studio 共学 Epoch1 指引
---
# [YamKH514]

> 一般路过，不必在意

## 笔记证明

### 01.06

Duration of study: 1h \
What did I learn today: The Shell

Try to use English handouts and study note.

` which ` Programe \
Using ` which ` to find out the address which argument you entered.

    ~/The-Missing-Semester$ which which
    /usr/bin/which

今天先到这儿，有几科重量级还要复习 ⊙﹏⊙∥

### 01.08

Duration of study: 1h \
What did I learn today: Using the Shell

A path on the shell is a delimited list of directories \
It separated by ` / ` on Linux or X OS and ` \ `on Windows. \
We can use ` pwd ` to get currented path, ` ls ` to list files and directories on currented path, ` cd ` to change currented working directory. \
Entering ` ls -l /home `, the shell will output:
```bash
ren@ren-VMware-Virtual-Platform:~/The-Missing-Semester$ ls -l /home
total 4
drwxr-x--- 27 ren ren 4096 Jan  8 23:13 ren
```
Using ` -l ` to get more infomation about each file or directory present.
The ` drwxr-x--- ` indicate what permissions the owner of the file (`ren`), the owning group (`ren`), and everyone else respectively have the given permission. \
- ` - ` indicates that the grpup or user does not have the given permission.
- ` w ` indicate ` modify `
- ` r ` indicate ` read `
- ` x ` indicate ` execute `. If you want to enter a directory, you need this permission.

Using `man` programe to get more information about a programe, like:
```base
$ man ls
```
