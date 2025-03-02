---
title: '为你的博客引入阿里Iconfont图标'
date: 2024-02-01 16:12:11
tags: [美化]
published: true
hideInList: false
feature: 
isTop: false
---
如何为Hexo博客引入阿里巴巴矢量库
<!-- more -->
## 引言

在搭建和美化个人博客时，图标资源是我们经常需要用到的元素。阿里巴巴矢量图标库因其丰富的图标种类和极高的自定义性，深受开发者喜爱。本文将详细介绍如何在你的Hexo博客中引入并使用阿里巴巴矢量图标库。
## 步骤一：获取图标链接
首先，访问[阿里巴巴矢量图标库](https://www.iconfont.cn/)，搜索并选择你需要的图标，添加到项目或者购物车，然后点击“下载至本地”。在下载后的文件夹中，你可以找到一个名为 `iconfont.css`的样式文件，这个文件包含了所有你选择图标的CSS样式代码。
## 步骤二：引入 iconfont.css
将下载的`iconfont.css`文件上传至你的`Hexo`主题的`source/css/`目录下（如果该目录不存在，请自行创建）。 在你的主题的主要CSS文件（如：`main.css`或`style.styl`等），通过`@import`语句引入`iconfont.css`：
```markdown
/* 如果是css文件 */
@import "css/iconfont.css";

/* 如果是stylus文件 */
@import "iconfont.styl";
```


确保路径正确对应你放置 iconfont.css 的位置。
## 步骤三：在文章或页面中使用图标
在HTML模板或Markdown文件中，可以使用类名来引用图标。假设你在阿里图标库中选中的图标类名为 .icon-xxx ，则在Markdown文件中插入图标的方式如下：
```html
<i class="iconfont icon-xxx"></i>
```

请将 `icon-xxx`替换为你实际使用的图标类名。
## 结语
至此，你已经成功地在你的Hexo博客中引入并使用了阿里巴巴矢量图标库。通过这种方式，你可以轻松定制博客的各个部分，丰富其视觉效果，提升用户体验。
注意：具体的引入方式可能因不同的Hexo主题而有所差异，请根据实际情况进行适当调整。同时，建议在引入第三方资源时遵循版权协议，合理合法使用。

更完整更加完美的教程，请看店长的[Iconfont Inject](https://akilar.top/posts/d2ebecef/)

