---
layout: post
title: 开机流程中的事儿
category: 技术
tags: [UEFI,GPT,BIOS,MBR]
keywords: UEFI,BIOS,开机引导
description: 
---

## 一些基本概念

### MBR分区表

>MBR - Master Boot Record 主引导记录/主引导扇区

MBR分区方案中硬盘的每个扇区通过32位二进制数逻辑块地址（LBA）来标识。计算机开机后访问硬盘时要先读取第一个扇区，这个扇区（通常有512bytes）储存着主引导记录MBR（446bytes）和分区表DPT（64bytes）。主引导记录中装有引导程序（boot loader），分区表中记录了磁盘分区情况。由于每一条分区记录需要16个字节，因此MBR分区结构只能支持4个主分区，想得到4个以上的分区需要采用扩展分区，注意扩展分区只能有一个，在windows系统中默认划分一个主分区给系统，其余的全部划入扩展分区。扩展分区可以划分出多个逻辑分区。
![img](/assets/img/images/2015-10-23-about-booting_1.png)

MBR的局限性在于，分区表大小固定，只能支持4个主分区，而且最大只能支持到2.2TB的分区容量。随着硬盘技术的发展，MBR分区方案有些撑不住了，再加上win8/8.1的催化，GPT分区表逐渐成为主流。

### GPT分区表

>GPT - GUID Partition Table 全局唯一标识分区表

先睡觉去了。。



