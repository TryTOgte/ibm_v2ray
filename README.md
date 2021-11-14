# 白嫖IBM套CF,github actions定时重启

## 我不仅白嫖IBM，还嫖了以下两位大哥的项目：

https://github.com/CCChieh/IBMYes

https://github.com/badafans/v2ray-cloudfoundry

嫖到骄傲。

## 使用方法：

参考上面的IBMyes项目，在ibm console运行：

```bash
$ curl -Lso- https://raw.githubusercontent.com/TryTOgte/ibm_v2ray/master/deploy.sh | bash
```

有点点差别，这个项目会生成唯一的`uuid`，避免了一群mjj用一个的尴尬境地

同时，主要还是用别人的项目不放心，特别是还有几个二进制程序，所以这里就直接从官方下载`ibmcloud`和`v2ray`了

还添加了自定义端口，注意设置1024-65535之间，不要设置太小，实际上你的程序在IBM是一普通用户权限运行的

总之来讲，你的输出会是这样：

```bash
请输入你的应用名称：liuxu-v2ray
请输入你的应用内存大小(默认256)：
请输入你需要部署的端口（范围：1024-65535，默认8080)：
应用名称：liuxu-v2ray
内存大小：256
配置完成...
初始化部署环境...
下载ibmcloud...
下载v2ray...
初始化配置...
*******************************
将这个v2ray uuid设置到你的客户端:  xxxx-xxxx-xxxx-xxxx-xxxx
*******************************
部署完成
```

如果你想使用`cloudflare`，用下面配置：

```javascript
addEventListener(
   "fetch",event => {
       let url=new URL(event.request.url);
       url.hostname="你的IBM域名:你前面设置的APP端口";
       let request=new Request(url,event.request);
       event. respondWith(
           fetch(request)
       )
   }
)
```

## 调试

在IBM cloud右上角可以点进去你`账户`的IBM控制台，系统是`ubuntu16.04`

你还可以到你的应用里面调试，我这里再白嫖一下IBMyes的图片（dog）

![img](https://github.com/CCChieh/IBMYes/raw/master/img/README/image-20200615210821081.png)

点击左边的运行时，再点击右边的SSH，就是你应用的系统了，是`ubuntu18.04`，居然比个人控制台系统新，666
