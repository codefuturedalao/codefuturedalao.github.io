---
layout:     post                    # 使用的布局（不需要改）
title:      Typora Upload Image              # 标题 
subtitle:   解决上传博客图片显示不了的问题				 #副标题
date:       2020-06-12             # 时间
author:     Jackson                      # 作者
header-img: img/verilog-chapter1-bg.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
- other


---



# Typora  使用Upload Image将图片上传到服务器上

​		之前写博客，上传后常常还需要将图片上传到我的七牛云服务器上，把图片地址变为http开头的网络地址，时间久了也就不再上传博客了，今天决定搞一搞，看到了typora上面有upload image的选项，教程可查看typora提供的文档，打开方式如下图所示。

![image-20200612203021122](http://sql.icrystal.top/img/image-20200612203021122.png)

其中有个比较详细的操作图片如下图

<img src="https://support.typora.io/media/image-upload/upload.gif" style="zoom:50%;" />

点击箭头指向的超链接，可以看到更加详细的教程。

![image-20200612203403065](http://sql.icrystal.top/img/image-20200612203403065.png)

文档全英文，看不懂没关系，现在我们逐步讲解。本机为Win10操作系统，因此看Configurarion下面的说明，我们可以选择PicGo.app、PicGo和Cusotm。

![image-20200612203714492](http://sql.icrystal.top/img/image-20200612203714492.png)

下面我们点击Typora左上角的File->Preferences->Image，可以看到如下图所示的内容，点击Image Uploader的PidGo-Core（Command Line），然后点击DownLoad Or Upload，等待下载（我网速太慢了，十几兆等了好久）。

![image-20200612203852671](http://sql.icrystal.top/img/image-20200612203852671.png)

下载好之后点击Open Config File

![image-20200612204125162](http://sql.icrystal.top/img/image-20200612204125162.png)

可以看到类似这样的图（uploader在我这里是current，这两个字段没什么区别）

![image-20200612204308097](http://sql.icrystal.top/img/image-20200612204308097.png)

下面进入到重点了，我们要修改配置文件来满足我们的需求，我直接讲解上传到七牛云的，其他的参见[官方文档](https://picgo.github.io/PicGo-Core-Doc/zh/guide/config.html#默认配置文件)，先给大家看个成品

![image-20200612204749131](http://sql.icrystal.top/img/image-20200612204749131.png)

#### 1. AccessKey和SecretKey

​		在个人中心->密钥管理

![image-20200612205039607](http://sql.icrystal.top/img/image-20200612205039607.png)

#### 2. Bucket

​		Bucket指的就是空间名称

![image-20200612205200537](http://sql.icrystal.top/img/image-20200612205200537.png)

#### 3.URL 

​		Url是和这个空间绑定的域名，记得加http://或https://

![image-20200612205254136](http://sql.icrystal.top/img/image-20200612205254136.png)

#### 4.Area

​		区域是看自己的的存储区域，华东为z0，华北为z1，可以看下图

![image-20200612205411761](http://sql.icrystal.top/img/image-20200612205411761.png)

配置到这里就完成了，保存后，点击Test Uploader

![image-20200612205533092](http://sql.icrystal.top/img/image-20200612205533092.png)

你会看到下面的图

![image-20200612205559899](http://sql.icrystal.top/img/image-20200612205559899.png)

恭喜你，配置成功，现在可以右键点击图片直接上传到自己的七牛云服务器上面了！:smile: