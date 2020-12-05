---
layout: post
title: "Typora+picGo+Gitee管理图床"
date: 2020-12-04
description: "Typora+picGo+Gitee管理图床配置详解"
tag: 常用软件
---

[TOC]



# Typora+picGo+Gitee管理图床

**图床**

​	图床是一个网络上存储图片的地方，为了节约本地资源，图片可以外链，例如：如果你想写Markdown的文章时，Markdown使用的图片必须是一个链接地址，其用到的本地的图片需要上传到一个可以外链的服务器上了，也就是所说的图床

## PicGo使用（图床管理工具）

### 步骤一：安装PicGo的Gitee插件

PinGo没有自带的Gitee图床，所以需要下载相关的插件

- ​	必须先安装node.js之后才能安装插件

- 在插件设置中搜索gitee，两个都可以用，这里我选择的是第一个

  ![image-20201204121026917](https://gitee.com/happyzm/images/raw/master/image-20201204121026917.png)

### 步骤三：建立Gitee图床仓库

1. 新建仓库

![image-20201204121412814](https://gitee.com/happyzm/images/raw/master/image-20201204121412814.png)

2.选择个人设置中的私人令牌，点击生成新令牌

![下载 (1)](https://gitee.com/happyzm/images/raw/master/%E4%B8%8B%E8%BD%BD%20(1).png)



3.填写令牌描述，选择projects

![image-20201204122220030](https://gitee.com/happyzm/images/raw/master/image-20201204122220030.png)

4.复制token



### 步骤四：配置PicGo

填写owner信息，为你的gitee用户名，repo：你的图床仓库名，然后在填写token信息

![image-20201204122406564](https://gitee.com/happyzm/images/raw/master/image-20201204122406564.png)



### 步骤五：Typora设置

打开文件-偏好设置-图像，设置PicGo软件的路径

![image-20201204122620526](https://gitee.com/happyzm/images/raw/master/image-20201204122620526.png)



点击验证图片上传选项，测试是否上传成功

![image-20201204122752443](https://gitee.com/happyzm/images/raw/master/image-20201204122752443.png)





**常见错误**

1.检查端口是否被占用

2.检查gitee图床配置是否有误