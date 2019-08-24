

#  Ubuntu开机时进入gun grup 解决方法

```shell
sudo vi /etc/default/grub 
```

 注释掉   GRUB_HIDDEN_TIMEOUT=0         

 将 GRUB_TIMEOUT 修改为 GRUB_TIMEOUT = 0 

  保存退出

```shell
sudo update-grub
```

