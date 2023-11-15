---
title: vue中video绑定的值发生了改变页面video标签并未刷新的解决方案
date: 2022-01-21 10:10:10
tags:
  - JS
categories:
  - Vue2问题
index_img: ../tnt/8.jpg
banner_img: ../tnt/8.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

**vue中video绑定的值发生了改变我们会发现页面的video标签并未刷仍然是黑屏或者显示原来的视频，改如何解决呢？**
第一步给video标签赋个唯一标识（id，ref都行）：

```js
<video controls="controls" loop="loop" id={props.id} >
                      <source src={props.content} type="video/mp4"></source>
                      <source src={props.content} type="video/ogg"></source>
                      <source src={props.content} type="video/webm"></source>
                      <object width="" height="" type="application/x-shockwave-flash" data="myvideo.swf">
                        <param name="movie" value="myvideo.swf" />
                        <param name="flashvars" value="autostart=true&amp;file=myvideo.swf" />
                      </object>
                      当前浏览器不支持 video直接播放，点击这里下载视频： <a href="myvideo.webm">下载视频</a>
                    </video>
```

第二部采用dom的方式修改其src属性：

```js
document.getElementById(message.id).src = res.data.data;
```
这样video标签就会刷新，变为你再次赋的url的视频。
