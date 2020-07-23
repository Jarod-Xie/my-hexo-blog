---
title: npm 发包初体验
date: 2020-07-23 15:19:25
categories:
- 程序
- js
- npm
tags:
- npm
---

# 前言
为了更好的理解npm，第一次尝试发布npm包
<!--more-->

# 发包流程

## 一. 准备[npm](https://www.npmjs.com/)账号
新账号要记得验证后才能publish发包。

## 二. 创建并初始化项目
1. 创建项目目录：如：tool-pratice
2. 进入目录 `cd tool-pratice`
3. 执行npm init 初始化项目，一直回车就可以。
``` powershell
PS E:\develop\npm-pacages\tool-pratice> npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (tool-pratice)
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to E:\develop\npm-pacages\tool-pratice\package.json:

{
  "name": "tool-pratice",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this OK? (yes)
PS E:\develop\npm-pacages\tool-pratice>
```

- 默认字段简介：  
  - name：发布的包名，默认是上级文件夹名。不得与现在npm中的包名重复。包名不能有大写字母/空格/下滑线!  
  - version：包的版本，默认是1.0.0。对于npm包的版本号有着一系列的规则，模块的版本号采用X.Y.Z的格式，具体体现为：  
    - 1. 修复bug，小改动，增加z。  
    - 2. 增加新特性，可向后兼容，增加y  
    - 3. 有很大的改动，无法向下兼容,增加x  
  - description：项目简介  
  -mian：入口文件，默认是Index.js，可以修改成自己的文件   
  -scripts：包含各种脚本执行命令  
  -test：测试命令。  
  -author：写自己的账号名  
  -license：这个直接回车，开源文件协议吧，也可以是MIT，看需要。  

4. 在根目录创建 `index.js`，写点内容
``` javascript
!function(){
  console.log(`我的npm包的入口文件`)
}()
```

5. 在本机添加npm 账号
``` powershell
PS E:\develop\npm-pacages\tool-pratice> npm adduser
Username: **********
Password:
Password:
Email: (this IS public) ******
Logged in as ***** on https://registry.npm.taobao.org/.
PS E:\develop\npm-pacages\tool-pratice> 
```

6. npm publish 发包
``` powershell
PS E:\develop\npm-pacages\tool-pratice> npm publish                                                                     npm notice
npm notice package: tool-pratice@1.0.0
npm notice === Tarball Contents ===
npm notice 63B  index.js
npm notice 208B package.json
npm notice === Tarball Details ===
npm notice name:          tool-pratice
npm notice version:       1.0.0
npm notice package size:  349 B
npm notice unpacked size: 271 B
npm notice shasum:        5083fa312c39f194cd7d5e4e0cd4072e3a9e6451
npm notice integrity:     sha512-4PCoJu8mHqUw+[...]NrWgw4TZn0pZQ==
npm notice total files:   2
npm notice
npm ERR! code E403
npm ERR! 403 403 Forbidden - PUT https://registry.npm.taobao.org/tool-pratice - [no_perms] Private mode enable, only admin can publish this module
npm ERR! 403 In most cases, you or one of your dependencies are requesting
npm ERR! 403 a package version that is forbidden by your security policy.

npm ERR! A complete log of this run can be found in:
npm ERR!     D:\nodejs\npmcache\_logs\2020-07-23T08_01_12_463Z-debug.log
PS E:\develop\npm-pacages\tool-pratice>
```
额，第一次发包失败。网上搜了下，参考这个[发布npm包报错: 403 Forbidden - PUT https://registry.npm.taobao.org/extract - no_perms](https://blog.csdn.net/weixin_38080573/article/details/88080556)处理一下。

``` powershell
PS E:\develop\npm-pacages\tool-pratice> npm publish
npm notice
npm notice package: tool-pratice@1.0.0
npm notice === Tarball Contents ===
npm notice 63B  index.js
npm notice 208B package.json
npm notice === Tarball Details ===
npm notice name:          tool-pratice
npm notice version:       1.0.0
npm notice package size:  349 B
npm notice unpacked size: 271 B
npm notice shasum:        5083fa312c39f194cd7d5e4e0cd4072e3a9e6451
npm notice integrity:     sha512-4PCoJu8mHqUw+[...]NrWgw4TZn0pZQ==
npm notice total files:   2
npm notice
+ tool-pratice@1.0.0
PS E:\develop\npm-pacages\tool-pratice>
```
终于完成推送。去[npm](https://www.npmjs.com/) 已经可以查找到这个包了。

整个过程参考了:  
  - [一分钟教你发布npm包](https://www.jianshu.com/p/7bba18925fbf)  
  - [发布npm包报错: 403 Forbidden - PUT https://registry.npm.taobao.org/extract - no_perms](https://blog.csdn.net/weixin_38080573/article/details/88080556)

# 错误汇总

## 需要验证邮箱
``` powershell
PS E:\develop\npm-pacages\tool-pratice> npm publish
npm notice
npm notice package: tool-pratice@1.0.0
npm notice === Tarball Contents ===
npm notice 63B  index.js
npm notice 208B package.json
npm notice === Tarball Details ===
npm notice name:          tool-pratice
npm notice version:       1.0.0
npm notice package size:  349 B
npm notice unpacked size: 271 B
npm notice shasum:        5083fa312c39f194cd7d5e4e0cd4072e3a9e6451
npm notice integrity:     sha512-4PCoJu8mHqUw+[...]NrWgw4TZn0pZQ==
npm notice total files:   2
npm notice
npm ERR! code E403
npm ERR! 403 403 Forbidden - PUT http://registry.npmjs.org/tool-pratice - you must verify your email before publishing a new package: https://www.npmjs.com/email-edit
npm ERR! 403 In most cases, you or one of your dependencies are requesting
npm ERR! 403 a package version that is forbidden by your security policy.

npm ERR! A complete log of this run can be found in:
npm ERR!     D:\nodejs\npmcache\_logs\2020-07-23T08_23_14_129Z-debug.log
PS E:\develop\npm-pacages\tool-pratice> npm publish
```

## 这个是从淘宝镜像源 切到 官方镜像源后，执行npm login遇到的。
我先npm adduser 成功， 然后 npm login 就可以了。
``` powershell
PS E:\develop\npm-pacages\tool-pratice> npm login
npm ERR! code ETIMEDOUT
npm ERR! errno ETIMEDOUT
npm ERR! network request to http://registry.npmjs.org/-/v1/login failed, reason: connect ETIMEDOUT 104.16.23.35:80
npm ERR! network This is a problem related to network connectivity.
npm ERR! network In most cases you are behind a proxy or have bad network settings.
npm ERR! network
npm ERR! network If you are behind a proxy, please make sure that the
npm ERR! network 'proxy' config is set properly.  See: 'npm help config'

npm ERR! A complete log of this run can be found in:
npm ERR!     D:\nodejs\npmcache\_logs\2020-07-23T08_18_35_594Z-debug.log
PS E:\develop\npm-pacages\tool-pratice> npm adduser
```