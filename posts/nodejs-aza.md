---
title: 'nodejs的安装及配置（适用于windows）'
date: 2023-01-04 16:05:47
tags: [nodejs]
published: true
hideInList: false
feature: 
isTop: false
---
# 一、下载安装
本教程演示的环境：win 11 64位

首先进入[nodejs](https://nodejs.org/en/)官网，或者直接点击[nodejs](https://nodejs.org/dist/v20.10.0/node-v20.10.0-x64.msi/)的进行下载（2023.12.27日），优先选择稳定版本，根据自己电脑系统配置进行下载适合的安装包

![](https://cdn.shimail.cn/nodejs%E7%9A%84%E5%AE%89%E8%A3%85%E5%8F%8A%E9%85%8D%E7%BD%AE%EF%BC%88%E9%80%82%E7%94%A8%E4%BA%8Ewindows%EF%BC%89/1.png)
# 二、安装步骤
1.傻瓜式安装即可（一直点击下一步 手动狗头😄）
2.可以点击change按钮，安装到自己想要的位置（不修改默认位置也是可以的）。我安装到了X盘

# 三、验证是否安装成功
win + r 打开运行框，输入cmd，进入终端，然后输入node -v 和 npm -v ，如果出现版本号就是安装成功了。如图：
![](https://cdn.shimail.cn/nodejs%E7%9A%84%E5%AE%89%E8%A3%85%E5%8F%8A%E9%85%8D%E7%BD%AE%EF%BC%88%E9%80%82%E7%94%A8%E4%BA%8Ewindows%EF%BC%89/2.png)

![](https://cdn.shimail.cn/nodejs%E7%9A%84%E5%AE%89%E8%A3%85%E5%8F%8A%E9%85%8D%E7%BD%AE%EF%BC%88%E9%80%82%E7%94%A8%E4%BA%8Ewindows%EF%BC%89/3.png)
# 四、nodejs配置环境
修改全局模块下载路径
在nodejs根目录内新建两个文件夹 node_global 和 node_cache 如图：
![](https://cdn.shimail.cn/nodejs%E7%9A%84%E5%AE%89%E8%A3%85%E5%8F%8A%E9%85%8D%E7%BD%AE%EF%BC%88%E9%80%82%E7%94%A8%E4%BA%8Ewindows%EF%BC%89/4.png)

创建完两个空文件夹之后，跟之前操作一样，在键盘按下【win+R】键，输入cmd，然后回车，进入终端，输入下面命令，然后回车即可。

说明：

管理员身份- 打开CMD，配置路径：（注意一定要管理员身份运行CMD！！！路径改成你自己的路径，不要无脑复制！！！）

prefix = 创建的node_global文件夹所在路径

cache = 创建的node_cache文件夹所在路径

-------------------------------------------------------------------------------
```shell
npm config set prefix "X:\nodejs\node_global"
npm config set cache "X:\nodejs\node_cache"
```

配置环境变量
我的电脑”-右键-“属性”-“高级系统设置”-“高级”-“环境变量”

进入环境变量对话框，在【系统变量】下新建【NODE_PATH】，

输入【X:\nodejs\node_global】，并且在path路径中新增【X:\nodejs\】和【X:\nodejs\node_modules】
![](https://cdn.shimail.cn/nodejs%E7%9A%84%E5%AE%89%E8%A3%85%E5%8F%8A%E9%85%8D%E7%BD%AE%EF%BC%88%E9%80%82%E7%94%A8%E4%BA%8Ewindows%EF%BC%89/5.png)
![](https://cdn.shimail.cn/nodejs%E7%9A%84%E5%AE%89%E8%A3%85%E5%8F%8A%E9%85%8D%E7%BD%AE%EF%BC%88%E9%80%82%E7%94%A8%E4%BA%8Ewindows%EF%BC%89/6.png)

将【用户变量】下的【Path】新增【X:\nodejs\node_global】和【X:\nodejs\node_global\node_modules】
![](https://cdn.shimail.cn/nodejs%E7%9A%84%E5%AE%89%E8%A3%85%E5%8F%8A%E9%85%8D%E7%BD%AE%EF%BC%88%E9%80%82%E7%94%A8%E4%BA%8Ewindows%EF%BC%89/7.png)

# 五、测试
1.全局安装最常用的 express 模块 进行测试
命令如下:
```shell
npm install express -g
```

成功结果如下：
![](https://cdn.shimail.cn/nodejs%E7%9A%84%E5%AE%89%E8%A3%85%E5%8F%8A%E9%85%8D%E7%BD%AE%EF%BC%88%E9%80%82%E7%94%A8%E4%BA%8Ewindows%EF%BC%89/8.png)

2.注：若执行命令npm install express -g 出现如下报错
![](https://cdn.shimail.cn/nodejs%E7%9A%84%E5%AE%89%E8%A3%85%E5%8F%8A%E9%85%8D%E7%BD%AE%EF%BC%88%E9%80%82%E7%94%A8%E4%BA%8Ewindows%EF%BC%89/9.png)
是由于权限的原因，右击Nodejs文件夹->属性->安全，点击编辑，将所有权限都✔即可。

建议全部用户都改成完全控制权限，别忘点应用，再点确认。
![](https://cdn.shimail.cn/nodejs%E7%9A%84%E5%AE%89%E8%A3%85%E5%8F%8A%E9%85%8D%E7%BD%AE%EF%BC%88%E9%80%82%E7%94%A8%E4%BA%8Ewindows%EF%BC%89/10.png)

# 六、更换npm源为淘宝镜像
因为npm默认下载服务器为国外，速度慢；故更换为国内淘宝镜源。

注意一定要管理员身份运行CMD！！！
```shell
npm config set registry https://registry.npm.taobao.org
```

# 安装 cpm （按需安装）
```shell
npm install -g cnpm
```

我们也可以通过cnpm -v 来查看是否安装成功。

安装后就可以使用cnpm安装模块了。

切换回国外镜源
```shell
npm config set registry https://registry.npmjs.org
```

查看当前镜源
```shell
npm config get registry
```

nodejs的环境配置就到此结束了，因为当时自己也没少踩坑，所以借此交流
结束，完结撒花😊