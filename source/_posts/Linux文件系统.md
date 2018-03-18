---
title: Linux文件系统
date: 2017-11-07 08:29:40
update: 2017-11-07 08:29:40
categories: Linux知识
tags:

---

## 文件系统

### 1.分层

第一层：虚拟文件系统(VFS)   第二层：具体文件系统（FATFS等）    

VFS封装底层，向C标准库提供系统调用接口

<!-- more -->

## I/O操作

Linux将设备当作文件来处理。

### 1.分类

非缓冲式I/O操作：系统调用提供           缓冲式：C标准输入输出库函数提供

非缓冲式用“文件描述符”来表示文件



### 2.文件标识符

0——标准输入，从键盘输入     1——标准输出，输出到终端    2——标准错误，存放错误信息的堆栈



### 3.标准I/O

三种缓冲类型：全缓冲、行缓冲、不带缓冲

文件指针：文件的各种**信息存在结构体FILE**中，流（stream）用指针FILE *来描述



### 4.文件和目录操作

文件类型：

- 目录文件（directory file）		
  - 普通文件（regular file）	
- 字符设备文件（char device file）
- 块设备文件（block device file）
- FIFO
- 套接字（Socket）
- 符号链接（symbolic link）

文件访问权限：用ls -l会看到文件具体信息，最前方的是**10个字符的字符串**表示文件类型和访问权限

``` 
 -rwxr-xr-x 1 root root 6444 09-22 15:33 shmwrite
 -rw-r--r-- 1 root root 1443 09-22 15:33 shmwrite.c
 drwxr-xr-x 2 root root 4096 09-22 17:19 test
```

​	第一个字符表示文件类型。**d代表目录，-代表非目录** 。 后边的都是**三个字符为一组权限**，		  

​	分三组。依次表示，**所有者权限（当前用户），同组用户权限，其它用户权限**。

​	r,读权限；w，写权限；x，可执行权限；-没权限。**

文件属性：判断文件存不存在可以用stat/open。

​	stat结构体：st_mode——判断文件类型，比如是不是可执行文件



常用函数：

stat：可以获取文件的一些状态：大小、修改时间等。结果保存在stat结构体变量里。

DIR * opendir(const char * name)：打开文件夹，返回值是DIR *类型

struct dirent * readdir(DIR * dir)：**联合while，可遍历**文件夹内所有文件。