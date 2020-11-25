---
layout: post
title: "vue-element-admin框架路由介绍"
date: 2020-11-25
description: "vue-element-admin框架路由介绍"
tag: 前端
---
# 路由和侧边栏
路由和侧边栏是绑定在一起的，只有在@/router/index.js下面配置对应的路由，侧边栏就会动态的生成

## 配置项

```javascript
// 当设置 true 的时候该路由不会在侧边栏出现 如401，login等页面，或者如一些编辑页面/edit/1
hidden: true // (默认 false)

//当设置 noRedirect 的时候该路由在面包屑导航中不可被点击
redirect: 'noRedirect'

// 当你一个路由下面的 children 声明的路由大于1个时，自动会变成嵌套的模式--如组件页面
// 只有一个时，会将那个子路由当做根路由显示在侧边栏--如引导页面
// 若你想不管路由下面的 children 声明的个数都显示你的根路由
// 你可以设置 alwaysShow: true，这样它就会忽略之前定义的规则，一直显示根路由
alwaysShow: true

name: 'router-name' // 设定路由的名字，一定要填写不然使用<keep-alive>时会出现各种问题
meta: {
  roles: ['admin', 'editor'] // 设置该路由进入的权限，支持多个权限叠加
  title: 'title' // 设置该路由在侧边栏和面包屑中展示的名字
  icon: 'svg-name' // 设置该路由的图标，支持 svg-class，也支持 el-icon-x element-ui 的 icon
  noCache: true // 如果设置为true，则不会被 <keep-alive> 缓存(默认 false)
  breadcrumb: false //  如果设置为false，则不会在breadcrumb面包屑中显示(默认 true)
  affix: true // 若果设置为true，它则会固定在tags-view中(默认 false)

  // 当路由设置了该属性，则会高亮相对应的侧边栏。
  // 这在某些场景非常有用，比如：一个文章的列表页路由为：/article/list
  // 点击文章进入文章详情页，这时候路由为/article/1，但你想在侧边栏高亮文章列表的路由，就可以进行如下设置
  activeMenu: '/article/list'
}
```

**示例：**

```javascript
  {
    path: '/',
    component: Layout,
    redirect: '/dashboard', // 重定向地址，在面包屑中点击会重定向去的地址
     hiden: true,   //不在侧边栏显示，默认为false
     alwaysShow: true,  // 一直显示根路由
     meta: { roles:['admin', 'editor'] },  // 设置跟路由权限，子路由继承权限
    children: [{
      path: 'dashboard',
      name: 'Dashboard',
      component: () => import('@/views/dashboard/index'),
      meta: { title: '首页', icon: 'dashboard' }    //title 设置路由侧边栏，面包屑显示的名字
    }]
  },
```


## 路由
两种路由： constantRoutes 和 asyncRoutes
constantRoutes ： 代表那些不需要动态判断权限的路由，如登录页，404等通用页面
asyncRoutes:  代表那些需求动态判断权限并通过addRoutes动态添加的页面


## 侧边栏
侧边栏基于element-ui的el-menu改造
侧边栏是通过读取路由并结合权限判断而动态生成的，而且还需要支持路由无线嵌套，所以使用了递归组件。侧边栏有两种形式：submenu和el-menu-item。
在sidebar中做好判断了，当你一个路由下面的children声明的路由大于1个时，自动变成嵌套的模式，如果子路由正好等于一个就会默认将子路由作为根路由显示在侧边栏中，若不想这样，可以在根路由中设置alwaysShow：true来取消这一特性

## 多级目录（嵌套路由）
如果你的路由是多级目录，如本项目 @/views/nested 那样， 有三级路由嵌套的情况下，不要忘记还要手动在二级目录的根文件下添加一个 <router-view>。


## 新增页面
首先在@/router/index.js中增加你需要添加的路由
如：新增一个example页面

```javascript
{
  path: '/example',
  component: Layout,
  redirect: '/example/export-example',
  name: 'example',
  meta: {
    title: '示例',
    icon: 'excel'
  },
    children: [
    {
      path: 'export-example',
      component: ()=>import('example/exportExample'),
      name: 'exportExample',
      meta: { title: '示例子路由1' }
    }
  ]
}
```

## 新增view
新增完路由之后要在@/views 文件夹下创建相应的文件夹，一般一个路由对应一个文件，该模块的功能组件或者方法建议在本文件夹下创建一个utils或者components文件夹，各个功能模块维护自己的utils 或者components 组件

## 新增api 
最后在@/api文件夹下创建本模块对应的api服务
