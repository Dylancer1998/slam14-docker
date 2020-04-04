## 视觉SLAM十四讲：从理论到实践 第二版 docker环境

#### 旨在为想要通过十四讲入坑slam的同学打造一个快捷上手的docker环境。

#### [首先致敬一下原书的repo]([https://github.com/gaoxiang12/slambook2#%E8%A7%86%E8%A7%89slam%E5%8D%81%E5%9B%9B%E8%AE%B2%E4%BB%8E%E7%90%86%E8%AE%BA%E5%88%B0%E5%AE%9E%E8%B7%B5-%E7%AC%AC%E4%BA%8C%E7%89%88](https://github.com/gaoxiang12/slambook2#视觉slam十四讲从理论到实践-第二版))



**流程分为两部分，docker环境下载介绍和slam14代码运行环境使用介绍。**

## docker环境下载安装

#### 下载安装

本环境的docker链接如下：[docker-slam14](https://hub.docker.com/r/bodcoder2/slam14)

或者直接使用命令下载

```dockerfile
docker pull bodcoder2/slam14:latest
```

#### 一些常用命令

docker的原理很复杂，但是上手使用可以很容易。常用的操作不算多，下面列举个别最好用的：

- ##### 打开docker，并让该docker环境和本机环境共享某一个文件夹

  这个的好处不言而喻，传输文件非常方便。

  ```dockerfile
  docker run -it -v /home/hhh/share bodcoder2/slam14:latest /bin/bash
  ```

- ##### 打开docker，共享文件的同时和本机保持一定的端口映射

  这个的好处在于，如果你是选择在服务器上远程跑代码并搭配CLION这样支持远程调试的IDE的话，简单的端口映射能够让你的远程docker环境一样能够被本地的IDE找到。

  ```dockerfile
  docker run -it -p 50002:22 -v /home/hhh/share ubuntu:18.04 bodcoder2/slam14:latest /bin/bash
  ```

  

## slam14代码运行环境说明

### 版本说明

**g++:** 7.4.0

**Eigen:** 3.3.4

**OpenCV:** 3.4.8

**OpenCV_Contrib:** 3.4.8

**Sophus:** 13fb328

**Ceres: **e51e9b46f6

**g2o:** 9b41a4e

**DBow3:**  c5ae539abd

**Pangolin:**  master



### 使用说明

- 代码路径在 ``/root/SLAMCode/slambook2``

- 环境路径

  环境路径安装在``/root``下，没有像书中建议那样全部装在3rdparty文件夹；

  但是绝大部分的章节在其build子目录下都已经编译通过，参考其cmakelist可以容易找到相应的环境路径。