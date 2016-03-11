---
layout: post
title: 基本的bash shell命令
category: 学习笔记
tags: [linux,bash,shell]
keywords: linux,bash,shell
description:
---

## 基本的bash shell命令

### 处理文件和目录

* `ls` 输出目录
    - -s 显示文件大小
    - -a 输出隐藏文件
    - -i 显示文件的索引值
    - -l 产生长列表的输出
    - -R 递归列出子目录内容
* `touch` 创建新文件或者改变访问/修改时间
    - -a 只改变访问时间
    - -m 只改变修改时间
    - -t 指定时间戳
* `cp` 复制文件
    - -f 强制覆盖不提示
    - -i 覆盖前提示
    - -r 递归的复制文件
    - -R 递归的复制目录
    - -l 创建文件链接（硬链接）
    - -s 创建符号链接（软连接）
    - -v 详细模式
* `mv` 移动文件（重命名）
* `rm` 删除文件
    - -i 删除前提示
    - -f 强制删除不提示
    - -r 递归删除非空目录
* `mkdir` 创建目录
* `stat` 提供文件的所有状态信息
* `file` 查看文件类型
* `cat` 显示文本数据
    - -n 给所有行加上行号
    - -b 给有文本的行加上行号
    - -s 多个空白行压缩为一行
    - -T 用^I替换制表符
* `more` 分页显示
    - 空格 显示下一屏
    - ENTER 显示下一行
    - /expression 查找
    - n 查找下一处匹配的内容
    - ' 调到匹配的第一处内容
    - !cmd 执行shell
    - v 在当前行启动vi
    - = 显示当前行号
    - . 执行前一条命令
* `sort` 读文本文件中的数据行排序
    - -n 数字识别为数字
    - -M 按月排序（常用于日志文件）
    - -r 反序
    - -b 忽略起始的空白
    - -t 指定字段分隔符
    - -k 指定排序字段
* `tail` 显示文件末尾的内容
    - -c *bytes* 显示文件最后的bytes字节的内容
    - -n *lines* 显示文件最后的lines行
    - -f 保持活动，有新内容添加到末尾就显示
    - -s sec 与-f一起，每次输出前休眠sec秒ps
    - -v 显示带文件名的头
    - -q 从不显示带文件名的头
* `head` 显示文件开头的内容，类似tail
* `grep` *[option] pattern [file]* 查找文件中大的一行数据
    - -v 输出不匹配的行
    - -n 显示匹配行的行号
    - -c 输出匹配的行数
    - -e 指定多个匹配字符串（满足任意一个），通常用正则表达式替代
* `egrep` 支持POSIX扩展正则表达式
* `tar` *function [options] obj1 obj2* 归档
    - -A 将一个tar文件追加到另一个tar文件
    - -c 创建新的tar归档文件
    - -r 追加文件到tar文件末尾
    - -x 从tar文件中提取文件
    - -C 切换到指定目录
    - -f 输出结果到文件或设备
    - -j 将输出重定向为bzip2
    - -z 将输出重定向给gzip
    - -p保留所有文件权限
    - -v 处理文件时显示文件

实例：
        
        //解压.tgz
        tar -zxvf filename.tgz


### 进程和设备管理

* `ps` 检测进程
    - -A 显示所有进程
    - -e 显示所有进程
    - -p *pidlist* 显示指定pid的进程
    - -f 显示完整格式的输出
    - -F 显示更多额外输出（相对-f而言）
    - -l 显示长列表
    - -L 显示进程中的线程
    - -H 用层级格式显示进程
    - --forest 图表形式显示层级信息
* `top` 实时显示进程信息，__很有用__，详见man
* `kill` *pid* 结束进程（默认发送TERM信号）
    - -s *signal* 发送其他信号
* `killall` *name* 通过进程名结束进程
* `mount` 挂载媒体设备，详见man
实例：
        
        //挂载iso文件
        mount -t iso9660 -o loop file_name.iso /path/to/

* `unmonut` 卸载设备
    >当提示设备繁忙无法卸载设备时可使用`lsof`命令获得使用它的进程信息
* `df` 查看已挂载磁盘的使用情况
    - -h human-readable
* `du` 显示当前目录下所有文件、目录、子目录占用的磁盘块数
    - -c 显示所有已列出文件的总大小
    - -h human-readable
    - -s 显示每个输出参数的总计

### 系统和权限

* `set` 显示进程的所有环境变量
* `export` *var* 将局部变量导出为全局变量
* `unset` *var* 删除环境变量
* `alias` 设置命令别名
    - -p 显示已有的别名列表
实例：
        
        //定义命令别名
        alias li='ls -il'

* `useradd` 创建用户
    - -c *comment* 添加备注
    - -d *home_dir* 为主目录指定一个名字（默认即home）
    - -D *YYYY-MM-DD* 显示设置用户的系统默认值
    - -g *initial_group* 指定用户登录组的GID或组名
    - -G *group* 指定除登录组外的附加组
    - -k 与-m一起使用，将/etc/skel目录的内容复制到HOME目录，（bash shell的标准启动文件）
    - -m 创建HOME目录
    - -r 创建系统用户
    - -p *passwd* 指定默认密码
    - -s *shell* 指定默认登录shell
    - -u *uid* 为账户指定唯一的uid
* `userdel` 删除用户（默认只删除/etc/passwd文件中的用户信息）
    -  -r 删除HOME目录和mail目录
* `usermod` 修改用户信息，参数与useradd基本相同
    - -l 修改用户登录名
    - -L 锁定账户，无法登录
    - -p 修改账户密码
    - -U决出锁定
* `groupadd` 添加新组
* 

