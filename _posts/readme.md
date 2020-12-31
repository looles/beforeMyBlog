---
title: happyzm(looles)的hexo博客介绍
description: happyzm(looles)的hexo博客基础介绍与相关步骤
top: true
abbrlink: 8b8152ca
date: 2020-11-25 10:02:00
---

# [happyzm](https://github.com/looles/happyzm)

#### 介绍
这是一个采用 `Material Design` 和响应式设计的 Hexo 博客主题，[演示地址](http://happyzm.gitee.io)

#### 欢迎Star

如果你喜欢本博客的话，欢迎star与fork，然后根据你的信息来具体配置你的博客。

#### 下载

当你看到这里的时候，应该已经有一个自己的 [Hexo](https://hexo.io/zh-cn/) 博客了。如果还没有的话，不妨使用 Hexo 和 [Markdown](https://www.appinn.com/markdown/) 来写博客和文章。

点击 [这里](https://github.com/looles/happyzm)到你的 文件夹中即可。

当然你也可以在你的 文件夹下使用 `Git clone` 命令来下载:

```
git clone https://github.com/looles/happyzm.git
```

#### 配置

##### `站点_config.yml` 文件的其它修改建议:

- 请修改 `_config.yml` 的 `url` 的值为你的网站主 `URL`（如：`http://xxx.github.io`）。
- 建议修改两个 `per_page` 的分页条数值为 `6` 的倍数，如：`12`、`18` 等，这样文章列表在各个屏幕下都能较好的显示。
- 如果你是中文用户，则建议修改 `language` 的值为 `zh-CN`。

#### 其余配置

其余具体配置参考 [本博客]( http://happyzm.gitee.io/posts/749ffe0.html)


#### 安装教程

1.  安装Git
2.  安装Node.js
3.  安装Hexo
4.  GitHub/Gitee创建个人仓库
5.  生成SSH添加到Github或者gitee
6.  将hexo部署到github或者gitee
7.  设置个人域名
8.  发布文章

### 标题

#### 使用说明

1.  安装hexo
npm install -g hexo-cli

2.  初始化
hexo init myblog
//这个myblog 为你的博客文件名

3.  安装依赖
cd myblog    //进入文件夹下安装依赖
npm install

4. 生成静态文章
hexo g

5.  启动本地服务，开启本地调试
hexo server

6.将hexo部署到github或者gitee
打开站点配置文件_config.yml 
 deploy:
  type: git
  repo: https://github.com/YourgithubName/YourgithubName.github.io.git // 仓库地址
  branch: master
这个时候需要先安装deploy-git ，也就是部署的命令,这样你才能用命令部署到GitHub。

npm install hexo-deployer-git --save

7. 清除之前生成的文件
hexo clean

8. 生成静态文章
hexo generate

9.部署文章，更新到github或者gitee上
hexo deploy

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request




#### 
