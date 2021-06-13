## 前言

下文中贴的代码段，均为默认配置项，且只贴相关的部分。

其中 `${user.home}` 表示用户目录，Windows 下表示 `C:\Users\用户名`，Linux 中对于 root 用户，在 `/root/` 路径下，对于其他用户，在 `/home/用户名/` 路径下。


## 启动端口

```yml
server:
  port: 8080
```

## 路径相关

### 日志路径

```yml
zfile:
  log:
    path: ${user.home}/.zfile/logs
```

### 数据库文件路径

```yml
zfile:
  db:
    path: ${user.home}/.zfile/db/zfile
```

### 临时文件路径

系统运行过程中，可能会产生一些临时文件，如解析音频文件的歌手和封面时，会先下载音频到服务器，解析后会自动删除，此文件的下载临时路径为如下: 

```yml
zfile:
  tmp:
    path: ${user.home}/.zfile/tmp
```

## 缓存相关

### 缓存自动刷新时间间隔

缓存自动刷新任务间隔时间，每隔多长时间检测一次到期的缓存 KEY 并自动刷新，单位为秒。

```yml
zfile:
  cache:
    auto-refresh:
      interval: 1
```

### 缓存过期时间

目录缓存过期时间 和 下载地址过期时间(需存储策略支持)，单位为秒。

```yml
zfile:
  cache:
    timeout: 1800
```

## 文档文件名称

系统会自动识别文件名为此名称的文件，取其内容作为文档，显示在文件列表下方。

```yml
zfile:
  constant:
    readme: readme.md
```

## 密码文件名称

系统会自动识别文件名为此名称的文件，取其内容作为文件夹密码，可修改此文件的文件名，以防被恶意获取密码文件。

```yml
zfile:
  constant:
    password: password.txt
```

## 解析的音频文件大小限制

播放音频文件时，会自动解析音频文件的歌手和封面，此配置用于限制支持最大的文件大小，默认为 `5 MB`。

```yml
zfile:
  preview:
      audio:
          maxFileSizeMb: 5
```

## 在线浏览文本文件大小限制

在线预览文件文件，如 `md`, `txt`, `html`, `java`, `js`, `php` 等文件时，此配置用于限制支持最大的文件大小，默认为 `512 KB`。

```yml
zfile:
  preview:
      text:
          maxFileSizeKb: 512
```

## DEBUG 模式

开启 debug 模式后：

1. 可以访问 `http(s)://ip:port/h2-console` ，使用内置的 h2 数据库控制台来维护数据库。
2. 可以访问 `http(s)://ip:port/debug/resetPwd`，会将用户名强制重置为 admin，密码修改为 123456。

!> 在配置文件 application.yml 中 zfile -> debug 修改。


## 自定义直链前缀

默认直链前缀为 `directlink`, 如 https://zfile.jun6.net/directlink/2/ZFile.md ，可自定义修改为其他值，**但修改之前的直链将无法访问**。

```yml
zfile:
  directLinkPrefix: directlink
```
