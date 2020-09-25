# pingpong
使用boost/TASSL的pingpong demo

##### 环境搭建
1) 安装TASSL
2) 安装boost 1.57.0
3) 安装cmake version>3.0
4) 安装g++

##### 设置BOOST_ROOT变量
export BOOST_ROOT=boost安装位置

##### 分别运行cmake, 生成ssl_server/ssl_client
```c
make buld && cd build && cmake .. && make
```
