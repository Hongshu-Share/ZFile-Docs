## ZFile

![https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square](https://img.shields.io/badge/license-MIT-blue.svg?longCache=true&style=flat-square)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/70b793267f7941d58cbd93f50c9a8e0a)](https://www.codacy.com/manual/zhaojun1998/zfile?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=zhaojun1998/zfile&amp;utm_campaign=Badge_Grade)
![https://img.shields.io/badge/springboot-2.0.6-orange.svg?style=flat-square](https://img.shields.io/badge/springboot-2.0.6-yellow.svg?longCache=true&style=popout-square)
![GitHub tag (latest SemVer)](https://img.shields.io/github/tag/zhaojun1998/zfile.svg?style=flat-square)

此项目是一个在线文件目录的程序, 支持各种对象存储和本地存储, 使用定位是个人放常用工具下载, 或做公共的文件库. 不会向多账户方向开发.

前端基于 [h5ai](https://larsjung.de/h5ai/) 的原有功能使用 Vue 重新开发、后端采用 SpringBoot, 数据库采用内嵌数据库.

预览地址: [https://zfile.jun6.net](https://zfile.jun6.net)

文档地址: [http://docs.zhaojun.im/zfile](http://docs.zhaojun.im/zfile)

## 系统特色

* Docker 支持
* 文件数据库 (免安装)
* 直链功能
* 图片模式
* 文件夹密码
* 忽略文件夹
* 自定义 JS, CSS
* 自定义目录的 readme 说明文件
* 支持在线浏览文本文件, 视频, 图片, 音乐. (支持 FLV 和 HLS)
* 文件/目录二维码
* 同时挂载多个存储策略
* 缓存动态开启, ~~缓存自动刷新 (v2.2 及以前版本支持)~~
* ~~全局搜索 (v2.2 及以前版本支持)~~
* 支持 S3 协议, 阿里云 OSS, FTP, 华为云 OBS, 本地存储, MINIO, OneDrive 国际/家庭/个人版/世纪互联版/SharePoint, , 七牛云 KODO, 腾讯云 COS, 又拍云 USS.

## 源码地址

项目源码 : [https://github.com/zhaojun1998/zfile/](https://github.com/zhaojun1998/zfile/)

前端源码 : [https://github.com/zhaojun1998/zfile-vue/](https://github.com/zhaojun1998/zfile-vue/)

文档源码 : [https://github.com/zhaojun1998/zfile-docs/](https://github.com/zhaojun1998/zfile-docs/)

## 系统预览

#### 前台首页
![前台首页](https://cdn.jun6.net/2021/03/23/c1f4631ee2de4.png)
#### 图片预览
![图片预览](https://cdn.jun6.net/2021/03/23/713741d43b939.png)
#### 视频预览
![视频预览](https://cdn.jun6.net/2021/03/23/9c724383bb506.png)
#### 文本预览
![文本预览](https://cdn.jun6.net/2021/03/23/b00efdfb4892e.png)
#### 音频预览
![音频预览](https://cdn.jun6.net/2021/03/23/d15b14378d3f0.png)
#### 后台设置-驱动器列表
![后台设置-驱动器列表](https://cdn.jun6.net/2021/03/23/b4f76f20ea73a.png)
#### 后台设置-新增驱动器
![后台设置-新增驱动器](https://cdn.jun6.net/2021/03/23/e70e04f8cc5b6.png)
#### 后台设置-站点设置
![后台设置-站点设置](https://cdn.jun6.net/2021/03/23/fd946991bb6b9.png)
