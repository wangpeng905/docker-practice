# docker-practice
在看完《Docker-从入门到实践》之后，做了一些定制 Docker 镜像的练习。

例如在 Ubuntu 16.04 基础镜像上搭建 RNA-seq 数据分析环境……

## 自己动手写 dockerfile 的注意事项

 - ADD 与 COPY 的区别，ADD 命令会自动将压缩的源文件解压（偷摸解压缩，毫无提示），这可能会导致后续看 dockerfile 时对压缩文件的操作产生疑惑。
 - dockerfile 中运行 source 命令，正确方式是单独运行 /bin/bash -C
 
 ```shell
 RUN /bin/bash -c "source file"
 ```
 
 - dockerfile 中安装软件，configure 的正确方式
  
  ```shell
  autoconf && ./configure
  ```
  
 - 善用 &&，在每条命令中清理不需要的文件，避免 Docker 镜像体积过大。
