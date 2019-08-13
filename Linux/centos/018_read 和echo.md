其实这个不算是基本命令了，算是shell脚本里的内容吧

+ read       read v1 v2 接受从键盘输入的两个值。从键盘输入后可通过echo $v1 $v2 将其显示出来。

  ```shell
  [root@ocloud50 usr]# read v1 v2
  20 3[root@ocloud50 usr]# echo $v1 $v2
  20 30
  ```

  

   + echo   在显示器上显示一段文字，一般起到提示作用，在shell脚本编程中极为常见。#是注释，一般解释脚本内容，作者等。

     ```shell
     [root@ocloud50 usr]# echo -e 'hello world'
     hello world
     [root@ocloud50 usr]# echo -e 'hello world \a\a'
     hello world
     [root@ocloud50 usr]# echo \ 'hello world \a\a'
      hello world \a\a
     ```

 [echo命令详解]( https://www.cnblogs.com/karl-python/p/9261920.html)

