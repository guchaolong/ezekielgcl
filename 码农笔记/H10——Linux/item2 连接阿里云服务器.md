
> 优惠购买了阿里云服务器 ESC，99 元一年，新用户返现49，往后三年依旧是每年 99



然后使用 item2 连接服务器


公网 ip: 120.24.58.36


# 服务器配置
`vim /etc/ssh/sshd_config`
找到以下内容，去掉前面的注释（#）
```
PubkeyAuthentication yes 
AuthorizedKeysFile .ssh/authorized_keys
```
重启sshd服务
`service sshd restart`


根据网上的方法，在 item2 中执行以下2个命令的时候，
提示：root@120.24.58.36: Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
`ssh root@120.24.58.36`
`ssh-copy-id -i ~/.ssh/id_rsa.pub root@120.24.58.36`
是因为没有设置服务器实例的密码，在阿里云控制台上设置一下密码
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202311040041074.png)
然后**重启**服务器



# item2连接服务器
2 种连接方式：


方式一：使用ssh
```
1. `# 默认使用 22 端口连接服务器`
2. `ssh root@120.24.58.36``
3. `# 使用 -p 参数指定端口连接服务器`
4. `ssh root@120.24.58.36` -p 23`
```
item2 中执行命令`ssh root@120.24.58.36`，输入密码，就能连上服务器了



方式二：使用ssh密钥
服务器上有个文件 /root/.ssh/authorized_keys，最开始的时候里面什么都没有

本机/Users/ezekiel/.ssh里有公钥私钥（之前生成过）
```
id_rsa ：私钥 
id_rsa.pub ：公钥
```

将本地公钥导入到服务器认证文件中:
`ssh-copy-id -i ~/.ssh/id_rsa.pub root@120.24.58.36`

再查看服务器的/root/.ssh/authorized_keys，里面就有我本机的公钥了

再修改 mac 下的配置文件 ~/.ssh/config （没有则创建）
```
Host aliyun  ### 别名
Hostname 120.24.58.36  ###公网 IP
Port 22  ###端口
User root  ###登录账号
IdentityFile ~/.ssh/id_rsa ###本机私钥地址
```

然后使用命令`ssh aliyun`,就连接上了


# 保持 ssh 连接
用iTerm2进行ssh时，空闲了一段时间就会断掉了

有多种解决办法:

1. 修改服务器端`vim /etc/ssh/sshd_config`
```
ClientAliveInterval 600 ###数值是秒 可以随意设置
ClientAliveCountMax 10 ###如果发现客户端没有响应，则判断一次超时，参数设置是允许超时次数
```


2. 修改ssh配置，间隔60s发送一个no-op包 `vim ~/.ssh/config`（我采用的）
```
Host *
    Port 22
    User root
    ServerAliveInterval 60
    ConnectTimeout 0
    TCPKeepAlive yes
```


 3. 修改 item2 配置,每隔60s发送一个字符
 这个办法的副作用也是有的，比如iTerm2会出现一些并不想输入的字符、vim会有些多余字符插入等等
 ![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202311040146691.png)



4. 客户端进行SSH连接时，直接在命令里加上这个参数即可（推荐！）：
````
ssh -o TCPKeepAlive=yes -o ServerAliveInterval=300 root@120.24.58.36
````

# 退出
使用`exit`命令即可退出 ssh