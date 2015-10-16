---
layout: post
title: "Embed a google map"
date: 2015-10-16
comments: true
published: true
categories: 折腾
tag: 
  - Google Maps
---

## 三种途径：

- 在 Google Maps 的页面里“分享或嵌入地图”——[相应的帮助文档点这里](https://support.google.com/maps/answer/3544418?hl=zh-Hans)；

<iframe src="http://www.google.cn/maps/embed?pb=!1m18!1m12!1m3!1d436717.96616795985!2d121.1965694821956!3d31.22463250679695!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x35b27040b1f53c33%3A0x295129423c364a1!2z5LiK5rW35biC!5e0!3m2!1szh-CN!2scn!4v1444990528566" width="600" height="450" frameborder="0" style="border:0" allowfullscreen></iframe>

- Google Maps 提供的 API——[相应的帮助文档点这里](https://developers.google.com/maps/documentation/embed/)；

<iframe width="600" height="450" frameborder="0" style="border:0" src="https://www.google.com/maps/embed/v1/place?q=%E9%BB%84%E5%86%88%E5%B8%82&key=AIzaSyDisDs5_JsozIIocMK8T22Xng-G3MmyAvA" allowfullscreen></iframe>

- Google My Maps 里的“分享或嵌入地图”——[相应的帮助文档点这里](https://support.google.com/mymaps/answer/4708605?hl=zh-Hans&ref_topic=3526007&vid=1-635805994587174532-2307466006)

<iframe src="https://www.google.com/maps/d/embed?mid=zbeuMIatNXqs.kvFz7_CCyWA8" width="640" height="480"></iframe>


---

## tips

功能最基本，简单好用的就是第一种了。

第二种中比较麻烦的地方在于使用 API 需要申请一个 Key，不过嵌入地图的类型很丰富。而且为了防止 Key 被其他人使用，可以授权一个作用域`*.example.com/*`来作出限制，如果不填的话，就是任何其他人、其他网站都可以使用这个 Key 来调用 Google Maps API 了。

<del>在这里需要特别指出的就是：以我这个网站为例，我这个是搭在 Github Pages 上的博客，虽然域名是 darkkate.com 但是把作用域写为`darkkate.com/*`是无法在使用的，正确填法是`username.github.io/*`</del>

下午填`username.github.io/*`有效，晚上填`*.darkkate.com/*`才有效，过一会儿又变成填`*.darkkate.com/*`才有效，我搞不懂了。

而且其实第一种可以实现 Google Maps Embed API 的大部分功能（没仔细看，不确定是不是全部），所以感觉基本没有必要为了使用 Embed API 去搞一个 Key.

Google My Maps 自定义程度很高，还可以导入 KML, GPX 等等路线文件。

还有跟国情相关的很关键的一点，第一种是可以从 [www.google.cn/maps](http://www.google.cn/maps) 分享的，**可以在墙内显示**。