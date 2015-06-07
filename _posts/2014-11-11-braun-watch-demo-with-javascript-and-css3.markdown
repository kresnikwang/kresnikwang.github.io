---
author: kresnikwang
comments: true
date: 2014-11-11 07:29:31+00:00
layout: post
slug: braun-watch-demo-with-javascript-and-css3
title: JS and CSS3 Braun Watch(Clock) Demo|js时钟手表效果（含日期）
wordpress_id: 146
categories:
- Works
- Tech
tags:
- css3
- Html5
- javascript
---

Demo: [http://kresnik.co/demo/watchdemo/braunwatch.html](http://kresnik.co/demo/watchdemo/braunwatch.html)

Github: [https://github.com/kresnikwang/Braunwatch.git](https://github.com/kresnikwang/Braunwatch.git)

I like this watch so much. So today I tried to rebuild it using Javascript and CSS3. Wish you like it. Pure CSS and no jQuery required. _It's not advertisement_, So I didn't put any logo in to this demo. Thank you!

Using javascript to move 3 pointer and indicate the current date. Using CSS3 to make the appear right under different browers.

我用JS 和 CSS3 来写的这个时钟demo然后嵌套到手表里面进行设计。尽量把这个设计做的跟我的手表设计贴合。

Here is a Photo of this Braun Watch.

[![71uknFTfBdL._UY550_](http://kresnik.co/wp-content/uploads/2014/11/71uknFTfBdL.-UY550--192x300.jpg)](http://kresnik.co/wp-content/uploads/2014/11/71uknFTfBdL.-UY550-.jpg)

Below is a screenshot of what I made

[![watchdemo](http://kresnik.co/wp-content/uploads/2014/11/watchdemo.jpg)](http://kresnik.co/wp-content/uploads/2014/11/watchdemo.jpg)

Clock Only：[http://kresnik.co/demo/watchdemo/braun_watch.html](http://kresnik.co/demo/watchdemo/braun_watch.html)

Download Link：[http://kresnik.co/demo/watchdemo/braunwatch.zip](http://kresnik.co/demo/watchdemo/braunwatch.zip)




```
    < !DOCTYPE HTML><script type="text/javascript">// < ![CDATA[
    function clock(){
        var $=function(id){return document.getElementById(id)};
        //Write into DOM
        function mark(){
            //radius
            var r=parseFloat(window.getComputedStyle?window.getComputedStyle($("clock"),null).width:$("clock").currentStyle["width"])/2;
            //DOM
            for(var i=1;i&lt;61;i++){
                $("clock-mark").innerHTML+="<b class='c"+i+"'><i></i>";
                var ci=document.getElementsByClassName("c"+i)[0];
                var cii=ci.getElementsByTagName("i")[0];
                //use Sin and Cos to set the position of Marks on the watch
                ci.style.left=r+r*(Math.sin(i*6*2*Math.PI/360))+"px";
                ci.style.top=r-r*(Math.sin((90-i*6)*2*Math.PI/360))+"px";
                //the degree
                /*other*/
                ci.style.transform="rotate("+i*6+"deg)";
                /*FF*/
                ci.style.MozTransform="rotate("+i*6+"deg)";
                /*webkit*/
                ci.style.WebkitTransform="rotate("+i*6+"deg)";
                /*opera*/
                ci.style.OTransform="rotate("+i*6+"deg)";
                /*ms*/
                ci.style.msTransform="rotate("+i*6+"deg)";
                //big mark
                if(i%5==0){
                    ci.className="c"+i+" "+"big-mark";
                    cii.innerHTML=i/5;
                    }
                //小刻度
                else{
                    ci.className="c"+i+" "+"small-mark";
                    ci.removeChild(cii);
                    }
                //rotate the numbers
                var iRotate=-i*6;
                cii.style.transform="rotate("+iRotate+"deg)";
                cii.style.MozTransform="rotate("+iRotate+"deg)";
                cii.style.WebkitTransform="rotate("+iRotate+"deg)";
                cii.style.OTransform="rotate("+iRotate+"deg)";
                cii.style.msTransform="rotate("+iRotate+"deg)";
                }
            }
        //rotation of pointer
        function turnR(){
            var d=new Date();
            var h=d.getHours();
            var m=d.getMinutes();
            var s=d.getSeconds();
            var sRadius=360/60*s;
            var mRadius=360/60*m;
            //rotate in consistant speed. var mRadius=360/60*m+360/60/60*s
            var hRadius=360/12*h+30/60*m;
            var ch=$("clock-h");
            var cm=$("clock-m");
            var cs=$("clock-s");
            /*other*/
            ch.style.transform="rotate("+hRadius+"deg)";
            cm.style.transform="rotate("+mRadius+"deg)";
            cs.style.transform="rotate("+sRadius+"deg)";
            /*FF*/
            ch.style.MozTransform="rotate("+hRadius+"deg)";
            cm.style.MozTransform="rotate("+mRadius+"deg)";
            cs.style.MozTransform="rotate("+sRadius+"deg)";
            /*webkit*/
            ch.style.WebkitTransform="rotate("+hRadius+"deg)";
            cm.style.WebkitTransform="rotate("+mRadius+"deg)";
            cs.style.WebkitTransform="rotate("+sRadius+"deg)";
            /*opera*/
            ch.style.OTransform="rotate("+hRadius+"deg)";
            cm.style.OTransform="rotate("+mRadius+"deg)";
            cs.style.OTransform="rotate("+sRadius+"deg)";
            /*ms*/
            ch.style.msTransform="rotate("+hRadius+"deg)";
            cm.style.msTransform="rotate("+mRadius+"deg)";
            cs.style.msTransform="rotate("+sRadius+"deg)";
            setTimeout(turnR,1000);
            }
        /*for the date*/
        function clockDate(){
            var d=new Date();
            $("clock-date").innerHTML=d.getDate();
            }
        //use function
        mark();
        turnR();
        clockDate();
        }
    window.onload=clock;
    // ]]></script>
```



