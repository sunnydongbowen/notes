目录

[TOC]

##  1、安装服务端

​         在上一篇中，介绍了docker安装的方法。下面参考一个链接，手动安装zabbix服务端，参考网络上的安装方法

​         [安装zabbix-server4.2](https://www.jianshu.com/p/6afd6ecbd505)

​         [第3.4版本安装](https://blog.csdn.net/weixin_41927237/article/details/81712404)    

##  2、客户端安装       

​           客户端未使用docker安装，一方面是因为被测服务器不允许随便安装docker，二是因为使用docker安装，不方便自定义脚本啥的

```shell
# 下载yum 源仓库
wget http://repo.zabbix.com/zabbix/3.2/rhel/7/x86_64/zabbix-release-3.2-1.el7.noarch.rpm
# 安装yum 源
rpm -ivh zabbix-release-3.2-1.el7.noarch.rpm
# 安装zabbix
yum install -y zabbix-agent
```

​           修改配置文件

```shell
vim /etc/zabbix/zabbix_agentd.conf
          Server=192.168.8.136
          ServerActive=192.168.8.136
          Hostname=adai-02
```

​             启动zabbix-agent服务

```shell
systemctl start zabbix-agent.service 
systemctl enable zabbix-agent.service 
```

​             [参考链接](https://www.jianshu.com/p/8ee4517a9600)

  

​              







