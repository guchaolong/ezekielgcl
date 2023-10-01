下载镜像：
`docker pull centos:7

查看：
`docker images`

启动容器：
`docker run -itd --name centos_7 centos:7 /bin/bas`

进入容器：
`docker exec -it centos_7 /bin/bash`

