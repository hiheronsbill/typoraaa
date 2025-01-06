### 一、概述

> Shell是一个命令行解释器，它接受应用程序/用户命令，然后调用操作系统内核。
>
> Shell还是一个功能相当强大的变成语言，易编写、易调试、灵活性强

![image-20250106152304783](/Users/linkk/codes/freestyle/typoraaa/linux/.images/image-20250106152304783.png)

![image-20250106152338939](/Users/linkk/codes/freestyle/typoraaa/linux/.images/image-20250106152338939.png)



### 二、Shell脚本格式与执行方式



- 脚本以 #!/bin/bash 开头 (指定解析器)

- 执行方式

  - 第一种：采用bash或sh + 脚本的相对路径或绝对路径（不用赋予脚本+x权限）
  - 第二种：采用输入脚本的绝对路径或相对路径（必须具有可执行权限+x）
  - 第三种：在脚本的路径前加上 "." 或者 source

  > 区别：
  >
  > 第一种和第二种都是在当前shell中打开一个子shell来执行脚本内容，当脚本内容结束，则子shell关闭，回到父shell中。
  >
  > 第三种，也就是使用在脚本路径前加 "." 或者source 的方式，可以使脚本内容在当前shell里执行，而无需打开子shell！这也是为什么我们每次修改完/etc/profile文件以后，需要source一下的原因。
  >
  > 开子shell与不开子shell的区别就在于，环境变量的继承关系，如在子shell中设置的当前变量，父shell是不可见的。