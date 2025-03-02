---
title: 'Handsome主题美化！'
date: 2025-01-08 11:05:13
tags: [typecho,handsome]
published: true
hideInList: false
feature: 
isTop: false
---
本文主要描写对于typecho框架Handsome主题进行简单美化的教程!

<!--more-->


## 1.Handsome主题时光机圆形头像

自定义CSS自定义CSS丨放入后台-外观设置-开发者设置-自定义CSS
```css
/* 时光机圆形头像 */
.img-square {border-radius: 50%;}
.list-group-item .thumb-sm .img-square {border-radius: 5px;}
```
## 2.Handsome主题文章标题居中

自定义CSS自定义CSS丨放入后台-外观设置-开发者设置-自定义CSS
```css
/*文章标题居中*/
.panel h2{
    text-align: center; 
}
.panel-small h2{
    text-align: center; 
}
.panel-picture h3{
    text-align: center; 
}
.post-item-foot-icon{
    text-align: center;
}
```
## 3.Handsome主题首页新年倒计时

将以下代码添加至后台-开发者设置-首页列表最前方广告位。
```html
/*首页倒计时*/
<style> 
.gn_box{     border: none;     border-radius: 15px; } 
.gn_box {     padding: 10px 14px;     margin: 10px;     margin-bottom: 20px;     text-align: center;     background-color: #fff; } 
#t_d{     color: #982585;     font-size: 18px; } 
#t_h{     color: #8f79c1;     font-size: 18px; } 
#t_m{     color: #65b4b5;     font-size: 18px; } 
#t_s{     color: #83caa3;     font-size: 18px; } 
</style> 
<div class="gn_box">   
<h1><font color=#E80017>2</font><font color=#D1002E>0</font><font color=#BA0045>2</font><font color=#A3005C>5</font><font  color=#8C0073>年</font><font color=#75008A>-</font>
<font color=#5E00A1>新</font><font color=#4700B8>年</font><font color=#3000CF>倒</font><font color=#1900E6>计</font><font color=#0200FD>时</font></h1><center>
<div id="CountMsg" class="HotDate"><span id="t_d"> 天</span><span id="t_h"> 时</span><span id="t_m"> 分</span><span id="t_s"> 秒</span></div></center>
<script type="text/javascript"> 
function getRTime() {   
    var EndTime = new Date('2021/01/29 00:00:00');  
    var NowTime = new Date();  
    var t = EndTime.getTime() - NowTime.getTime();   
    var d = Math.floor(t / 1000 / 60 / 60 / 24);   
    var h = Math.floor(t / 1000 / 60 / 60 % 24);   
    var m = Math.floor(t / 1000 / 60 % 60);   
    var s = Math.floor(t / 1000 % 60); 
    var day = document.getElementById("t_d");
    if (day != null) {
        day.innerHTML = d + " 天";   
    }
    var hour = document.getElementById("t_h");
    if (hour != null) {
        hour.innerHTML = h + " 时";  
    }
    var min = document.getElementById("t_m");
    if (min != null) {
        min.innerHTML = m + " 分";   
    }
    var sec = document.getElementById("t_s");
    if (sec != null) {
        sec.innerHTML = s + " 秒";
    }
}   
setInterval(getRTime, 1000);   
</script> </div>
```
## 4.handsome主题博客信息添加访客数量和网站响应耗时

首先将以下代码加到themes/handsome/libs/Content.php中放在class Content{}之前
```php
/*访问总量*/
function theAllViews(){
$db = Typecho_Db::get();
$row = $db->fetchAll('SELECT SUM(VIEWS) FROM `typecho_contents`');
echo number_format($row[0]['SUM(VIEWS)']);
}
/*响应时间*/
function timer_start() {
global $timestart;
$mtime = explode( ' ', microtime()  );
$timestart = $mtime[1] + $mtime[0];
return true; 
}
timer_start();
function timer_stop( $display = 0, $precision = 3  ) {
global $timestart, $timeend;
$mtime = explode( ' ', microtime()  );
$timeend = $mtime[1] + $mtime[0];
$timetotal = number_format( $timeend - $timestart, $precision  );
$r = $timetotal < 1 ? $timetotal * 1000 . " ms" : $timetotal . " s";
if ( $display  ) {
echo $r;
}
return $r;
}
```
然后在/usr/themes/handsome/component/sidebar.php文件内，找到博客信息下面添加以下代码
```php
<li class="list-group-item text-second"> <span class="blog-info-icons"> <i data-feather="users"></i></span>
<span class="badge
pull-right"><?php echo theAllViews();?></span><?php _me("访客总数") ?></li>
<li class="list-group-item text-second"> <span class="blog-info-icons"> <i data-feather="refresh-ccw"></i></span>
<span class="badge
pull-right"><?php echo timer_stop();?></span><?php _me("响应时间") ?></li>
```