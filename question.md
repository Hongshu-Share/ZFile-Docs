## 如何更改端口

```bash
vim ~/zfile/WEB-INF/classes/application.yml
```
    
```yaml
server:
    port: 8080      # 修改此处.
```


> 默认启动端口为 8080, 如需请配置文件请编辑上述文件, 修改后重启程序生效.


## 为什么启动后无法访问

可能是防火墙没开启. 下面介绍如何防火墙开启端口. 对于阿里云、腾讯云、谷歌云等厂商, 可能还需要额外去后台开启防火墙.

### CentOS 7.x

```bash
firewall-cmd --zone=public --add-port=8080/tcp --permanent # 开放 8080 端口
firewall-cmd --reload                                      # 重启firewall
```

### Ubuntu 16.x / Debian 9.x

```bash
iptables -I INPUT -p tcp --dport 8080 -j ACCEPT
iptables-save
sudo apt-get install iptables-persistent
sudo netfilter-persistent save
sudo netfilter-persistent reload
```


### 宝塔面板

宝塔面板可以去后台开放端口:

![Snipaste_2020-01-30_18-54-42.png](http://cdn.jun6.net/2020/01/30/18fa335b407ae.png)


## 如何使用域名进行访问

方式1: 将域名 `A` 记录解析到服务器 IP, 即可通过 `域名:端口` 访问 (80 端口即可免输入端口). 

方式2: 使用 `nginx` 或 `caddy` 等工具反向代理. 以下以宝塔面板为例:

首先点击 `网站` -> `新增站点`:

![Snipaste_2020-01-30_19-00-49.png](http://cdn.jun6.net/2020/01/30/558b35c21519c.png)

点击反向代理:

![Snipaste_2020-01-30_19-01-31.png](http://cdn.jun6.net/2020/01/30/2bf2585516f8d.png)

设置反向代理:

![Snipaste_2020-01-30_19-03-21.png](http://cdn.jun6.net/2020/01/30/ac865a78a617b.png)


## 为什么提示密码错误

1. 请检查密码文件中是否包含中文，如果包含，请保持文件编码为 UTF8。
2. 请检查密码文件中是否包含空格, 换行符等不可见字符.


## 前后端分离如何部署

下载 `https://github.com/zhaojun1998/zfile/tree/master/src/main/resources/static` 路径下的所有文件, 或在程序运行后的相对路径：`WEB-INF/classes/static`.

修改 `zfile.config.json` 内文件指向后端地址, 然后放到静态资源服务器, 或对象存储即可:

```json
{
  "baseUrl": "http://xx.xxx.cn:8080"
}
```