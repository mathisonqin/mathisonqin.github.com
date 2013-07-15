---
layout : post
title : "重装win7后修复ubuntu启动项"
description : "重装win7后修复ubuntu启动项"
category : learning 
tags: [ubuntu, boot]
---
{% include JB/setup %}
##问题描述
电脑在安装了win7系统之后，又通过硬盘安装的方式安装了ubuntu系统。后来win7系统重装，导致ubuntu引导项丢失。

##问题解决
之前遇到这个问题，我都是不假思索就直接重新安装ubuntu，其实，ubuntu系统并没有被破坏，它仍然安装在我电脑的最后一个硬盘分区中，只是缺少了一个开机引导项来引导ubuntu,使用EasyBCD重新建立ubuntu的引导项即可解决该问题。

下面是EasyBCD的界面：  
![EasyBCD的界面](/images/2013-06-22-ubuntu-boot/easybcd.jpg)  
在windows7下安装完成后打开EasyBCD，单击左侧的“Add New Entry”，然后在“Operating Systems”中选择“Linux/BSD”选项卡，“Type”中选择“GRUB 2”，下面的名字可以改，比如改为“ubuntu”，然后点击下面的“Add Entry”即可。可以参照下面的图示：  
![EasyBCD添加ubuntu引导项](/images/2013-06-22-ubuntu-boot/easybcd_entry.jpg)  
重新启动计算机后，会出现windows7的启动管理器，您会发现已经加入了ubuntu（若您没有为其改名将显示NeoSmart Linux）。当您选择进入时，系统会自动搜索到正确位置，然后熟悉的Grub2界面就会出现在您面前了。您可以选择进入各种ubuntu模式，或者再次 进入windows7。

