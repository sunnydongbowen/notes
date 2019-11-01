### 安装

```shell
# 下载，下载完改一下权限就可以用了。【下载下来，传NAS】,以后用的时候上传服务器，改权限即可
 wget http://sourceforge.net/projects/nmon/files/nmon16e_x86_rhel72
```

　  [参考链接1](https://blog.csdn.net/w4187402/article/details/90203789)

​      [参考连接2](https://www.cnblogs.com/wnfindbug/p/5719181.html)

### 使用

```shell
#　采样
 ./nmon -f -s 10 -c 3600  ＃　 每10s采用一次，采样3600次，10个小时
 ./nmon -f -s 10 -c 360      采样一个小时
```

![1568185872331](1568185872331.png)

### 分析

​      需要下载专用的分析器来分析。nmon是 IBM公司开发的。性能测试是对服务器性能很重要的一个环节。  ./nmon 可以选择要看的项目。这个监控对性能测试还是很有帮助的，几乎不占cpu。可以结合zabbix，基本上满足性能测试的监控监控方案了。对于zabbix，自己也要深入研究一下。很有用。







  

  

  

 

