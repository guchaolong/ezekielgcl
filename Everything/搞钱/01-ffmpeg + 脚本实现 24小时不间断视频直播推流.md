keys:
云服务器
自动化
7×24小时陪伴型直播
推流



# 窗口管理工具：
`yum -y install screen`

# 创建目录
video_live为整个项目目录
video 用来存放视频文件

`mkdir -p /root/video_live/video`

# 下载视频
downie4 下载视频，downie4可以设置 格式 mp4, 1080p

# Mac上传本地文件到服务器
>windows系统，我们可以使用xftp或者rz命令，那么mac呢？ mac系统，我们可以使用sftp、scp或者rz命令

## scp

上传：在本地机器执行以下命令，向 Linux 轻量应用服务器上传文件
`scp 本地文件地址 服务器用户名@服务器实例公网IP/域名:轻量应用服务器文件地址`

例如：
`scp /home/Inmp0.4.tar.gz root@129.20.0.2:/home/Inmp0.4.tar.gz`

`scp /Users/ezekiel/Downloads/Islands 4K.mp4 root@120.24.58.36:/root/video_live/video/Islands 4K.mp4`


下载：在本地机器执行以下命令，将 Linux 轻量应用服务器上的文件下载至本地
`scp 轻量应用服务器用户名@轻量应用服务器实例公网 IP/域名:轻量应用服务器文件地址 本地文件地址 `

例如，您需要将 IP 地址为 `129.20.0.2` 的轻量应用服务器文件 `/home/lnmp0.4.tar.gz` 下载至本地对应目录下，则执行的命令如下：
`scp root@129.20.0.2:/home/Inmp0.4.tar.gz /home/Inmp0.4.tar.gz`



## sftp
终端-新建远程连接-sftp
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202311070107434.png)
登录成功后，我们就可以输入命令“ put 本地文件路径 远程路径 ”将本地的文件上传到服务器了。（不写远程路径的话默认保存在/root下）

本地路径复杂的话，直接把文件拖进终端，会自动生成
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202311070110848.png)



# 推流脚本
原脚本参考[FFmpeg循环推流脚本-荒岛](https://lala.im/4816.html)

为了控制视频的码率，合理利用服务器的带宽，修改原脚本 72-78 行内容为：
```
		video=$(find ./ -type f | shuf -n 1)
  		ffmpeg -re -i "$video" -preset ultrafast -vcodec libx264 -g 60 -b:v 6000k -c:a aac -b:a 128k -strict -2 -f flv ${rtmp}
 	done
fi
 	}
```

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202311041441208.png)

`-preset ultrafast` 用最快的编码方式
`-vcodec libx264` 用libx264编码器
`-b:v 6000k` 视频码率，如果是海外平台，可以调高一点，如果每个月流量是有限的，设置 1500k 左右
`-b:a 128k` 音频的，92k 128k都可以


