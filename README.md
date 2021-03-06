孔明前端工程师操作服务器端机器必知的linux知识
============


# linux文件系统基本介绍

- /home:  普通用户个人文件夹
- /root:  root用户专用的个人文件夹
- /etc:   一般存放各种配置文件
- /var:   存放经常改变的文件，比如一般网站的根目录就在该文件夹下
- /bin:   一般存放重要的系统程序
- /usr:   一般用来存放各种用户程序
- ...


# linux基本指令

- ls    -- 查看文件
- cd    -- 切换当前位置
- pwd   -- 查看当前位置
- sudo  -- 以某一用户身份来执行指令
- su    -- 切换用户
- man   -- 查看某一指令的帮助手册
- less  -- 查看文件内容
- rm    -- 删除文件（删除之后文件不能恢复，谨慎使用）
- mkdir -- 新建文件夹


# screen指令简介


screen是linux下的一种多重视窗管理程序。
对于普通SSH远程登录linux时，如果连接非正常中断，重新连接时，那么原来操作的窗口就没了。
screen就是为了解决这个问题，ssh连接断开时，原有操作窗口都会保留”

### 如何进入一个会话

- screen -ls                  -- 查看该机器下的所有screen会话
- screen -d/-D [会话名称]     -- -d强制detach其它地方的会话;-D除了强制detach其它地方的会话外，还可以使其它地方退出登录
- screen -r [会话名称]        -- 继续一个处于detach状态的会话(可以和-d/-D配合使用)
- screen -R [会话名称]        -- 新建并命名一个会话(可以和-d/-D配合使用)


### 如何退出一个会话

- Ctrl + a + d                 -- 退出当前会话，使其处于detach状态
- Ctrl + d                     -- 退出当前会话，并销毁当前会话


# git指令简介


### 几个指令

- git status    -- 查看当前工作目录的情况
- git fetch     -- 获取远程代码库上的最新代码
- git merge     -- 合并代码
- git pull      -- 相当于先git fetch获取最新代码，然后再将本分支的远程分支上的更新合到本地分支上
- git checkout  -- 切换分支
- git branch    -- 查看分支


### 如何新建远程代码库

#### 新建本地代码库

1. 命令行创建
   找到任意一个文件夹，执行git init即可，文件夹下会多出一个.git文件夹，里面存放代码库的各种信息
2. 客户端创建
   在任意一个文件夹下，右键打开菜单，git客户端里一般有一个“初始化”的选项


#### 新建远程代码库

##### 创建*.git文件夹

命令行创建(windows下可以用git的命令行工具)：

git clone --bare [想要创建远程代码库的文件夹路径] [想要起的名字].git

比如：git clone --bare kmsocial_3.0 kmsocial3.git

kmsocial3.git ------ 需要上传到服务器的文件夹

##### 上传*.git文件夹到服务器

1. 命令行
   可以用sftp或scp工具上传
2. 客户端
   windows操作系统可以用WinScp或FileZilla上传

##### 初始化服务器上的*.git文件夹

用cd切换到*.git文件夹下，执行：

git init --bare --shared

##### 本地重新clone代码

关键：知道服务器上代码库的绝对路径

比如：julian@facebook.com:/home/julian/git/kmsocial3.git

git clone julian@facebook.com:/home/julian/git/kmsocial3.git

搞定！







