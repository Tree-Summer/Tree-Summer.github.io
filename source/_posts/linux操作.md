---
title: linux操作
date: 2024-03-04 17:39:52
tags:
- 操作系统
- 大二下
- method
---
### dd:用于读取，转换并输出数据
* if= 文件名：输入文件名，默认为标准输入。
* of=文件名：输出
* ibs=bytes：一次读入bytes个字节
* obs=bytes：一次输出bytes个字节
* bs=bytes：同时设置读入/输出的块大小为bytes个字节
* count=blocks：仅拷贝blocks个块
* --help：显示帮助信息
* --version：显示版本信息

### objdump
* -d：将代码段反汇编
* -S：将代码段反汇编的同时，将反汇编与源代码交替显示，编译时要使用-g参数，即需要调试信息
* -C：将C++符号名逆向解析
* -l：反汇编代码中插入文件名和行号
* -j section ：仅返汇编指定的section
* --help


