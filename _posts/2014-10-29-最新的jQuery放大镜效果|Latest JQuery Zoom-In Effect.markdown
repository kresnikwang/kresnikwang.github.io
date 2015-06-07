---
author: kresnikwang
comments: true
date: 2014-10-29 08:05:28+00:00
layout: post
title: 最新的jQuery放大镜效果|Latest JQuery Zoom-In Effect
wordpress_id: 85
categories:
- Tech
tags:
- css3
- javascript
- jQuery
---

兼容最新的jQuery1.11

Demo：
演示地址[jquery-magnifying-glass.html](http://kresnik.co/download/jquery-magnifying-glass.html)

效果很精美，而且好处在于不用加载大小两张图片，可以一张图片搞定，载入速度也相对有所保证。
The biggest advantage is that you don't need to load 2 pictures(Normally one thumbnail and one original picture) to get the effect down. Just one clear picture and you are good to go!!!

CSS代码


    
```
/*Some CSS*/
* {margin: 0; padding: 0;}
.magnify {width: 200px; margin: 50px auto; position: relative;}

/*Lets create the magnifying glass*/
.large {
    width: 175px; height: 175px;
    position: absolute;
    border-radius: 100%;
    
    /*Multiple box shadows to achieve the glass effect*/
    box-shadow: 0 0 0 7px rgba(255, 255, 255, 0.85), 
    0 0 7px 7px rgba(0, 0, 0, 0.25), 
    inset 0 0 40px 2px rgba(0, 0, 0, 0.25);
    
    /*Lets load up the large image first*/
    background: url('http://thecodeplayer.com/uploads/media/iphone.jpg') no-repeat;
    
    /*hide the glass by default*/
    display: none;
}

/*To solve overlap bug at the edges during magnification*/
.small { display: block; }
    
```


HTML代码


    
    
```    
<div class="magnify">
    
    
    <div class="large"></div>
    
    
    <img src="http://thecodeplayer.com/uploads/media/iphone.jpg" class="small" width="200"></img>
    
</div>


<script src="http://thecodeplayer.com/uploads/js/prefixfree.js" type="text/javascript"></script>



<script src="http://thecodeplayer.com/uploads/js/jquery-1.7.1.min.js" type="text/javascript"></script>
```



JS代码


    
```    
<script>
$(document).ready(function(){

    var native_width = 0;
    var native_height = 0;

    //Now the mousemove function
    $(".magnify").mousemove(function(e){
        //When the user hovers on the image, the script will first calculate
        //the native dimensions if they don't exist. Only after the native dimensions
        //are available, the script will show the zoomed version.
        if(!native_width && !native_height)
        {
            //This will create a new image object with the same image as that in .small
            //We cannot directly get the dimensions from .small because of the 
            //width specified to 200px in the html. To get the actual dimensions we have
            //created this image object.
            var image_object = new Image();
            image_object.src = $(".small").attr("src");
            
            //This code is wrapped in the .load function which is important.
            //width and height of the object would return 0 if accessed before 
            //the image gets loaded.
            native_width = image_object.width;
            native_height = image_object.height;
        }
        else
        {
            //x/y coordinates of the mouse
            //This is the position of .magnify with respect to the document.
            var magnify_offset = $(this).offset();
            //We will deduct the positions of .magnify from the mouse positions with
            //respect to the document to get the mouse positions with respect to the 
            //container(.magnify)
            var mx = e.pageX - magnify_offset.left;
            var my = e.pageY - magnify_offset.top;
            
            //Finally the code to fade out the glass if the mouse is outside the container
            if(mx < $(this).width() && my < $(this).height() && mx > 0 && my > 0)
            {
                $(".large").fadeIn(100);
            }
            else
            {
                $(".large").fadeOut(100);
            }
            if($(".large").is(":visible"))
            {
                //The background position of .large will be changed according to the position
                //of the mouse over the .small image. So we will get the ratio of the pixel
                //under the mouse pointer with respect to the image and use that to position the 
                //large image inside the magnifying glass
                var rx = Math.round(mx/$(".small").width()*native_width - $(".large").width()/2)*-1;
                var ry = Math.round(my/$(".small").height()*native_height - $(".large").height()/2)*-1;
                var bgp = rx + "px " + ry + "px";
                
                //Time to move the magnifying glass with the mouse
                var px = mx - $(".large").width()/2;
                var py = my - $(".large").height()/2;
                //Now the glass moves with the mouse
                //The logic is to deduct half of the glass's width and height from the 
                //mouse coordinates to place it with its center at the mouse coordinates
                
                //If you hover on the image now, you should see the magnifying glass in action
                $(".large").css({left: px, top: py, backgroundPosition: bgp});
            }
        }
    })
})
</script>
```        



转载自http://thecodeplayer.com/walkthrough/magnifying-glass-for-images-using-jquery-and-css3
