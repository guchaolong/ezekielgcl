

# Nacos

## 下载、启动

下载地址：https://github.com/alibaba/Nacos/releases

解压到：/Users/ezekiel/DevTool/nacos

bin/startup.sh -m standalone

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230920113016.png)

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230920113804.png)


![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230920113829.png)


访问：http://192.168.10.2:8848/nacos

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230920113929.png)

# sentinel


流控效果有快速失败、warm up、排队等待三种

快速失败：适用于对系统处理能力确切已知的情况下，比如通过压测确定了系统的准确水位时，超过 QPS 阈值的请求就直接被拒绝

Warm Up：适用于激增流量，防止流量突然增加，压垮系统
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230921171849.png)


排队等待：适用于脉冲流量，比如：某一秒有大量的请求到来，而接下来的几秒则处于空闲状态，我们希望系统能够在接下来的空闲期间逐渐处理这些请求，而不是在第一秒直接拒绝多余的请求。
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230921173256.png)



快速失败：

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202309211759170.png)

下面的图更容易看
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202309211805727.png)



排队等待：
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202309211821428.png)



![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202309211835105.png)
