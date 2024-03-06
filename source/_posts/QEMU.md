---
title: QEMU
date: 2024-03-03 16:57:53
tags:
- 操作系统
- 大二下
---
### 命令
~~~
.\qemu-img create -f raw try2.img 40G 
.\qemu-img create -f raw myimage.img 60G
~~~
创建一个60G的raw格式磁盘

<br>

~~~
.\qemu-system-x86_64 -m 4G -hda try2.img -cdrom ubuntu-22.04.4.iso -boot order=d
~~~
安装ubuntu

~~~
.\qemu-system-x86_64 -m 4G -hda try2.img -bios bios.bin
~~~
启动安装的磁盘（没试过不知道效果）

~~~
-machine/-M 设备类型
-m 内存大小
-smp 核心数
-drive 驱动器映像文件
- netdev 网络设备配置

~~~
[参考博客1](https://blog.csdn.net/weixin_39871788/article/details/123250595)


### linux MBR相关内容
* 查看磁盘 fdisk -l
    - 如果失效的话记得su root获得权限 
        - 再失效记得用sudo passwd root创建root
* 备份mbr到mbr.bin
~~~
dd if=/dev/sda of=mbr.bin bs=446 count=1
~~~
* 查看
~~~
xxd mbr.bin
~~~
* 反编译
~~~
objdump -D -b binary -mi386 -Maddr16,data16 mbr.bin
~~~

### windows查看磁盘信息指令
打开cmd，输入diskpart再enter
~~~
list disk：查看磁盘，分区格式
list volume：看到当前系统中的全部分区、盘符。
~~~

   
