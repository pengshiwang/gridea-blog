---
title: '如何发布自己的npm包'
date: 2023-01-20 16:07:51
tags: [npm]
published: true
hideInList: false
feature: 
isTop: false
---
#### 1.首先需要注册一个 npm 的账号。访问[npm 注册页面](https://www.npmjs.com/signup/)

<!-- more -->


![](https://unpkg.com/shimail-img@1.0.0/0.1.png)

完成邮箱验证，注册完成后进入账号管理界面:头像->Account，拉倒最上方，你会看到You have not verified your email address字样的提示，点击以后按提示步骤验证你的邮箱。

![](https://unpkg.com/image-blog@1.0.1/02.png)

#### 2.在电脑上新建一个文件夹（比如image-blog）

进入文件夹

```shell
npm init
```

进行初始化

![](https://unpkg.com/image-blog@1.0.2/03.png)

最后会输出一段 package.json，请求确认，输入 yes 即可。

#### 3.然后输入发布指令，我们就可以把包发布到 npm 上了。

```shell
npm publish
```

#### 4.jsdelivr+npm 的图片引用

可以看到 Npm 只需要提供包名即可。这也是一开始要求包名不重复的原因之一

```text
【jsd出品，网宿国内节点】
https://cdn.jsdelivr.net/npm/:package@:version/:file
【unpkg 自建】
https://cdn.cbd.int/:package@:version/:file
```

当然你也可以利用[unpkg](https://unpkg.com/)自建。(UNPKG 是一个内容源自 npm 的全球快速 CDN。它部署在 cloudflare 上，在大陆地区访问到的是香港节点。所以速度也不错。)

```text
https://unpkg.com/:package@:version/:file
```

#### 5.包的更新

每次更新必须更新版本号，如1.0.0     必须向上才能发布

```shell
npm config get registry // 你的是否是npm官方的源，不是请切回
npm config set registry https://registry.npmjs.org
npm whoami // 可以查看当前登录的npm用户
npm version patch//补丁版本，最后一位数加1 
npm version minor //增加了新功能 中间的数字加1 
npm version major //大改动，不向下兼容 第一位数字加1
// 强制卸载
npm unpublish --force
```

注：大家也可以看看[鱼佬的文章](https://blog.anheyu.com/posts/72ea.html)

