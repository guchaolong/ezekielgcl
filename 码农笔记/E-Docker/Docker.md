
```bash
service docker start    //启动docker
```

# 相关文章
[Docker 入门终极指南，别再说不会用Docker了！](https://mp.weixin.qq.com/s/9LHd9FTdaiZqwUOuyIafpg)


# 虚拟化技术、容器技术
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688737869114-8043231d-2b58-476e-8fef-5027058ddbd5.png#averageHue=%23e3e7e4&clientId=u621ddacf-f4cb-4&from=paste&height=634&id=u2e937b83&originHeight=743&originWidth=917&originalType=binary&ratio=2&rotation=0&showTitle=false&size=336487&status=done&style=none&taskId=u38c1fb1c-71ab-4be4-980f-8094978f234&title=&width=782.5)

虚拟机本身也是有局限性的，每一个虚拟机都是一个完整的操作系统，要分配系统资源，虚拟机多到一定程度时，操作系统本身资源也就消耗殆尽，或者说必须扩容

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688738805339-8412f459-f27d-4b9d-8bcf-95c691b97b29.png#averageHue=%23f7eceb&clientId=u621ddacf-f4cb-4&from=paste&height=406&id=ue739a417&originHeight=811&originWidth=1476&originalType=binary&ratio=2&rotation=0&showTitle=false&size=416957&status=done&style=none&taskId=u9ad2dc27-ea4b-454c-a63f-6b33e757ea3&title=&width=738)


虚拟化的目标都是一台完整的计算机，拥有底层的物理硬件、操作系统和应用程序执行的完整环境。
为了让虚拟机中的程序实现像在真实物理机器上运行“近似”的效果，背后的HyperVisor做了大量的工作，付出了“沉重”的代价。
虽然HyperVisor做了这么多，但你有没有问过虚拟机中的程序，这是它想要的吗？或许HyperVisor给的太多，而目标程序却说了一句：你其实可以不用这样辛苦。
确实存在这样的情况，虚拟机中的程序说：我只是想要一个单独的执行执行环境，不需要你费那么大劲去虚拟出一个完整的计算机来。
这样做的好处是什么？
虚拟出一台计算机的成本高还是只虚拟出一个隔离的程序运行环境的成本高？答案很明显是前者。一台物理机可能同时虚拟出10台虚拟机就已经开始感到乏力了，但同时虚拟出100个虚拟的执行环境却还是能够从容应对，这对于资源的充分利用可是有巨大的好处。
近几年大火的容器技术正是在这样的指导思想下诞生的。
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688739215333-4bf5868d-1a91-47cb-82e9-5b9750a41866.png#averageHue=%2340777e&clientId=u621ddacf-f4cb-4&from=paste&id=u6aacc943&originHeight=283&originWidth=730&originalType=url&ratio=2&rotation=0&showTitle=false&size=110954&status=done&style=none&taskId=ub5c65839-692b-4110-970e-b0532e8a013&title=)
不同于虚拟化技术要完整虚拟化一台计算机，容器技术更像是操作系统层面的虚拟化，它只需要虚拟出一个操作系统环境。

在原生操作系统上隔离出一个单独的空间，将应用程序置于其中运行，这个空间的形态上类似于一个容器将应用程序包含在其中，故取名容器技术

容器技术的好处是轻量，所有隔离空间的程序代码指令不需要翻译转换，就可以直接在CPU上执行，大家底层都是同一个操作系统，通过软件层面上的逻辑隔离形成一个个单独的空间

# 
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688739764277-b4f5eeae-7ec3-4321-ac03-b71ad3f6f821.png#averageHue=%23f1f1f1&clientId=u621ddacf-f4cb-4&from=paste&height=152&id=uf5f4630c&originHeight=198&originWidth=983&originalType=binary&ratio=2&rotation=0&showTitle=false&size=105874&status=done&style=none&taskId=u1d329b04-2f86-4648-99fd-6e70241a801&title=&width=755.5)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688739981636-24650206-fd07-4fa6-b04c-aa99eaa5b6a9.png#averageHue=%23fcf9f9&clientId=u621ddacf-f4cb-4&from=paste&height=384&id=u1d8fd809&originHeight=767&originWidth=1251&originalType=binary&ratio=2&rotation=0&showTitle=false&size=261755&status=done&style=none&taskId=u948cf26b-8e0b-46d0-bfe9-6550e243cb6&title=&width=625.5)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688740610631-b03eda20-c6ef-43a6-8ae3-c858d8b4c53d.png#averageHue=%23fcfafa&clientId=u621ddacf-f4cb-4&from=paste&height=297&id=ue8338298&originHeight=593&originWidth=1724&originalType=binary&ratio=2&rotation=0&showTitle=false&size=321074&status=done&style=none&taskId=u90dbcff3-3b0d-453e-9cdd-28cc7fe4d1a&title=&width=862)


![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688740165235-a9091353-c062-4885-889d-84e90efa8436.png#averageHue=%23f1f2ef&clientId=u621ddacf-f4cb-4&from=paste&height=742&id=ue99a84cf&originHeight=708&originWidth=966&originalType=binary&ratio=2&rotation=0&showTitle=false&size=652266&status=done&style=none&taskId=u4f39aaa8-5b5b-4811-a83b-2c65972ab55&title=&width=1012)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688740226407-ae6e7306-ffaa-47c4-b969-3a152f1560b8.png#averageHue=%23dee1de&clientId=u621ddacf-f4cb-4&from=paste&height=385&id=u7b5918f3&originHeight=500&originWidth=950&originalType=binary&ratio=2&rotation=0&showTitle=false&size=549883&status=done&style=none&taskId=uf8d8b955-2ed4-4856-9411-893d8ad56f0&title=&width=731)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688740466979-aad9e665-4cd2-40a0-9d36-ae0c6113f8ba.png#averageHue=%23fefefc&clientId=u621ddacf-f4cb-4&from=paste&height=155&id=u8e7e693d&originHeight=309&originWidth=1189&originalType=binary&ratio=2&rotation=0&showTitle=false&size=199972&status=done&style=none&taskId=u4d7ef4a5-7281-45ba-ba67-7c84be3df9f&title=&width=594.5)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688740511311-ff6fdc03-4e2e-40d4-9d35-592ae55b13b1.png#averageHue=%23f3f3f3&clientId=u621ddacf-f4cb-4&from=paste&height=399&id=u5c7fa6cd&originHeight=797&originWidth=1245&originalType=binary&ratio=2&rotation=0&showTitle=false&size=318752&status=done&style=none&taskId=ud8e828e9-e4ff-4284-8435-d8c10212010&title=&width=622.5)![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688740649535-b9e89dbe-c29a-4f15-bd81-8efb726f1f08.png#averageHue=%23f1f1f1&clientId=u621ddacf-f4cb-4&from=paste&height=248&id=u48afba46&originHeight=496&originWidth=1221&originalType=binary&ratio=2&rotation=0&showTitle=false&size=216572&status=done&style=none&taskId=u97f5e4a2-6b5d-4541-8f99-f5e9dfeefa1&title=&width=610.5)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688741345677-5a1b4c63-a3ea-498e-a9f4-59c0238f4722.png#averageHue=%23f3f3f3&clientId=u621ddacf-f4cb-4&from=paste&height=136&id=ua1fc99ba&originHeight=271&originWidth=1009&originalType=binary&ratio=2&rotation=0&showTitle=false&size=97108&status=done&style=none&taskId=u32967e0c-2802-4474-ac5a-c2e2bb1a0e8&title=&width=504.5)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688740737828-5570d51c-171e-46cf-8e48-0c64adfcc213.png#averageHue=%23fafafa&clientId=u621ddacf-f4cb-4&from=paste&height=435&id=udee3ef3e&originHeight=657&originWidth=952&originalType=binary&ratio=2&rotation=0&showTitle=false&size=301559&status=done&style=none&taskId=u9673d375-f443-40f0-9f7b-3fd8197a8e3&title=&width=631)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688740987327-7a0983a7-0f57-4805-bae1-7e57f7d4b725.png#averageHue=%23f8f8f8&clientId=u621ddacf-f4cb-4&from=paste&height=652&id=u62bf68e4&originHeight=897&originWidth=888&originalType=binary&ratio=2&rotation=0&showTitle=false&size=313228&status=done&style=none&taskId=u4b5e9486-f2f4-4c92-b44e-8cf80ff387a&title=&width=645)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688741378404-bff68bf1-bdf1-4033-baa9-aaab4ba1553b.png#averageHue=%23f5f5f5&clientId=u621ddacf-f4cb-4&from=paste&height=340&id=u8680bf1c&originHeight=425&originWidth=760&originalType=binary&ratio=2&rotation=0&showTitle=false&size=113822&status=done&style=none&taskId=u8519cfd0-0d56-4a52-816d-a66f82f7ba0&title=&width=608)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688741404366-0f6ba306-480d-4587-abf8-50e9976aa6bb.png#averageHue=%23f8f8f8&clientId=u621ddacf-f4cb-4&from=paste&height=348&id=uc391a573&originHeight=612&originWidth=1112&originalType=binary&ratio=2&rotation=0&showTitle=false&size=147584&status=done&style=none&taskId=u8e65b635-d940-4d3d-851f-3035eeb24d2&title=&width=632)




# doker简介
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688746360076-29c3bd07-be07-4063-8dce-aef5759dcd8b.png#averageHue=%23277d9c&clientId=u621ddacf-f4cb-4&from=paste&height=655&id=u35a070f5&originHeight=577&originWidth=651&originalType=binary&ratio=2&rotation=0&showTitle=false&size=120572&status=done&style=none&taskId=uee216e83-9720-40a9-a7a6-03d3a875d69&title=&width=739.5)
docker可以将应用程序和它运行时所需要的各种依赖包，第三方软件库，配置文件等打包在一起，以便在任何环境中都能正确的运行

# 为什么要用 docker
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688746608403-a7247935-eaf6-4452-8bac-1f55ee757644.png#averageHue=%23126fbd&clientId=u621ddacf-f4cb-4&from=paste&height=317&id=u85eb9593&originHeight=633&originWidth=1805&originalType=binary&ratio=2&rotation=0&showTitle=false&size=471256&status=done&style=none&taskId=u8e4540bb-4b8e-4bfc-bc5f-6e2573204f5&title=&width=902.5)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688746669221-4eba4b62-b966-4fea-9251-6d7d37392694.png#averageHue=%231076bc&clientId=u621ddacf-f4cb-4&from=paste&height=304&id=u533779c4&originHeight=607&originWidth=1763&originalType=binary&ratio=2&rotation=0&showTitle=false&size=218258&status=done&style=none&taskId=uec61a0fa-02a0-4a7d-90b3-15f21be9bc4&title=&width=881.5)

# Docker和虚拟机的区别
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688746804466-055f3cc0-7865-499a-8cf2-3fb5181042d3.png#averageHue=%231977be&clientId=u621ddacf-f4cb-4&from=paste&height=371&id=u4da36bc6&originHeight=741&originWidth=1724&originalType=binary&ratio=2&rotation=0&showTitle=false&size=289700&status=done&style=none&taskId=u2b870a32-9b0f-4e60-b9a6-bab592f28d7&title=&width=862)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688747224432-ae1bdd07-4282-4fbe-94a7-847cbfbab8ae.png#averageHue=%231473bd&clientId=u621ddacf-f4cb-4&from=paste&height=279&id=uff174cab&originHeight=558&originWidth=1733&originalType=binary&ratio=2&rotation=0&showTitle=false&size=364501&status=done&style=none&taskId=u9a222de5-53f7-4fec-9e3c-75f77f2b217&title=&width=866.5)

docker和容器是两个不同的概念，Docker是容器的一种实现，是一个容器化的解决方案和平台，而容器是一种虚拟化技术，和虚拟机类似，也是一个独立的环境，可以在这个环境中运行应用程序，和虚拟机不同的是它并不需要在容器中运行一个完整的操作系统，而是使用宿主机的操作系统，所以启动速度非常快，通常只需要几秒钟，同时，因为需要的资源更少，可以在一台物理服务器上运行更多的容器，减少资源的闲置和浪费，比如一台物理服务器上可能只能运行几个虚拟机，但却可以运行上百个容器


# 基本原理和概念
镜像是一个只读的模板，他可以用来创建容器，容器是doker 的运行实例，它提供了一个独立的可移植环境，可以在这个环境中运行应用程序
镜像和容器的关系，就像 Java类和实例的关系
镜像就是一个模版，我们可以根据这个模版创建多个实例，即容器，实例可以有 1 个也可以有多个
仓库，就是用来存储镜像的地方

docker 采用 CS架构模式，docker client和 docker daemon之间通过Socket 或者 RESTful API进行通信
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688748373461-0eeb05ce-6419-4ca7-99a8-b49e8058c829.png#averageHue=%239bfdca&clientId=u15850ca0-de8c-4&from=paste&height=376&id=uee173b25&originHeight=751&originWidth=1693&originalType=binary&ratio=2&rotation=0&showTitle=false&size=235022&status=done&style=none&taskId=u1658dc04-3bd9-4459-804b-e21c44844d6&title=&width=846.5)

# docker 生命周期
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688752223139-1cf56bba-fd5b-4747-946a-7fe80d060f54.png#averageHue=%23e5dfdf&clientId=u15850ca0-de8c-4&from=paste&height=409&id=ud244fc60&originHeight=818&originWidth=1306&originalType=binary&ratio=2&rotation=0&showTitle=false&size=761541&status=done&style=none&taskId=u74afe46b-56a5-40dc-a894-5f1e3e8c719&title=&width=653)

# 安装
安装，启动，然后查看版本
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688748543030-3198df56-7cad-46ce-bbfb-d7def521250d.png#averageHue=%230b1d24&clientId=u15850ca0-de8c-4&from=paste&height=724&id=uc20e867e&originHeight=553&originWidth=535&originalType=binary&ratio=2&rotation=0&showTitle=false&size=77577&status=done&style=none&taskId=u2875ec73-8384-4363-8512-02f7e60e0de&title=&width=700.5)

# 容器化和 Dockerfile
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688748971548-141f513c-c608-4a0a-a6db-df9d8a390675.png#averageHue=%233780bf&clientId=u15850ca0-de8c-4&from=paste&height=390&id=u91260ed5&originHeight=779&originWidth=1618&originalType=binary&ratio=2&rotation=0&showTitle=false&size=252307&status=done&style=none&taskId=ue1d44238-f4e0-460d-8bca-21654796ecb&title=&width=809)

# Volumes 逻辑卷
逻辑卷是 Docker 中用来存储数据的，docker容器有一个特点，就是容器中的数据是不会持久化的，当我们创建一个容器的时候，它通常以一个干净的文件系统开始，容器启动之后，我们可以在容器中创建、修改文件，但是当容器停止之后，容器中的所有数据都会丢失，如果想要持久化容器中的数据，就是逻辑卷的所做的，他可以把容器中的目录或者指定路径映射到宿主机的某一个目录或者位置上，这样就可以将数据保存到宿主机的磁盘上 ，实现了数据的持久化


# Docker Compose
是 docker官方开源的项目，是一个
用于定义和运行多容器 Docker应用程序的工具
使用 yaml 文件来配置应用程序的服务
一条命令即可创建并启动所有服务

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688750599221-2db1289c-86d7-4de4-b235-00248455cbe4.png#averageHue=%2336679b&clientId=u15850ca0-de8c-4&from=paste&height=418&id=u924a5474&originHeight=836&originWidth=1711&originalType=binary&ratio=2&rotation=0&showTitle=false&size=312847&status=done&style=none&taskId=uc75d628e-81d1-442b-95a0-75ad8c70e01&title=&width=855.5)
比如，搭建一个网站需要多个服务，比如前端后端数据库等，这些服务都是独立的，但是他们之间又是有关联的， 需要相互配合来工作，前端需要连接后端，后端需要连接数据库 ，这些服务之间的关联关系就是 Docker Compose要解决的问题，它通过一个单独的 docker-compose.yaml的配置文件，来将这一组相互关联的容器组合在一起，形成一个项目，然后使用一条命令`docker compose up`就可以启动 停止或者重建这些服务

# docker命令
![DockerCheatSheet-ByGeekHour.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688758721004-92cbf7c4-68ba-4027-b3d0-aa99dc3b1841.png#averageHue=%23d6dace&clientId=u15850ca0-de8c-4&from=ui&id=u9e30037d&originHeight=6220&originWidth=6590&originalType=binary&ratio=2&rotation=0&showTitle=false&size=4006862&status=done&style=none&taskId=ub9a10f8a-91ec-4df6-851c-647e97c70fd&title=)
