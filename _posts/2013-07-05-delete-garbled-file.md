---
layout: post
title: "linux下删除文件名乱码的文件"
description: ""
category: skill
tags: [problem]
---
{% include JB/setup %}

>1. ls -i 列出文件的节点ID, 如: 123456789 
>2. find ./ -inum 123456789 -print -exec rm -rf {} \;   

批量删除: 

<pre class="prettyprint linenums">
for n in 123456789 987654321;do find . -inum $n -exec rm -f {} \;;done 
</pre>
