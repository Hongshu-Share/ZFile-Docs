## OneDrive 相关 CF 加速 :id=onedrive-cf

OneDrive SharePoint 国际版, 世纪互联版等，使用 CF 加速功能。

### 登陆/注册账号

https://dash.cloudflare.com/sign-up

### 配置 Cloudflare Workers

#### 初次使用入口

初次注册会显示如下页面:

![image.png](https://cdn.jun6.net/2021/04/10/c53465c6da270.png)

![image.png](https://cdn.jun6.net/2021/04/10/71bacabf1450a.png)

![image.png](https://cdn.jun6.net/2021/04/10/d20cebcea8f67.png)

![image.png](https://cdn.jun6.net/2021/04/10/6cef8b026b14c.png)

激活后，按照下方 `非初次使用入口` 继续操作。

#### 非初次使用入口

![image.png](https://cdn.jun6.net/2021/04/10/5915cf2b4af8e.png)

![image.png](https://cdn.jun6.net/2021/04/10/cb7c1157f7334.png)

![image.png](https://cdn.jun6.net/2021/04/10/79d49c9b2ddf6.png)

```javascript
addEventListener("fetch",event => {
    let url = new URL(event.request.url);
    url.hostname ="youdomain.com";

    let request = new Request(url,event.request);
    event.respondWith(
        fetch(request,{
            headers:{
                'Referer':'https://youdomain.com/',
                'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36'
            }
        })
    )
});
```

### 添加到 ZFILE

![image.png](https://cdn.jun6.net/2021/04/10/770eefe082c2e.png)

### 注意事项

!> 使用 CF 后下载速度不一定比原来快，这个自行测试，且因为技术原因，反代后无法使用多线程下载。
