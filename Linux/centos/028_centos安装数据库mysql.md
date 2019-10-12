​      安装mysql ，其实自己可以针对不同的系统，做一些常用软件的安装包。到时候直接脚本一键安装就好了。这依赖于shell脚本

​       对于开发技能，python必须要精通，shell，c 其次也要掌握。前端。java 果断放弃。要求会的东西。必须要会。所以其实自己有很多东西要学的啊。

​       比如mysql，python3环境等。常用的。到时候就不需要手动一步一步执行了。虽说熟练了手动装起来也很快。但是其实还是自动安装方便一些。

```shell
wget http://dev.mysql.com/get/mysql57-community-release-el7-8.noarch.rpm   
rpm -ivh mysql-community-release-el7-5.noarch.rpm
yum install mysql-server
chown  -R root:root /var/lib/mysql
service mysqld  restart
# 初次安装，查看初始密码
grep "password" /var/log/mysqld.log
# 修改密码前，修改下面的文件，加一句 validate_password=off
Cat  /etc/my.cnf

```

​      设置远程

```mysql
 grant all privileges on *.* to 'root'@'%' identified by '123456' with grant option;
 flush privileges;
```

​        

​      