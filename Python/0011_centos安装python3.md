        下面是centos 安装python3.7 版本的步骤

​         很多时候需要在linux下安装python3.x版本，linux系统自带了python2.7版本，但不满足要求。就需要在上面安装python3版本的。安装完成后，在上面执行脚本即可。并不必要说都要用pycharm 去连上去。这样pycharm 设置的项目就很多。会乱。用一台常用的，然后其他服务器直接把脚本上传上去。缺少什么包自己pip下载即可。【但是试了一下，还是直接用Pycharm 远程调试 比较方便一些】

​        [pycharm远程调试步骤](https://jingyan.baidu.com/album/8065f87f56db86233124980d.html?picindex=5)

+ 安装编译相关工具

  ```shell
  yum -y groupinstall "Development tools"
  yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
  yum install libffi-devel -y
  ```

+  下载安装包解压

  ```shell
  cd #回到用户目录
  wget https://www.python.org/ftp/python/3.7.0/Python-3.7.0.tar.xz
  tar -xvJf  Python-3.7.0.tar.xz  # 要把j去掉
  ```

+  编译安装

  ```shell
  mkdir /usr/local/python3 #创建编译安装目录
  cd Python-3.7.0
  ./configure --prefix=/usr/local/python3
  make && make install
  ```

+ 创建软连接

  ```shell
  ln -s /usr/local/python3/bin/python3 /usr/local/bin/python3
  ln -s /usr/local/python3/bin/pip3 /usr/local/bin/pip3
  ```

+ 验证是否成功

  ```shell
  python3 -V
  pip3 -V
  ```

  





​        

​          

​        







