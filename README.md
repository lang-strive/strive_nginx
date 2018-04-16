## nginx:
``` bash
  1.应用场景
  1.http服务器
  静态资源 图片 js css
  2.虚拟主机
  *虚拟出多个主机，域名80
  IP
  端口
  域名
  3.nginx反向代理
  正向代理:
  从内网到外网的过程属于正向代理.
  反向代理:
  从外网到内网的过程属于反向代理.
  4.负载均衡
```

## openresty:
``` bash
nginx+lua
```

## 1.nginx安装:
> 网址:
``` bash
  http://nginx.org/en/download.html
```
> linux安装:
``` bash
  wget http://nginx.org/download/nginx-1.12.2.tar.gz
```

## 2.安装前提:
> 因为nginx是c开发的

``` bash
1.gcc
对源码进行编译
yum install gcc-c++

2.PCRE
perl库 包括了perl兼容的正则表达式 nginx的http模块使用的是pcre来解析正则
yum install -y pcre pcre-devel


3.zlib
压缩和解压的库 nginx 使用zlib对http包进行 gzip
yum install -y zlib zlib-devel

4.openssl
yum install -y openssl openssl-devel
```

## 3.nginx安装:
``` bash
1.解压
  tar -zxvf nginx-1.12.2.tar.gz
  2.cd 到解压目录
  ll     //查看然后切换
  cd nginx-1.12.2
  3.configure  //命令行直接粘贴下面的代码
  ./configure --prefix=/app/nginx \
  --with-pcre \
  --with-http_stub_status_module \
  --with-http_realip_module \
  --with-http_addition_module \
  --with-http_ssl_module \
  --with-file-aio \
  --with-debug \

  ll  查看就会生成MakeFile文件
4.编译安装
  make && make install

5.启动nginx
  cd /app/nginx/
  cd sbin
  ./nginx
  此方式默认加载的是conf/nginx.conf配置文件

6.修改加载配置文件（一般不会修改）
  ./nginx -c /app/nginx/conf/nginx.conf

7.关闭nginx
  方式一：
    ./nginx -s stop
    先查出pid 然后再kill(会丢包)
  方式二：完整停止 优雅关闭
    ./nginx -s quit
    等待nginx处理进程把请求处理完毕 完后再停止

8.重启
  方式一：
    ./nginx -s reload
  方式二：
    ./nginx -s quit
    ./nginx

9.查看nginx是否启动
  ps -ef | grep nginx 

10.切换到root权限
  su

11.安装上传文件
  yum install -y lrzsz

12.Linux开启80端口
  https://www.cnblogs.com/cnsevennight/archive/2016/06/27/5619424.html
```
