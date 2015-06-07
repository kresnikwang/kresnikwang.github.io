---
author: kresnikwang
comments: true
date: 2015-05-31 05:03:36+00:00
layout: post
slug: github-%e8%ae%be%e7%bd%ae%ef%bc%8c%e5%bc%ba%e5%88%b6%e4%bd%bf%e7%94%a8https-%e6%9d%a5%e4%bb%a3%e6%9b%bf-git
title: Github 设置，强制使用"https://" 来代替 "git://"
wordpress_id: 323
categories:
- Tech
tags:
- angularjs
- github
- npm
---




If you can't clone a repository with a "git://" url because of a proxy or firewall, here is a little git configuration that will force git to use "https://" even when you'll type "git://" URL.









    
    <code class="haskell"><span class="title">git</span> config <span class="comment">--global url."https://".insteadOf git://</span>
    </code>


With this command, it will add the following lines in you .gitconfig :

    
    <code class="1c">[url <span class="string">"https://"</span>]   
        insteadOf = git:<span class="comment">//</span>
    </code>


That way, you don't have to care about using "git://" or "https://" when you are cloning repo, both urls will work. Maybe a well known tweak but discovered it lately...


