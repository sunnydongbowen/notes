目录 

[TOC]

##  1、docker安装

​             依次执行下面命令

```shell
 yum install docker
 ## 下面如果是新系统，基本不用执行
 yum -y remove docker-ce-cli
 yum -y remove docker-ce
 ## 安装开发工具
 sudo yum install -y  yum-utils device-mapper-persistent-data lvm2
 # 添加软件源信息【可能会报错，yum源问题，更换yum源repos.d这个文件，已放在NAS上】
 sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/dockerce.repo
 # 更新yum缓存【可能会报错】
 sudo yum makecache fast
 # 启动docker
 systemctl start docker
 systemctl enable docker
```

##  2、 查看docker版本

```shell
[root@zabbix-server ~]# docker --version
Docker version 1.13.1, build 7f2769b/1.13.1
```

##  3、安装docker-compose

```shell
yum install docker-compose
# 如果报错，可执行下面语句
wget https://archive.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-7
```

##  4、使用docker搭建zabbix监控server端

​          zabbix监控服务端搭建复杂，之前手动搭过没搭起来，想搭在windows上面又没找到资料。遇到各种报错。于是想到了docker。

### 4.1 yml文件

​          新建 docker-compose.yml文件，内容如下:

```yml
version: '2'
services:
  zabbix-db:
    image: monitoringartist/zabbix-db-mariadb
    container_name: zabbix-server-db
    ports:
      - "3310:3306"
    volumes:
      - zabbix-db-storage:/var/lib/mysql
      - backups:/backups
      - /etc/localtime:/etc/localtime:ro
    environment:
      - MARIADB_USER=zabbix
      - MARIADB_PASS=my_password
  zabbix-server:
    image: monitoringartist/zabbix-3.0-xxl
    container_name: zabbix-server
    depends_on:
      - zabbix-db
    ports:
      - "8888:80"
      - "10051:10051"
    volumes:
      - /etc/localtime:/etc/localtime:ro
    links:
      - zabbix-db:zabbix.db
    environment:
      - ZS_DBHost=zabbix.db
      - ZS_DBUser=zabbix
      - ZS_DBPassword=my_password
volumes:
  zabbix-db-storage:
    driver: local
  backups:
    driver: local

```

### 4.2 编排

​      在yml文件同一目录下执行下面命令

```shell
docker-compose up -d
```

### 4.3 查看日志

```shell
docker logs -f zabbix-server
```

### 4.4 登录zabbix

​      输入[http://192.168.40.73:8888](http://192.168.40.73:8888/)，访问web页面，admin/zabbix

​      到此，zabbix服务端就搭建完成了，简单吧。之前一直以为用docker搭建zabbix-server端不方便，其实在自定义shell或者python脚本等自定义监控项和报警时，其实是在agent端定义的。服务端需要在页面上配置一些东西就可以。所以使用docker搭建zabbix监控服务端，是完全可行的。比手动搭建排除错误，步骤要简单很多。之前在某大公司，同事被zabbix搞的死去活来，当时要是会这个，也不用这么担心了吧。

​         zabbix监控其实很有用，很多大公司在分布式集群监控时使用的就是zabbix 进行二次开发接口。有空多研究一下。

​       关于zabbix的使用，参考链接

​       [zabbix官网](https://www.zabbix.com/documentation/3.4/zh/manual/quickstart/item)

​        [添加磁盘]( https://www.cnblogs.com/baizhantang/p/3253246.html)

​       [zabbix自定义触发器脚本](https://jingyan.baidu.com/article/17bd8e524b94a785ab2bb881.html)

### 4.5  docker 容器开机自启动

​        上一步中，我们搭建了zabbix监控，docker服务是实现开机自启动的（测试过），但是，想让zabbix容器开机自启动，这样就不用开机手动启动容器了。执行下面命令即可，测试生效！

```shell
docker update --restart=always zabbix-server
docker update --restart=always zabbix-server-db
# 启动方法
docker update --restart=always xxx
```

​       



​       

















