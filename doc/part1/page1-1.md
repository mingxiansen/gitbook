# 新建服务器账号

## 连接服务器

为了使用服务器，你需要:

* 知道服务器的ip地址  
* 拥有**管理员权限**的服务器账号  

我们通过SSH的方式连入服务器，需要使用SSH客户端。对于windows系统，推荐使用Xshell；对于Mac系统，推荐使用Royal TSX。

**-FOR WINDOWS**

Xshell-6是付费软件，但是提供免费教育版本，需要填写学校邮箱申请.(需要等待申请通过)  

·  安装完成之后打开Xshell.  
·  在"会话"窗口中点击左上角的"新建"，进入新建连接的界面.  
·  只需要修改下图中的2个红框部分，名称自行选择，"主机"填写服务器的ip地址.

![Xshell新建连接](../../img/part1/xshell-create_session.png)

完成之后，点击确定，回到"会话"界面就会看到新建的连接.

![连接列表](../../img/part1/xshell-session_list.png)

双击之后，进入填写用户的界面，填入有管理员权限账号的用户名-&gt;确定-&gt;填密码-&gt;确定.  
看到`name@xxx:~$` 就说明登录成功了.

> 这里的name表示的是管理员账号的用户名



**-FOR macOS**

Royal TSX 是一个强大的全面的远程连接管理软件，兼容多种连接类型。免费版本的Royal TSX最多可以连接10个连接。我们可以用它通过SSH、SFTP来登陆和部署Linux服务器。

·  进入官网下载安装Royal TSX：https://www.royalapps.com/ts/win/features

·  command + ，进入偏好设置，点击 Plugins 添加插件 Terminal 和 File Transfer 这两款插件。

![image](https://user-images.githubusercontent.com/35798056/133458571-03b391ba-9ac9-4bd5-a23f-91cdcc879bc0.png)

·  新建document：File->document

·  新建terminal：新建connection（左下角”+”)->terminal

![image](https://user-images.githubusercontent.com/35798056/133459252-5c6c7c8e-7fdf-49b7-90d8-87b64b7d1ff1.png)

·  填写连接信息：Display name：connection name，connection type：SSH，computer name：服务器IP地址

![image](https://user-images.githubusercontent.com/35798056/133459375-f35dc98e-fb0b-4bdf-ab2a-74106bfc1e15.png)

·  登陆：credential->输入管理员账号密码->apply登陆服务器

![image](https://user-images.githubusercontent.com/35798056/133459434-16cdf54e-dee0-4c2d-997f-ced5e793911b.png)

·  成功进入服务器

![image](https://user-images.githubusercontent.com/35798056/133459502-af1639b5-1b51-4aab-816a-e364bbed4ac6.png)


## 创建自己的账号

> 注意:这里的 **$USER-NAME** 指的是自己新账户的账户名

登陆成功之后，继续在刚才的界面输入  
`sudo adduser $USER-NAME` + 回车  
创建自己的账户 出现  
`[sudo] xxx 的密码：`  
之后，输入**管理员帐号**的密码，之后回车

> 有两点需要注意:  
> 1.输入的是**管理员账号**的密码，不是自己新账号的密码  
> 2.输入密码之后不会出现 **\*\*\*\*** ，不要慌，问题不大，正常输入密码就行

出现  
`输入新的 UNIX 密码：`  
之后，输入自己**新帐号**的密码，之后回车，再输入一次，然后一路连续回车，不用管，直到创建完成
![image](https://user-images.githubusercontent.com/35798056/133459657-08239a10-9ee4-40af-80a3-5fe0db2b1a25.png)


## 使用自己的账号

> 注意:  
> 1.这里的 **$username** 指的是自己新账户的账户名  
> 2.`su` 是切换账户的命令

创建完成之后，输入  
`su $username` + 回车  
再输入自己的密码，可以切换到自己的账号，来完成之后的操作  
切换账号会后记得再输入`cd ~` 把当前目录切换到自己的目录下

## 把自己的账号添加到Xshell/Royal TSX中

**-FOR WINDOWS**

·  点击Xshell左上角的"文件"->;"打开"->双击之前的服务器连接  
·  此时可以填写自己的账号信息，并且勾选下面的保存用户名/密码  
·  之后就可以双击之后直接登陆，并出现:
`name@xxx:~$`  
中的name就是当前登录的账号，通过这个可以知道目前登陆的是不是自己的账号


**-FOR macOS**

·  Terminal->properties->credential->输入你自己的账号密码->apply

![image](https://user-images.githubusercontent.com/35798056/133460887-c9bc261c-743a-436e-8169-f93b5999d225.png)


## 上传文件至服务器

刚刚我们在服务器上创建了属于自己的账号，但是如何把本地的文件传输到服务器呢  

**-FOR WINDOWS**

这里推荐一个好用免费的远程文件管理软件Winscp([下载地址](https://winscp.net/eng/download.php))  
打开Winscp之后，先选择新建站点，然后按照图中红框从上到下的顺序依次操作:  
1."主机名":填入服务器的IP  
2."用户名和密码":填入刚刚新建账户的用户名和密码  
3.点击保存和登录

![winscp新建连接](../../img/part1/winscp.png)

Winscp的左侧是本地文件，右侧是服务器文件  
软件提供了可视化的上传下载操作，简单易上手，具体细节就不再多说了


**-FOR macOS**

·  新建file transfer：新建connection（左下角”+”)->file transfer
![image](https://user-images.githubusercontent.com/35798056/133461352-e039b856-8f78-4cb7-a64f-ebad199396e3.png)

·  填写连接信息：Display name：connection name，connection type：SFTP，computer name：服务器IP地址

·  登陆：credential->输入管理员账号密码->apply登陆服务器，即可upload/download文件

![image](https://user-images.githubusercontent.com/35798056/133461516-6f399234-1904-4ca6-8aa1-8f542ce7d7e2.png)


