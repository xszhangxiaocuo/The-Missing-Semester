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
```bash
$ man ls
```

### 01.09

Duration of study: 1h \
What did I learn today: Using the Shell

Normally, a programe's input and output are both our terminal. We can use `< file` and `> file` to rewire the input and output streams of a program to a file. We can also use `>>` to append to a file.
```bash
ren@ren-VMware-Virtual-Platform:~$ echo hello > hello.txt
ren@ren-VMware-Virtual-Platform:~$ cat hello.txt 
hello
ren@ren-VMware-Virtual-Platform:~$ cat < hello.txt 
hello
ren@ren-VMware-Virtual-Platform:~$ echo world >> hello.txt 
ren@ren-VMware-Virtual-Platform:~$ cat hello.txt 
hello
world
```
The `|` operator lets us "chain" programe such that the output of one is the input of another.
```bash
ren@ren-VMware-Virtual-Platform:~$ ifconfig | grep 192
        inet 192.168.10.134  netmask 255.255.255.0  broadcast 192.168.10.255
```

Homework

```bash
ren@ren-VMware-Virtual-Platform:/tmp$ mkdir missing
ren@ren-VMware-Virtual-Platform:/tmp$ cd ./missing/
ren@ren-VMware-Virtual-Platform:/tmp/missing$ touch semester
ren@ren-VMware-Virtual-Platform:/tmp/missing$ chmod 777 semester
ren@ren-VMware-Virtual-Platform:/tmp/missing$ ./semester | grep last-modified > ~/last-modified.txt
ren@ren-VMware-Virtual-Platform:/tmp/missing$ cat ~/last-modified.txt
last-modified: Sat, 21 Dec 2024 16:53:01 GMT
```
