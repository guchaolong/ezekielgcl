
## Catalina结构

catalina负责管理Server

Server表示整个服务器

Server下面有多个服务Service

每个Service都包含着多个连接器组件Connector（Coyote实现）和一个容器组件Container组件

Tomcat启动的时候，就是初始化一个Catalina实例

![](https://cdn.nlark.com/yuque/0/2020/png/663445/1606378556027-2bf6ab04-44f6-4803-97e8-8929a01e233c.png)







或者

![](https://cdn.nlark.com/yuque/0/2020/png/663445/1606379073652-0dcdc38b-6ef2-4f27-8f1a-e7546c979b54.png)

  




  

## Container结构

Tomcat设计了4种容器，分别是Engine、Host、Context、Wrapper

这4种容器不是平行关系，而是父子关系

![](https://cdn.nlark.com/yuque/0/2020/png/663445/1606379441478-b6ab09e3-6c8a-4eb8-b179-16375d066228.png)