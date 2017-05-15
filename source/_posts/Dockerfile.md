---
title: Dockerfile
date: 2017-03-26 11:49:13
tags: tools
---
我们可以通过Dockerfile来编译image.命令格式为：
```docker build [path/url]```

path是要提供给docker damon的上下文环境，因为编译过程中你可能需要复制一些文件到image。但因为docker damon会加载整个的你设置的目录，所以最好用一个干净的目录并放入你编译过程中所需要的文件。

docker damon会顺序执行Dockerfile中的命令，每执行一个命令就会将结果提交成一个中间image, 在Dockerfile的执行过程中运行docker images命令，会看到这些生成的中间image:
{% img dockerfile /pic/dockerfile.jpg inter-img %}

而且这些命令是独立执行，所以cd到某个目录和用export设置环境变量并不会在下一个命令中生效。但是可以通过Dockerfile的ENV命令来设置环境变量，通过ENV设置的环境变量会一直生效。这些内容在dockerfile的官方文档里一开始就介绍了。

常用的Dockerfile命令：
FROM 设置base image
RUN 运行shell命令
COPY 拷贝文件并将文件加入容器的文件系统
ENV 设置环境变量
EXPOSE 预留端口
