#  root用户自登陆

​      ubuntu 系统 默认是不允许root用户登陆的,这个文档仅供参考。具体的根据实际来。不同的Ubuntu版本是不一样的。debian版本更是不一样。

1. ​    修改lightdm.conf 配置文件

```shell
sudo vi /etc/lightdm/lightdm.conf 
[Seat:*]
autologin-guest=false
autologin-user=root
autologin-user-timeout=0
greeter-session=lightdm-gtk-greeter
```

2.    修改50-ubuntu.conf 配置文件

```shell
vi /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
# 添加下面一行
greeter-show-manual-login=true 
```

3. 修改下面文件

```shell
sudo vi /root/.profile 

# ~/.profile: executed by Bourne-compatible login shells.

if [ "$BASH" ]; then
  if [ -f ~/.bashrc ]; then
    . ~/.bashrc
  fi
fi
# 主要是修改下面一行
tty -s && mesg n || true 
```





