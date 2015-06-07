---
author: kresnikwang
comments: true
date: 2013-08-31 08:48:40+00:00
layout: post
slug: chromium_u0026_amp_nbsp_os__open_edition_chrome_u0026_amp_nbsp_os_installation_and_audio_playback_in_flash_and_pdf_correction_plug-in
title: Chromium OS(开放版Chrome OS)下Flash和Pdf插件的安装及音频播放修正
wordpress_id: 22
categories:
- Tech
tags:
- Chromium OS
---

最近用了Vanilla的U盘装了Chromium OS来用，真心快！但是没有Flash插件和Pdf插件对于我而言几乎啥事都做不了了，为了发挥Chromium
OS的实际用途，必须给他安上这些插件。

本质上，Chromium OS是基于Linux的系统，网上有大神的方法是在Linux下mount用来装Chromium OS的U盘的第一分区，获取权限之后，直接把Firefox下的flash提取出来，写到Chromium OS下。太牛逼了，我搞不了。。。。

于是就借鉴了国外GitHub上的一片文章，也给大家分享一下，非常牛逼。亲自测试在最新的Vanilla Chromium OS下完美Flash和PDF

安装方法：



  1. 启动Chromium OS.


  2. log in.


  3. 同时按下 alt+ctrl+F2.进入Console

  4. log in 的 user是: chronos 
              password是: facepunch.

  5. 输入指令: sudo su, 接着 log in 密码还是: facepunch.

  6. 接着输入: curl
-L [http://goo.gl/JL1An5](http://goo.gl/JL1An5) |
bash

  7. 这样就搞定了，是不是很easy，程序会自动搞定回到登陆界面。

音频修复，有些电脑可能会遇到这些问题。然后就是试用Linux下不同的音频驱动，试试别的驱动是不是适用于你的声卡(there's a
change in the new builds, for me audio was working so i don't know
what to do if it doesn't. you can try to restart your audio driver
with alsaucm or alsactl):

  1. 启动 Chromium OS.

  2. log in.

  3. 同时按住 alt+ctrl+F2进入Console

  4. log in 的 user: chronos 密码password:
facepunch.

  5. 输入: sudo su, 接着登陆密码password:
facepunch.

  6. 输入命令: mount -o remount, rw /

  7. 接着输入: alsaconf, and press enter till
you come back to the terminal.

  8.然后是: mount -o remount, r /

  9.最后: reboot.


输入命令之后会重启系统，音频应该能搞定。

最近看到的中文教程相对比较少，希望能帮组到大家。如果密码不是facepunch就试试password









