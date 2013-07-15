---
layout: post
title: "ubuntu graphic crash"
description： "ubuntu 13.10经常在操作的时候图形界面卡死，导致系统无响应，之前一直都是采取强制关机来恢复。查阅资料之后通过如下方法可以在不重启电脑的情况下解决图形界面卡死的问题。"
category: learning
tags: [ubuntu]
---
{% include JB/setup %}
## 问题描述
ubuntu启动之后，图形界面卡死。

## 问题解决
1. Ctrl + Alt + F1
2. ps -t tty7 找到Xorg的进程号xxx
3. kill -9 xxx 即可重启ubuntu图形界面
