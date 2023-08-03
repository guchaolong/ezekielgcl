# 安装、配置
下载，解压，设置环境变量，在.zshrc文件中添加下面两行，然后`source ~/.zshrc`
**export GRADLE_HOME=/Users/ezekiel/DevTool/gradle-7.6**
**export PATH=$PATH:$GRADLE_HOME/bin**

**GRALE_USER_HOME** 相当于配置 Gradle 本地仓库位置和 Gradle Wrapper 缓存目录。
如果没有指定，默认是/Users/ezekiel/.gradle

是否安装成功？
`gradle -v`

# gradle项目目录结构
Gradle 项目默认目录结构和 Maven 项目的目录结构一致,都是基于约定大于配置
其完整项目目录结构如下所示：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688774060397-f05a682a-c834-49e2-bed2-300d24d56cc2.png#averageHue=%23f0f0f0&clientId=u0499adff-59f9-4&from=paste&height=368&id=u42020726&originHeight=736&originWidth=1179&originalType=binary&ratio=2&rotation=0&showTitle=false&size=220075&status=done&style=none&taskId=ua3f2fbf5-1de0-47c7-81aa-25fb0eb5f91&title=&width=589.5)
Tips:
1. 只有war工程才有webapp目录，对于普通的jar工程并没有webapp目录
2. gradlew与gradlew.bat执行的指定wrapper版本中的gradle指令,不是本地安装的gradle指令哦

# Wrapper包装器
Gradle Wrapper 实际上就是对 Gradle 的一层包装，用于解决实际开发中可能会遇到的不同的项目需要不同版本的 Gradle问题。例如：把自己的代码共享给其他人使用，可能出现如下情况:
> 1.对方电脑没有安装 gradle
> 2.对方电脑安装过 gradle， 但是版本太旧了

这时候，我们就可以考虑使用 Gradle Wrapper 了。这也是官方建议使用 Gradle Wrapper 的原因。实际上有了 Gradle Wrapper 之后，我们本地是可以不配置 Gradle 的,下载 Gradle 项目后，使用 gradle 项目自带的 wrapper 操作也是可以的。 


那如何使用 Gradle Wrapper 呢？ 
项目中的gradlew、gradlew.cmd脚本用的就是wrapper中规定的gradle版本。
而我们上面提到的gradle指令用的是本地gradle,所以gradle指令和gradlew指令所使用的gradle版本有可能是不一样的。 
gradlew、gradlew.cmd的使用方式与gradle使用方式完全一致，只不过把gradle指令换成了gradlew指令。 
当然,我们也可在终端执行 gradlew 指令时，指定指定一些参数,来控制 Wrapper 的生成，比如依赖的版本等，如下：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688774360368-f763d2c1-303e-42c1-b858-d7969ed89057.png#averageHue=%23f8f8f7&clientId=u0499adff-59f9-4&from=paste&height=126&id=ud03c193d&originHeight=148&originWidth=837&originalType=binary&ratio=2&rotation=0&showTitle=false&size=56441&status=done&style=none&taskId=u6150407f-4dd9-4224-a1fe-989477c6776&title=&width=712.5)
具体操作如下所示 ： 
`gradle wrapper --gradle-version=4.4`：升级wrapper版本号,只是修改gradle.properties中wrapper版本，未实际下载 
`gradle wrapper --gradle-version 5.2.1 --distribution-type all` :关联源码用


GradleWrapper 的执行流程：
1.当我们第一次执行 ./gradlew build 命令的时候， gradlew 会读取 gradle-wrapper.properties 文件的配置信息
2.准确的将指定版本的 gradle 下载并解压到指定的位置(GRADLE_USER_HOME目录下的wrapper/dists目录中)
3.并构建本地缓存(GRADLE_USER_HOME目录下的caches目录中),下载再使用相同版本的gradle就不用下载了
4.之后执行的 ./gradlew 所有命令都是使用指定的 gradle 版本。如下图所示：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688774440260-67db364f-8e34-4559-82b0-efcec238a444.png#averageHue=%23f5f5f5&clientId=u0499adff-59f9-4&from=paste&height=415&id=u790fe59c&originHeight=454&originWidth=810&originalType=binary&ratio=2&rotation=0&showTitle=false&size=64868&status=done&style=none&taskId=u674bef44-a995-4609-b3d9-b4195ab3d97&title=&width=740)

gradle-wrapper.properties 文件解读:
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688773705419-f722a2f4-ff1d-4dd1-a836-48be2928a9d7.png#averageHue=%23525542&clientId=u0499adff-59f9-4&from=paste&height=161&id=iDWC1&originHeight=322&originWidth=1521&originalType=binary&ratio=2&rotation=0&showTitle=false&size=69145&status=done&style=none&taskId=u8b007560-f083-44e6-a18c-b59f5a0ee9b&title=&width=760.5)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688774470639-c8a50db8-00ff-4f37-ad79-daa3f36795a2.png#averageHue=%23f4f4f4&clientId=u0499adff-59f9-4&from=paste&height=190&id=uaf875440&originHeight=274&originWidth=1070&originalType=binary&ratio=2&rotation=0&showTitle=false&size=92888&status=done&style=none&taskId=u81f9cc7e-35a7-47e3-b0f9-a342c5c8686&title=&width=743)
注意：前面提到的 GRALE_USER_HOME 环境变量用于这里的 Gradle Wrapper 下载的特定版本的 gradle 存储目录。如 果我们没有配置过 GRALE_USER_HOME 环境变量,默认在当前用户家目录下的.gradle 文件夹中。


那什么时候选择使用 gradle wrapper、 什么时候选择使用本地 gradle? 
下载别人的项目或者使用操作以前自己写的不同版本的gradle项目时：用Gradle 什么时候使用本地gradle?新建一个项目时: 使用gradle指令即可。



# IDEA 配置 gradle
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688774952783-592c326b-c362-44c3-87d1-47ef13b65a1a.png#averageHue=%233e4348&clientId=u0499adff-59f9-4&from=paste&height=325&id=u69fef9fe&originHeight=649&originWidth=1247&originalType=binary&ratio=2&rotation=0&showTitle=false&size=116012&status=done&style=none&taskId=ua3947aac-675f-43b3-96ba-8f0e77a0eb0&title=&width=623.5)
选择` 'gradle-wrapper.properties' file`就会使用项目中的gradle wrapper
下载的 gradle 会保存在 Gradle user home目录下，相当于**GRALE_USER_HOME**就是Gradle user home配置的目录


![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688775234649-9d8b203d-c87f-4777-a8dd-15c652a7a123.png#averageHue=%233e4247&clientId=u0499adff-59f9-4&from=paste&height=314&id=ue13596f0&originHeight=628&originWidth=1442&originalType=binary&ratio=2&rotation=0&showTitle=false&size=108685&status=done&style=none&taskId=u441f6596-b524-4b78-81ad-ebd01fa51d6&title=&width=721)
选择 Specified location就是使用本地的 gradle,下载的 gradle 会保存在 Gradle user home目录下

# gradle 下载的 jar 包位置
/Users/(用户名)/.gradle/caches/modules-2/files-2.1
