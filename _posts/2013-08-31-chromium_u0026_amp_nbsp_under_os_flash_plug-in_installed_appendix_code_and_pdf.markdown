---
author: kresnikwang
comments: true
date: 2013-08-31 01:08:40+00:00
layout: post
slug: chromium_u0026_amp_nbsp_under_os_flash_plug-in_installed_appendix_code_and_pdf
title: Chromium OS下Flash和Pdf插件安装附录代码
wordpress_id: 23
categories:
- Tech
tags:
- Chromium OS
---
附录一下代码，希望能有童鞋有用
```
#!/bin/bash
#based on
https://gist.github.com/3065781 which is based on
https://wiki.archlinux.org/index.php/Chromium
 
#mounting the
filesystem as writable
mount -o remount, rw /
cd
/opt/
 
echo
“Downloading
important data”
wget –no-check-certificate -O “data.tar” “https://googledrive.com/host/0B78S5hOqFxkOOGpDSHp4YWt0REU/addons.tar”
 
echo
“extracting the
very important data!”
tar -xf data.tar
 
mkdir -p /usr/lib/mozilla/plugins/
 
#Flash,
pdf
 
#mp3,mp4, stopped
working…
cp /opt/data/libffmpegsumo.so /usr/lib/cromo/ -f
cp /opt/data/libffmpegsumo.so /usr/lib/mozilla/plugins/ -f
 
#pdf
cp /opt/data/libpdf.so /opt/google/chrome/ -f
 
#flash
cp /opt/data/libpepflashplayer.so /opt/google/chrome/pepper/
-f
cp /opt/data/manifest.json /opt/google/chrome/pepper/ -f
cp /opt/data/pepper-flash.info /opt/google/chrome/pepper/ -f
 
echo
“deleting
downloaded crap”
rm -rf /opt/data/
rm /opt/data.tar
restart ui
```