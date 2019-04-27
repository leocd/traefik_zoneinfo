# traefik_zoneinfo

traefik官方镜像缺少time包依赖的zoneinfo.zip。

在使用Let's Encrypt功能时会被触发，触发现象:

```
open /usr/local/go/lib/time/zoneinfo.zip: no such file or directory

```

解决方案：

- 1.构建自定义镜像，添加依赖

```
FROM traefik:latest
COPY zoneinfo.zip /usr/local/go/lib/time/zoneinfo.zip
```

- 2.挂载volume

参见：[使用traefik作为kubernetes ingress controller并开启letsencrypt证书认证](https://blog.fanfengqiang.com/2019/04/27/%E4%BD%BF%E7%94%A8traefik%E4%BD%9C%E4%B8%BAkubernetes-ingress-controller%E5%B9%B6%E5%BC%80%E5%90%AFletsencrypt%E8%AF%81%E4%B9%A6%E8%AE%A4%E8%AF%81/)

自定义镜像位置：[fanfengqiang/traefik](https://hub.docker.com/r/fanfengqiang/traefik)
