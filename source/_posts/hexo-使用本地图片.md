---
title: hexo-使用本地图片
date: 2020-07-16 10:25:38
tags:
---
# 前言
我的第一篇博文{% post_link hexo-尝试使用（初始化、部署篇） %}是先发布到简书上再转过来hexo的，其中的图片是在简书服务器上的，转过来发现，在个人网站打不开图片报403。应该是简书做了图片防盗链，其实网上有方法避开防盗链，参考[【建站教程】网站引用三方图片遇到简单防盗链referer的处理办法](https://blog.csdn.net/xia296/article/details/85246761)。但为了学习hexo，本文使用图片放到本站的方法。
<!--more-->

---

# 官方方案 参考[Hexo-资源文件夹](https://hexo.io/zh-cn/docs/asset-folders)
## 一. 最简单的实现
资源（Asset）代表 source 文件夹中除了文章以外的所有文件，例如图片、CSS、JS 文件等。比方说，如果你的Hexo项目中只有少量图片，那最简单的方法就是将它们放在 source/images 文件夹中。然后通过类似于 `![](/images/image.jpg)` 的方法访问它们。

## 二. 想要有规律的使用静态资源
对于那些想要更有规律地提供图片和其他资源以及想要将他们的资源分布在各个文章上的人来说，Hexo也提供了更组织化的方式来管理资源。这个稍微有些复杂但是管理资源非常方便的功能可以通过将 `config.yml` 文件中的 `post_asset_folder` 选项设为 `true` 来打开。
``` cmd
_config.yml
post_asset_folder: true
```
当资源文件管理功能打开后，Hexo将会在你每一次通过 `hexo new [layout] <title>` 命令创建新文章时自动创建一个文件夹。这个资源文件夹将会有与这个文章文件一样的名字。将所有与你的文章有关的资源放在这个关联文件夹中之后，你可以通过相对路径来引用它们，这样你就得到了一个更简单而且方便得多的工作流。

## 三. 相对路径引用
当你打开文章资源文件夹功能后，你把一个 example.jpg 图片放在了你的资源文件夹中，如果通过使用相对路径的常规 markdown 语法 ![](/example.jpg) ，它将 不会 出现在首页上。（但是它会在文章中按你期待的方式工作）

正确的引用图片方式是使用下列的[标签插件](https://hexo.io/zh-cn/docs/tag-plugins)而不是 markdown ：
```
{% asset_img example.jpg This is an example image %}
```

## 四. 注意：
*1. 本地调试时，添加完新图片时，可能需要先执行下hexo generate。才能在/public目录下生成图片*


---

# 我的方案
结合上面的第二种方案 + 图片绝对路径。<br>
当执行hexo generate时，命令行中会把新添加的图片处理后的绝对路径展示出来，如下面的`INFO  Generated: 2020/07/08/hexo-写文章-写作篇/01.webp`
``` cmd
INFO  Start processing
INFO  Files loaded in 174 ms
INFO  Generated: 2020/07/08/hexo-写文章-写作篇/01.webp
INFO  1 files generated in 116 ms
```
在md中用`![创建新页面](/2020/07/08/hexo-写文章-写作篇/01.webp)` 这种md语法来引入。就能在文章详情页和首页都能看到图片了。*图片路径记得 `/` 开头*