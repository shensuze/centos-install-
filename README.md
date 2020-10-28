# centos-install-
华为云安装步骤以及遇到的问题
1、图形化界面，ubuntu安装找不到鼠标，官方教程里只显示了centos显示鼠标的方法，因此安装了centos7

X86云服务器使用了cirrus虚拟显卡，鲲鹏云服务器使用的是virtio GPU。鼠标显示有两种方式，分别称为Software Cursor和Hardware Cursor。
virtio GPU默认使用Hardware cursor，hardware cursor会依赖VNC客户端去显示鼠标光标的位置和形状，如果hardware cursor配置了“Let remote server deal with cursor”，那么客户端会忽略这些请求。因此这种情况下鼠标就显示不出来了，远程连接云服务器不显示鼠标。
1.2 安装archiconda，解压进入目录以后，修改vi archiconda/.condarc,添加阿里源
1.3 安装keras时使用conda无法找到源，因此采用cd archiconda3后pip keras==2.2.5
2、安装numpy等库的时候下载很慢，创建.pip/pip.conf文件，在其中添加阿里云镜像连接
3、安装numpy时要求python版本大于3.6，下载解压python3.6，并将centos中的软链接修改为相应文件夹地址
(http://c.biancheng.net/view/4162.html    
$sudo unlink /usr/bin/python
$sudo ln -s /usr/bin/python3.8 /usr/bin/python)
4、修改显示无pip模块，先vim /usr/bin/yum，将import中的python改为原版本（2.7），然后yum install python3-pip