修改后完整脚本为
```bash
#!/bin/bash
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin:~/bin
export PATH
#=================================================================#
#   System Required: CentOS7 X86_64                               #
#   Description: FFmpeg Stream Media Server                       #
#   Author: LALA                                    #
#   Website: https://www.lala.im                                  #
#=================================================================#

# 颜色选择
red='\033[0;31m'
green='\033[0;32m'
yellow='\033[0;33m'
font="\033[0m"

ffmpeg_install(){
# 安装FFMPEG
read -p "你的机器内是否已经安装过FFmpeg4.x?安装FFmpeg才能正常推流,是否现在安装FFmpeg?(yes/no):" Choose
if [ $Choose = "yes" ];then
	yum -y install wget
	wget --no-check-certificate https://www.johnvansickle.com/ffmpeg/old-releases/ffmpeg-4.0.3-64bit-static.tar.xz
	tar -xJf ffmpeg-4.0.3-64bit-static.tar.xz
	cd ffmpeg-4.0.3-64bit-static
	mv ffmpeg /usr/bin && mv ffprobe /usr/bin && mv qt-faststart /usr/bin && mv ffmpeg-10bit /usr/bin
fi
if [ $Choose = "no" ]
then
    echo -e "${yellow} 你选择不安装FFmpeg,请确定你的机器内已经自行安装过FFmpeg,否则程序无法正常工作! ${font}"
    sleep 2
fi
	}

stream_start(){
# 定义推流地址和推流码
read -p "输入你的推流地址和推流码(rtmp协议):" rtmp

# 判断用户输入的地址是否合法
if [[ $rtmp =~ "rtmp://" ]];then
	echo -e "${green} 推流地址输入正确,程序将进行下一步操作. ${font}"
  	sleep 2
	else  
  	echo -e "${red} 你输入的地址不合法,请重新运行程序并输入! ${font}"
  	exit 1
fi 

# 定义视频存放目录
read -p "输入你的视频存放目录 (格式仅支持mp4,并且要绝对路径,例如/opt/video):" folder

# 判断是否需要添加水印
read -p "是否需要为视频添加水印?水印位置默认在右上方,需要较好CPU支持(yes/no):" watermark
if [ $watermark = "yes" ];then
	read -p "输入你的水印图片存放绝对路径,例如/opt/image/watermark.jpg (格式支持jpg/png/bmp):" image
	echo -e "${yellow} 添加水印完成,程序将开始推流. ${font}"
	# 循环
	while true
	do
		cd $folder
		for video in $(ls *.mp4)
		do
		ffmpeg -re -i "$video" -i "$image" -filter_complex overlay=W-w-5:5 -c:v libx264 -c:a aac -b:a 192k -strict -2 -f flv ${rtmp}
		done
	done
fi
if [ $watermark = "no" ]
then
    echo -e "${yellow} 你选择不添加水印,程序将开始推流. ${font}"
    # 循环
	while true
	do
		cd $folder
		video=$(find ./ -type f | shuf -n 1)
  		ffmpeg -re -i "$video" -preset ultrafast -vcodec libx264 -g 60 -b:v 6000k -c:a aac -b:a 128k -strict -2 -f flv ${rtmp}
 	done
fi
 	}

# 停止推流
stream_stop(){
	screen -S stream -X quit
	killall ffmpeg
	}

# 开始菜单设置
echo -e "${yellow} CentOS7 X86_64 FFmpeg无人值守循环推流 For LALA.IM ${font}"
echo -e "${red} 请确定此脚本目前是在screen窗口内运行的! ${font}"
echo -e "${green} 1.安装FFmpeg (机器要安装FFmpeg才能正常推流) ${font}"
echo -e "${green} 2.开始无人值守循环推流 ${font}"
echo -e "${green} 3.停止推流 ${font}"
start_menu(){
    read -p "请输入数字(1-3),选择你要进行的操作:" num
    case "$num" in
        1)
        ffmpeg_install
        ;;
        2)
        stream_start
        ;;
        3)
        stream_stop
        ;;
        *)
        echo -e "${red} 请输入正确的数字 (1-3) ${font}"
        ;;
    esac
	}

# 运行开始菜单
start_menu
```

/root/video_live下面新建 live.sh,复制上面的代码,保存,赋执行权限
```
cd video_live
touch live.sh
vim live.sh
chmod 777 live.sh
```

# 执行脚本
所有脚本都是后台运行的，不然你退出命令行后，脚本就会停止工作了，可以使用 nohup、tmux、screen等命令来配合使用

开个新窗口，并取名为 live：
`screen -S live`

`./live.sh`
选 2，输入直播间地址
复制服务器地址、再复制串流地址
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202311041408973.png)
输入视频存放目录：`/root/video_live/video`
水印？不要加了

然后视频就会开始推了，脚本窗口在运行，直播间有视频了

# 关机不间断推流、关闭推流
上一步之后，脚本开始执行，如果把 screen 的窗口关闭，那直播就断了，为了让我本机可以关机，服务器也能不间断的推流:
`cmd + d`打开一个窗口
`ssh aliyun`连上服务器

`screen -ls`看一下，有哪些进程在跑
能看到此时此刻正在推流直播的进程，比如 11729.live (Attached)
括号中的 Attached 就表示关联了上一步中执行脚本的窗口，如果那个窗口关闭了那直播就断了

为了让进程脱离脚本执行窗口的控制，使用命令 `screen -d 11729.live`，然后原窗口就停止运行了，这时候就可以关闭本地电脑了，推流进程会不间断的运行

如果想要关闭推流
`screen -X -S 11729.live quit`
关闭之后服务器就不在推流了，不再消耗流量 不再运算了，关闭直播就好





---

以上是使用 ffmpeg + 脚本实现的

下面介绍另一种推流方法，使用工具kplayer
文档：
[Docker部署KPlayer，实现24小时无人直播(B站、斗鱼、虎牙等)](https://blog.fanjunyang.zone/archives/docker-live-stream)
[KPlayer文档](https://docs.kplayer.net/v0.5.8/quick/install.html)

```
# 安装
curl -fsSL get.kplayer.net | bash

cd kplayer

./kplayer

./kplayer play start --daemon

./kplayer play stop

```

config.json
```json
{
  "version": "2.0.0",
  "resource": {
    "lists": [""],
    "extensions": ["mp4","flv"]
  },
  "output": {
    "lists": [
      {
        "path": ""
      }
    ],
    "reconnect_internal": 5
  },
  "play": {
    "fill_strategy": "ratio",
    "skip_invalid_resource": true,
    "cache_on": true,
    "play_model": "loop"
  }
}
```

