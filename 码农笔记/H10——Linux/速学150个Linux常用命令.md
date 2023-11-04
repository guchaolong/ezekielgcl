#Linux

> 常用命令

## man
作用：查看帮助手册
`man -f ls`	查看ls命令的简要信息
`man -w ls`	查看ls命令所在位置
`man -k disk`	搜索跟disk相关的帮助手册
## info
## whatis
相当于man -f
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687855852830-bd070fae-4589-459e-976e-e9d953c9f700.png#averageHue=%230f0b08&clientId=u76d18795-c152-4&from=paste&height=97&id=uf5e41c95&originHeight=87&originWidth=458&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=5554&status=done&style=none&taskId=udcc712fc-6f8f-4e64-b1b1-7c0bc035429&title=&width=508.888902369841)

## 创建文件	touch
## 创建目录 mkdir
## 删除文件和目录 rm
## 删除空目录 rmdir

> Linux下一切皆目录，就算是一个空目录，也是占用磁盘空间的，如果磁盘爆满，想删除一些空目录释放磁盘空间，如果没有rmdir命令，就需要先判断目录是否是空的，然后再用rm命令删除，这样的话效率就低了，rmdir就可以一步到位，是空目录就删除，非空目录就不删除

`rmdir dir1`						删除dir1
`rmdir -p dir1/dir2/dir3	`	递归删除
`rmdir -v dir1	`				删除并显示详细执行过程

## 移动或重命名 mv
mv a.txt b.txt 				将a.txt 改名为b.txt
mv a.txt /mnt/b.txt 		同时更改路径为/mnt/
mv a.txt /opt/ftp/ 			将a.txt 剪切到/opt/ftp/下

## 复制 cp

## 显示文件状态信息命令：stat
## 批量文件重命名命令：rename
## 提取文件或目录名命令：basename
## 提取路径目录部分命令：dirname
## 修改_查看文件属性命令：chattr_lsattr
## 识别文件类型命令：file
## 生成和校验文件的md5值命令：md5sum
## 查找目录或文件命令：find
## 搜索命令位置命令：which
## 查找文件命令：whereis
## 查找符合条件的文档命令：locate
## 改变文件所属用户或组命令：chown
## 改变文件或目录所属组：chgrp
## 改变用户对文件或目录的权限：chmod
## 文本搜索工具：grep
## 文件内查找指定字符串命令：egrep
## 查看文本内容命令：cat
## 逐页阅读文本命令：more
## 分页查看文本内容命令：less
## 查看文件开头内容命令：head
## 查看文本尾部内容命令：tail
## 反向显示文本内容命令：tac
## 统计文件行号命令：nl
## 统计文本字数信息命令：wc
## 文件切割命令：split
## 文本截取命令：cut
## 文件合并命令：paste
## 文本内容排序命令：sort
## 去除重复行命令：uniq
## 比较差异_打补丁命令：diff_patch
## 连接两个文件命令：join
## 字符转换命令：tr
## 流编辑器：sed
## 编程语言：awk
## 显示目录或文件大小命令：du
## 磁盘使用情况命令：df
## 数据同步命令：sync
## 挂载文件系统命令：mount
## 卸载文件系统命令：umount
## 拷备及转换文件命令：dd
## 打包解压文件命令：tar
## 压缩解压命令：zip_unzip
## 压缩解压命令：gzip_gunzip
## 显示系统信息命令：uname
## 显示或设置主机名命令：hostname
## 显示开机信息命令：dmesg
## 查看系统负载命令：uptime
## 显示内存使用情况命令：free
## 限制系统资源命令：ulimit
## 切换系统运行级别命令：init
## 控制系统服务命令：service
## 显示虚拟内存状态命令：vmstat
## 监视系统输入输出设备和CPU的使用情况命令：iostat
## 显示进程间通信设备状态命令：ipcs
## 删除指定ipc资源：ipcrm



