---
title: hexo-命令
date: 2020-07-16 10:08:52
categories:
- 程序
- Hexo
tags:
- Hexo
- 博客搭建
---
# hexo 使用到的命令整理

<!--more-->
## npm 命令整理
`npm install hexo-cli -g` 安装/更新 hexo
`npm i` 创建完项目后安装依赖
`npm install hexo-deployer-git --save` 安装部署到github的插件

## hexo 命令
`hexo -v` 查看hexo版本
`hexo init my-blog` 初始化创建项目，‘my-blog’ 随意写
`hexo s` 本地运行预发布环境
`hexo d -g` 远程部署到仓库
`hexo new <title>` 创建新文章，&lt;title&gt; 替换为文章标题