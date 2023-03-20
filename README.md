# Docker container for Firefox

基于[jlesage/firefox](https://hub.docker.com/r/jlesage/firefox)的镜像，添加小米MiSans字体，支持显示中文网页。

启动命令如下
```
docker run -d --name=firefox -p 5800:5800 -v d:\\tmp\firefox:/config:rw --shm-size=512m --hostname firefox wellsen/firefox
```

如果需要指定网络可以使用如下命令
```
docker run -d --network hadoop --name=firefox --ip 172.32.3.100 -p 5800:5800 -v d:\\tmp\firefox:/config:rw --shm-size=512m --hostname firefox wellsen/firefox
```

在浏览器里打开`http://your-host-ip:5800`页面即可访问docker中的Firefox


构建Dockerfile内容如下，其中MiSans.tar.gz可以自行去小米网站[MiSans MIUI13全新系统字体](https://web.vip.miui.com/page/info/mio/mio/detail?postId=33935854)下载
```
FROM jlesage/firefox

ADD MiSans.tar.gz /usr/share/fonts/
```

具体详细使用方式请参考原始镜像[jlesage/firefox](https://hub.docker.com/r/jlesage/firefox)网页或GitHub[jlesage/docker-firefox](https://github.com/jlesage/docker-firefox)。

[jlesage/firefox](https://hub.docker.com/r/jlesage/firefox)是基于Alpine Linux构建的，关于Alpine Linux添加字体的方法请参考文档[Alpine Linux Fonts](https://wiki.alpinelinux.org/wiki/Fonts)


Reference：

[Running a Web Browser in a Docker container](https://collabnix.com/running-firefox-in-docker-container/)

[jlesage/docker-firefox](https://github.com/jlesage/docker-firefox)