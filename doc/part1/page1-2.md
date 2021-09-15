# 配置python环境

实验室的服务器被很多人同时使用，每个人跑程序需要依赖一套python环境，每个人使用自己的Python虚拟环境可以避免跟其他人互相影响

> 创建Python虚拟环境需要virtualenv的支持，现在实验室的服务器都带有这个软件  
> 如果提示找不到virtualenv，请切换成管理员账户自行安装

## 新建python虚拟环境

首先确认Xshell/Royal TSX登陆的是刚刚新建属于的**自己的账号**

创建虚拟环境有2个参数可选:  
1.\$version，代表python的版本(2.7/3.5/3.6/etc.)  
2.\$dir，代表虚拟环境的目录  

> 安装虚拟环境的前提是机器上已经安装过了相应的python解释器，安装虚拟环境前请先查看本机器已有python解释器版本

在这个教程中我们创建**python3.6**的虚拟环境，并且放在用户根目录的**py3**下(～/py3)
`~`的意思是用户根目录，举个例子，如果你的用户名是`username`，那么`~`代表的就是`/home/username`  
选择好参数之后，使用命令  
`virtualenv -p $version $dir`  
创建虚拟环境 根据本次教程的选择，输入以下命令创建一个存放在 ～/py3的python3.6版本的虚拟环境:  
`virtualenv -p python3.6 ~/py3`  
创建完成后，在虚拟环境的目录中bin文件夹下，会生成一个脚本:**activate**  
输入命令  
`source ~/py3/bin/activate`  
可以激活虚拟环境  
如果`(py3)`作为前缀出现在了命令行前说明激活成功，此时输入`deactivate`可以退出激活环境

![image](https://user-images.githubusercontent.com/35798056/133462723-93c3710f-b3a1-4c3d-afe6-b164c781846e.png)


> 处于激活状态时:  
> 1.pip默认会把python包安装在这个虚拟环境中  
> 2.默认使用这个虚拟环境中的python解释器运行代码

## 修改pip源

python通过pip管理包，下载依赖包时需要使用网络  
但是服务器默认不连外网，另外从下载速度考虑，我们希望pip可以通过[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/help/pypi/)下载python包  
接下来我们把pip源配置为清华源  
首先输入以下命令

```text
mkdir ~/.pip
nano ~/.pip/pip.conf
```

以上命令会打开文本编辑器，把下面的文字复制进去--&gt;Ctrl+X--&gt;y--&gt;回车，即可完成保存
```
[global]  
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```


之后pip都会从清华下载包，速度快，不需要登录网关联网

> 东南部的学校可以优先考虑[中科大pip源](https://lug.ustc.edu.cn/wiki/mirrors/help/pypi)
