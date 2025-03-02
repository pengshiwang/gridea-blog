---
title: '随机小姐姐短视频'
date: 2025-01-07 00:00:00
tags: [api]
published: true
hideInList: false
feature: 
isTop: false
---
请根据实际情况进行修改，以保证视频框大小合适，仅用于学习参考！

<!--more-->

[源码演示站](https://www.pppp.host/xjj)
### 一、简介
本模板是一款简洁而美观的HTML页面，专为看小姐姐而设计。

### 二、使用步骤
将本HTML源码复制后，在主机空间或服务器内根目录创建一个index.html打开index.html文件进行编辑。
根据个人需求，修改页面中的内容、样式、文本信息等。

### 三、功能特点
简洁美观，页面设计简洁

### 代码
```html
<html>
<head>
<meta charset="UTF-8">
<style>
#switch,#next1{
background: #7F9CCC;
color:#fff;
line-height:40px;
text-align:center;
width:100px;
border:none;
margin:0 6px;
border-radius:6px;
font-weight:bold;
}
</style>
</head>
<body>
<section id="main">
<video id="player" src="https://dwz.mk/MVZVjy" controls="controls" width="100%" height="500px"></video>
</section>
<div style="text-align: center;">
<section id="buttons">
<button id="switch">连续: 开</button><button id="next1">换一个</button>
</section>
</div>


 
<script>
(function (window, document) {
if (top != self) {
window.top.location.replace(self.location.href);
}
var get = function (id) {
return document.getElementById(id);
}
var bind = function (element, event, callback) {
return element.addEventListener(event, callback);
}
var auto = true;
var player = get('player');
var randomm = function () {
player.src = 'http://v.nrzj.vip/video.php?_t=' + Math.random();
player.play();
}
bind(get('next1'), 'click', randomm);
bind(player, 'error', function () {
randomm();
});
bind(get('switch'), 'click', function () {
auto = !auto;
this.innerText = '连续: ' + (auto ? '开' : '关');
});
bind(player, 'ended', function () {
if (auto) randomm();
});
})(window, document);</script>
<script>var _hmt = _hmt || [];(function() {var hm = document.createElement("script");hm.src = "";var s = document.getElementsByTagName("script")[0]; s.parentNode.insertBefore(hm, s);})();</script>

</body>
</html>
```