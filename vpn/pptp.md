Linux 搭建 vpn 服务（pptpd协议）
===

参考博客：  
[Jarett's Blog](https://www.nigesb.com/setup-your-own-vpn-with-pptp.html)

## 1、安装 pptpd
Ubuntu 系统：sudo apt-get install pptpd
CentOS 系统：sudo yum -y install pptpd

注：如果是 root 用户，则可以去掉 sudo 不写。

## 2、配置 IP 地址
编辑 /etc/pptpd.conf 文件，在文件最后加入 IP 地址配置：  
localip 10.0.0.1  
remoteip 10.0.0.100-200  

上面的IP地址是可以随便填的，ABC三类的内网地址都可以，主要兼顾其他地方的IP配置，不要出现IP冲突就可以了。后面的 remoteip ，默认从第一个 10.0.0.100 开始分配给客户，localip 表示分配给服务器的内部网关地址。

## 3、配置客户端 DNS
首先确认配置。查看 /etc/pptpd.conf 中指定的 option 文件。我的如下：  
![][dns-option.jpg]
