

## 一键部署

经测试本镜像占用内存资源较低，运行稳定。点击下方紫色图标部署。

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/buuok/kook.git)


#### 注：失效问题
上方一键部署已失效，刚看到有朋友说heroku检测到代码违反服务协议，估计使用的人太多或被人举报仓库被heroku封了。

#### 解决方法：
a.这里建议你fork本代码后，在github里设置为私有，然后绑定你github到heroku部署使用，推荐这个。

b.或者也可以fork代码后，修改下面链接rptec为你自己账户名，通过链接部署。

https://dashboard.heroku.com/new?template=https://github.com/buuok/kook.git

免费服务，且用且珍惜。

## 设置

### 路径

`WebSocket` 路径(配置文件中的 `path` )为 `/` 。你也可以自行修改

### 端口

`端口` 为 `443` 。

### UUID

`UUID` 默认为 `10974d1a-cbd6-4b6f-db1d-38d78b3fb109` 你也可以在部署时自由修改（建议修改）。

## 流量中转

使用cloudflare的workers来`中转流量`，配置为： 

```
addEventListener(
      "fetch",event => {
         let url=new URL(event.request.url);
         url.hostname="你的heroku域名.herokuapp.com";
         let request=new Request(url,event.request);
         event. respondWith(
           fetch(request)
         )
      }
    ) 
```


