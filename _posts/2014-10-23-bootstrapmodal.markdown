---
author: kresnikwang
comments: true
date: 2014-10-23 03:40:14+00:00
layout: post
slug: bootstrapmodal
title: bootstrap里面的modal example
wordpress_id: 53
categories:
- Tech
tags:
- bootstrap
- css3
- javascript
---

github里面一个关于bootstrap创建modal的例子
先修改bootstap.css让它风格化

```css
    
    body.modal-open, 
    .modal-open .navbar-fixed-top, 
    .modal-open .navbar-fixed-bottom {
      margin-right: 0;
    }
    
    .modal {
      left: 50%;
      bottom: auto;
      right: auto;
      padding: 0;
      width: 500px;
      margin-left: -250px;
      background-color: #ffffff;
      border: 1px solid #999999;
      border: 1px solid rgba(0, 0, 0, 0.2);
      border-radius: 6px;
      -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
      box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
      background-clip: padding-box;
    }
    
    .modal.container {
      max-width: none;
    }
    
```


正文
    ```
    <div data-focus-on="input:first" tabindex="-1" id="stack1" class="modal hide fade">
      <div class="modal-header">
        <button data-dismiss="modal" type="button" class="close" aria-hidden="true">×</button>
        <h3>Stack One</h3>
      </div>
      <div class="modal-body">
        One fine body…
        One fine body…
        One fine body…
        <input data-tabindex="1" type="text">
        <input data-tabindex="2" type="text">
        <button data-toggle="modal" href="#stack2" class="btn">Launch modal</button>
      </div>
      <div class="modal-footer">
        <button data-dismiss="modal" type="button" class="btn">Close</button>
        <button type="button" class="btn btn-primary">Ok</button>
      </div>
    </div>
     
    <div data-focus-on="input:first" tabindex="-1" id="stack2" class="modal hide fade">
      <div class="modal-header">
        <button data-dismiss="modal" type="button" class="close" aria-hidden="true">×</button>
        <h3>Stack Two</h3>
      </div>
      <div class="modal-body">
        One fine body…
        One fine body…
        <input data-tabindex="1" type="text">
        <input data-tabindex="2" type="text">
        <button data-toggle="modal" href="#stack3" class="btn">Launch modal</button>
      </div>
      <div class="modal-footer">
        <button data-dismiss="modal" type="button" class="btn">Close</button>
        <button type="button" class="btn btn-primary">Ok</button>
      </div>
    </div>
     
    <div data-focus-on="input:first" tabindex="-1" id="stack3" class="modal hide fade">
      <div class="modal-header">
        <button data-dismiss="modal" type="button" class="close" aria-hidden="true">×</button>
        <h3>Stack Three</h3>
      </div>
      <div class="modal-body">
        One fine body…
        <input data-tabindex="1" type="text">
        <input data-tabindex="2" type="text">
      </div>
      <div class="modal-footer">
        <button data-dismiss="modal" type="button" class="btn">Close</button>
        <button type="button" class="btn btn-primary">Ok</button>
      </div>
    </div>
    
    ```
