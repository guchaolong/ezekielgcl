
#nginx

# docker安装 nginx 并挂载

`docker search nginx`
`docker pull nginx`
`docker images`

创建 nginx 容器
`docker run -d --name nginx -p 8080:80 nginx`
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230920180410.png)
>参数说明：
--name 为容器起一个名字
-p 8080:80： 端口进行映射，格式为`宿主机端口:容器端口`，将本地 8080 端口映射到容器内部的 80 端口。  
-d 表示容器在后台运行
最后第一个字段为 image 名称


验证：
http://localhost:8080/
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230920183804.png)

上面我们通过将<mark style="background: #FF5582A6;">本地8080端口</mark>映射到docker<mark style="background: #FF5582A6;">容器的80端口</mark>上实现了nginx的访问。

首先明确的是容器中的文件内容是可以被修改的，但是**一旦容器重启，所有写入到容器中的，针对数据文件、配置文件的修改都将丢失**。所以为了保存容器的运行状态，执行结果，我们需要将容器内的一些重要的数据文件、日志文件、配置文件映射到宿主机上

>docker拉取下来的nginx配置文件路径一般情况下是：  
日志文件位置：/var/log/nginx  
配置文件位置: /etc/nginx  
资源存放的位置: /usr/share/nginx/html


创建本地挂载目录：
`mkdir -p ./DockerData/nginx/{conf,log,html}

把 nginx 容器中的文件进行复制
```shell
#nginx.conf复制到主机
docker cp nginx:/etc/nginx/nginx.conf /Users/ezekiel/DockerData/nginx/conf/nginx.conf

#conf.d文件夹复制到主机
docker cp nginx:/etc/nginx/conf.d /Users/ezekiel/DockerData/nginx/conf/conf.d

#html目录复制到主机
docker cp nginx:/usr/share/nginx/html /Users/ezekiel/DockerData/nginx
```

复制后，如图所示
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230920181250.png)


停止刚刚创建的 nginx 容器，然后删除
`docker stop 4dbbe9638e18`
`docker rm 4dbbe9638e18`

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230920182554.png)


重新创建容器
```shell
docker run -d --name nginx -p 8080:80 \
> -v /Users/ezekiel/DockerData/nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
> -v /Users/ezekiel/DockerData/nginx/conf/conf.d:/etc/nginx/conf.d \
> -v /Users/ezekiel/DockerData/nginx/log:/var/log/nginx \
> -v /Users/ezekiel/DockerData/nginx/html:/usr/share/nginx/html \
> --privileged=true nginx
```
>参数说明：
>四个-v依次：
>挂载主配置文件"nginx.conf"
>挂载docker内子配置文件的路径
>挂载ngixn日志，把ngixn日志放到挂载到的目录下
>挂载项目位置
>

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230920183210.png)


查看挂载情况：
`docker inspect nginx | grep Mounts -A 200`
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230920185132.png)


docker进入 nginx 容器
`docker exec -it nginx bash`

退出容器：输入`exit`

在客户端也可以操作，很方便