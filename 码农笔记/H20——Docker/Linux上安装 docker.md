
参考：[CentOS Docker 安装 | 菜鸟教程](https://www.runoob.com/docker/centos-docker-install.html)

有两种安装方式：采用脚本一键式安装或者手动安装，一下为手动安装方式

手动安装Docker分三步：卸载、设置仓库、安装。

# 卸载旧版本

为了防止旧版本的docker影响。我们需要先卸载干净
```bash
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

# 设置源仓库

在设置仓库之前，需先安装所需的软件包yum-utils
`sudo yum install -y yum-utils`

yum-utils提供了yum-config-manager，将仓库设置为官方源地址
`sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo`

>通常，官方的源地址比较慢，可将上述的源地址替换为国内比较快的地址：
>阿里云：https://download.docker.com/linux/centos/docker-ce.repo
>清华大学：https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/centos/docker-ce.repo

仓库设置完毕，即可进行Docker的安装。

# 安装 Docker Engine-Community
安装docker engine和docker-compose。 执行命令：
`sudo yum -y install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`

验证：
`docker -v` 
`docker compose version`


启动docker
`sudo systemctl start docker`


# 卸载 docker

删除安装包：
`yum remove docker-ce`

删除镜像、容器、配置文件等内容：
`rm -rf /var/lib/docker`




