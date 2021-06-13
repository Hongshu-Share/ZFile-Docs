## Linux

### 安装依赖

```bash
# CentOS系统
yum install -y java-1.8.0-openjdk unzip

# Debian/Ubuntu系统
apt update
apt install -y openjdk-8-jre-headless unzip
```

### 下载项目

#### 安装说明

下面命令中第一行表示默认安装到用户目录下: `~/zfile` 下。

对于 `root` 用户, `~`  = `/root`,  `~/zfile` 表示在 `/root/zfile` 路径下。

对于其他用户,  `~` = `/hone/用户名` 表示在 `/home/用户名/` 路径下。如对于 `oracle` 用户,  `~/zfile` 则表示安装在 `/home/oracle/zfile` 下。

如需更改安装路径, 请自行修改，如 `export ZFILE_INSTALL_PATH=/data/zfile`，表示安装在 `/data/zfile` 路径下。

```bash
export ZFILE_INSTALL_PATH=~/zfile
mkdir -p $ZFILE_INSTALL_PATH && cd $ZFILE_INSTALL_PATH
wget https://c.jun6.net/ZFILE/zfile-release.war
unzip zfile-release.war && rm -rf zfile-release.war
chmod +x $ZFILE_INSTALL_PATH/bin/*.sh
```

### 常用命令

!> 以下为默认未修改安装路径下的情况，如修改了安装路径请自行更改命令所在路径。

```bash
 ~/zfile/bin/start.sh       # 启动项目
 ~/zfile/bin/stop.sh        # 停止项目
 ~/zfile/bin/restart.sh     # 重启项目
```

### **更新方式**

如果没修改过安装路径，则停止程序后，删除安装文件夹即可，默认命令为：

（如修改过安装路径，则替换下方命令中的 `~/zfile` 部分为你的安装路径即可）

```bash
# 停止程序
~/zfile/bin/stop.sh
# 删除安装文件夹 
rm -rf ~/zfile
```


```bash
# 重新下载安装最新版
export ZFILE_INSTALL_PATH=~/zfile
mkdir -p $ZFILE_INSTALL_PATH && cd $ZFILE_INSTALL_PATH
wget https://c.jun6.net/ZFILE/zfile-release.war
unzip zfile-release.war && rm -rf zfile-release.war
chmod +x $ZFILE_INSTALL_PATH/bin/*.sh
```

---

## Windows

### 安装依赖

安装 JDK8, 并配置环境变量, 可参考: https://jingyan.baidu.com/article/ce09321b85e8d62bff858f93.html

### 下载项目

下载文件 https://c.jun6.net/ZFILE/zfile-release.jar

### 启动项目

然后在文件所在路径下, 使用 `cmd` 执行命令 (不支持 `powershell`):

```bash
# 不可关闭命令行，关闭即停止程序，或使用 ctrl + c 命令停止程序
java -Dfile.encoding=utf-8 -jar -Dserver.port=8080 .\zfile-release.jar
```

> 如需要修改配置文件, 可去 Github 复制一份配置文件, 放到 `jar` 文件同路径即可.

### **更新方式**

重新下载文件 https://c.jun6.net/ZFILE/zfile-release.jar 后，再次启动即可。

---

## Docker


### 启动命令

镜像地址为：https://hub.docker.com/r/zhaojun1998/zfile

首次运行会自动创建数据库目录和日志文件目录，并映射到本地，分别为 `/root/zfile/db` (数据库文件) 和 `/root/zfile/logs` (日志文件). 后期迁移可直接将整个zfile目录备份恢复, 并再次执行以下命令.

```dockerfile
docker run -d --name=zfile --restart=always \
    -p 8080:8080 \
    -v /root/zfile/db:/root/.zfile/db \
    -v /root/zfile/logs:/root/.zfile/logs \
    zhaojun1998/zfile
```

### **更新方式**

**停止并删除现有 docker 容器，及删除本地镜像后**，重新执行上方命令即可。由于已经映射出数据库文件路径 `/root/zfile/db` 和日志文件路径 `/root/zfile/logs`，所以直接启动即可。 但为了保险起见还是建议启动前备份一份数据库文件到其他位置，再尝试启动，谨防数据丢失。
