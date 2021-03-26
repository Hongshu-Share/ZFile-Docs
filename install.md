
## Linux

此处的命令中都默认安装到用户目录下: `~`。

对于 `root` 用户, 在 `/root/` 路径下, 对于其他用户, 在 `/home/用户名/` 路径下。

如需更改安装路径, 请自行修改。

### 安装依赖

!> 如为更新程序, 则可跳过此步骤, 但要执行命令, 停止服务并清理上个版本的程序:  `~/zfile/bin/stop.sh && rm -rf ~/zfile`  (不会删除数据文件)

```bash
# CentOS系统
yum install -y java-1.8.0-openjdk unzip

# Debian/Ubuntu系统
apt update
apt install -y openjdk-8-jre-headless unzip
```

### 下载项目

```bash
wget -P ~ https://c.jun6.net/ZFILE/zfile-release.war
cd ~
mkdir zfile && unzip zfile-release.war -d zfile && rm -rf zfile-release.war
chmod +x ~/zfile/bin/*.sh
```

### 常用命令

```bash
 ~/zfile/bin/start.sh       # 启动项目
 ~/zfile/bin/stop.sh        # 停止项目
 ~/zfile/bin/restart.sh     # 重启项目
```

### 更新项目

#### 删除旧版本

```bash
~/zfile/bin/stop.sh && rm -rf ~/zfile
```

#### 安装新版本
```bash
wget -P ~ https://c.jun6.net/ZFILE/zfile-release.war
cd ~
mkdir zfile && unzip zfile-release.war -d zfile && rm -rf zfile-release.war
chmod +x ~/zfile/bin/*.sh
```

## Windows

### 安装依赖

安装 JDK8, 并配置环境变量, 可参考: https://jingyan.baidu.com/article/ce09321b85e8d62bff858f93.html

### 下载项目

下载文件 https://c.jun6.net/ZFILE/zfile-release.jar

### 启动项目

然后在文件所在路径下, 使用 `cmd` 执行命令 (不支持 `powershell`):

```bash
java -Dfile.encoding=utf-8 -jar -Dserver.port=8080 .\zfile-release.jar
```

> 如需要修改配置文件, 可去 Github 复制一份配置文件, 放到 `jar` 文件同路径即可.
