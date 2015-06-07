---
author: kresnikwang
comments: true
date: 2014-10-28 07:31:55+00:00
layout: post
slug: let-browser-support-html5
title: Browser Support HTML5 让现有浏览器支持HTML5
wordpress_id: 65
categories:
- Tech
tags:
- Html5
---

用js在对网页里面没有的元素进行创建，然后就能支持html5元素了


    
    
   ```
    <script language="JavaScript">
    (function(){ 
       if(!/*@cc_on!@*/0) return; 
       var e = "abbr,article,aside,audio,bb,canvas,datagrid,datalist,details,dialog, eventsource,figure,footer,hgroup,header,mark,menu,meter,nav,output,progress,section,time,video".split(','),i=0,length=e.length; 
       while(i<length ){ 
            document.createElement(e[i++]) 
       } 
    })();
    </script>
    ```
