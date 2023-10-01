#Redis 
# redis单机部署

单机部署就十分简单了，只需要下面几个命令即可：

  
```
#默认拉取一个最新的redis镜像
docker pull redis

#在默认的6379端口上启动一个redis服务
docker run --name test-redis -p 6379:6379 -d redis

#进入容器内部
docker exec -it test-redis /bin/bash

# 启动一个redis客户端来连接redis
redis-cli

#进入之后安装惯例 ping一下即可
ping
```

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202310011609519.png)



