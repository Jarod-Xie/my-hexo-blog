---
title: hexo-尝试使用（初始化、部署篇）
date: 2020-07-08 17:31:19
updated: 2020-07-08 20:10:00
commonts: true
categories:
- 程序
- Hexo
tags:
- Hexo
- 博客搭建
---
# 前言
突然想整一个个人博客试试。在网上看到说hexo好上手，并且很久以前发自己往电脑上装过hexo，所以就拿这个试试。
<!--more-->
# 安装
因为电脑上已经有了，就不写怎么安装了。就是node+npm
# 更新hexo
首先面临的问题，就是升级hexo。毕竟是两年前安装的版本，还是先升级到最新的好。
1. 查看现有版本
```
PS D:\hexo> hexo -v
hexo-cli: 1.0.3
os: Windows_NT 10.0.18362 win32 x64
node: 14.4.0
v8: 8.1.307.31-node.33
uv: 1.37.0
zlib: 1.2.11
brotli: 1.0.7
ares: 1.16.0
modules: 83
nghttp2: 1.41.0
napi: 6
llhttp: 2.0.4
openssl: 1.1.1g
cldr: 37.0
icu: 67.1
tz: 2019c
unicode: 13.0
```
可以看到是比较老的版本了。目前的最新版本已经是3.1.0了。更新！

2. 更新 
重新安装就是更新，在任意目录执行 `npm install hexo-cli -g`
结果
```
PS D:\hexo> npm install hexo-cli -g
D:\nodejs\npmglobal\hexo -> D:\nodejs\npmglobal\node_modules\hexo-cli\bin\hexo
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.3 (node_modules\hexo-cli\node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.3: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

+ hexo-cli@3.1.0
added 31 packages from 16 contributors, removed 54 packages and updated 38 packages in 27.984s
```
接下来就放心大胆的使用了。
# 使用
1. 新建个目录，并在目录下初始化项目`hexo init my-blog`。初始化比较慢，可能是因为要从github克隆代码的原因......
```
PS D:\hexo> hexo init my-blog
INFO  Cloning hexo-starter https://github.com/hexojs/hexo-starter.git
Cloning into 'D:\hexo\my-blog'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 168 (delta 0), reused 0 (delta 0), pack-reused 165                                                        Receiving objects:  39% (66/168), 28.01 KiB | 4.00 KiB/s
Receiving objects: 100% (168/168), 32.45 KiB | 6.00 KiB/s, done.
Resolving deltas: 100% (79/79), done.
Submodule 'themes/landscape' (https://github.com/hexojs/hexo-theme-landscape.git) registered for path 'themes/landscape'
Cloning into 'D:/hexo/my-blog/themes/landscape'...
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 1071 (delta 1), reused 5 (delta 1), pack-reused 1063
Receiving objects: 100% (1071/1071), 3.22 MiB | 10.00 KiB/s, done.
Resolving deltas: 100% (586/586), done.
Submodule path 'themes/landscape': checked out '73a23c51f8487cfcd7c6deec96ccc7543960d350'
[32mINFO [39m Install dependencies

> ejs@2.7.4 postinstall D:\hexo\my-blog\node_modules\ejs
> node ./postinstall.js

Thank you for installing EJS: built with the Jake JavaScript build tool (https://jakejs.com/)

npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.3 (node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.3: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

added 252 packages from 448 contributors in 50.328s

5 packages are looking for funding
  run `npm fund` for details

INFO  Start blogging with Hexo!
```
2. 安装依赖。
```
cd my-blog
npm i
```
```
PS D:\hexo> cd .\my-blog\
PS D:\hexo\my-blog> npm i
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.3 (node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.3: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

up to date in 4.23s

5 packages are looking for funding
  run `npm fund` for details
```
初始化完成~

3. 运行本地环境`hexo s`
```
PS D:\hexo\my-blog> hexo s
(node:4152) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(Use `node --trace-warnings ...` to show where the warning was created)
(node:4152) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:4152) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
(node:4152) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(node:4152) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:4152) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
```
在浏览器中打开本地地址：http://localhost:4000。就成功看到了默认的博客了！

# 部署到github上

github 有基于仓库生成静态网站的功能。
1. 创建仓库 获取网址
![创建.PNG](https://upload-images.jianshu.io/upload_images/17173792-b875c25b62eff03d.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
创建时要注意：
仓库名有固定格式：**账户名.github.io**。**Initialize this repository with a README要勾选上**。
创建成功后，在仓库设置中有一个GitHub Pages设置，展示出来了一个链接，这个链接就是能够访问仓库中的网站的网址了。
![查看网址.PNG](https://upload-images.jianshu.io/upload_images/17173792-75e2a101300c41d4.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2. 配置Deployment
在博客项目的根目录有个_config.yml配置文件，修改里面的deploy配置，如下：
```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: git@github.com:Jarod-Xie/Jarod-Xie.github.io.git
  branch: master
```
3. 安装github部署插件
部署到git需要`hexo-deployer-git`这个插件。在根目录执行：`npm install hexo-deployer-git --save`
4. 部署至仓库
执行远程部署命令`hexo d -g`, 执行完毕后，打开 **1. 创建仓库 获取网址** 这一步中拿到的网址，就能看到博客部署成功了。
![默认博客](https://upload-images.jianshu.io/upload_images/17173792-15ffcff3f665f03e.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 回顾一下命令
`hexo -v` 查看hexo版本
`npm install hexo-cli -g` 安装/更新 hexo
`hexo init my-blog` 初始化创建项目，‘my-blog’ 随意写
`npm i` 创建完项目后安装依赖
`hexo s` 本地运行预发布环境
`npm install hexo-deployer-git --save` 安装部署到github的插件
`hexo d -g` 远程部署到仓库