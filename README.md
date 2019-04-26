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

参见：

自定义镜像位置：[fanfengqiang/traefik](https://hub.docker.com/r/fanfengqiang/traefik)