---
title: 'typecho博客评论添加IP属地的方法'
date: 2024-07-21 16:19:10
tags: [ip]
published: true
hideInList: false
feature: 
isTop: false
---
最近各大网站都添加了IP属地，本站也介绍一下如果给评论区添加显示IP属地的方法：

<!-- more -->

1，将此代码放入主题的functions.php文件中，可插入在最尾部，也可插入在中间，不知道为什么我插入最尾部，上传到虚拟主机后，用文件管理器打开却看不到，handsome主题是放在functions_mine.php文件中。 [获取评论者地址.txt](https://ltmltm.cn/usr/uploads/2022/05/2033970592.txt)

![图1][1]

2，下载QQWry.Dat放在网站根目录，注意是网站根目录！由于我博客主题是在子目录bk下，所以我把这个文件放到bk根目录下，下载地址：[qqwry.zip](http://pan.ltmltm.cn/f/1643564-582791972-a2277d)

3，打开主题评论模板comments.php文件，在您想显示的位置加上如下代码：<?php echo convertip($comments->ip); ?> handsome主题是添加在大约82-84行位置如下图：

![图2][2]

4，Typecho配置CDN后获取访客真实IP地址可能会受到影响，请在Typecho站点根目录里的config.inc.php添加下面这段代码即可。有的虚拟主机会自带CDN，所以哪怕没有配置CDN，只要不能正常显示，也可以尝试插入以下代码。

```php
//绕过 CDN 代理IP获取客户真实IP地址
if(isset($_SERVER['HTTP_X_FORWARDED_FOR']))
{
$list = explode(',',$_SERVER['HTTP_X_FORWARDED_FOR']);
$_SERVER['REMOTE_ADDR'] = $list[0];
}
```
![皓月星际转载][3]

本文转载自：网吧备忘录[博客评论添加IP属地的方法][4]


  [1]: https://cdn.shimail.cn/tp/2024-7-21-1.png
  [2]: https://cdn.shimail.cn/tp/2024-7-21-2.png
  [3]: https://ltmltm.cn/usr/uploads/2022/05/3789054717.png
  [4]: https://ltmltm.cn/4878.html