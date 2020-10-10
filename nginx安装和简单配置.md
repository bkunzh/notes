## 1. nginx安装和简单配置
#首先从nginx官网下载源码包

```
tar -tf xx.tar.gz #不解压，查看tar.gz文件列表
tar -C ./ -xzvf nginx-1.15.7.tar.gz
./configure #会报错，需要安装相关依赖

yum install -y zlib zlib-devel
#查看程序安装情况
rpm -qa | grep zlib

./configure 
make
make install

./nginx
./nginx stop
./nginx relod

#查看80端口被谁占用
#netstat依次显示 
#Proto Recv-Q Send-Q Local Address               Foreign Address             State       PID/Program name
netstat -anp | grep 80
netstat -ntpl | grep 80   #tcp端口
lsof -i:80
fuser -v -n tcp 80
killall httpd /service httpd stop
```

### 配置1）nginx配置两个虚拟主机都使用80端口（通过不同域名来区分）
vim conf/nginx.conf
配置如下：


```

 server {
     listen       80;
     server_name  test1.bkunzhang.com;

     location / {
         root   html1;
         index  index.html index.htm;
     }
 
     error_page   500 502 503 504  /50x.html;
     location = /50x.html {
         root   html;
     }
 
 }
 
 server {
     listen       80;
     server_name  test2.bkunzhang.com;

     location / {
         root   html2;
         index  index.html index.htm;
     }
 
     error_page   500 502 503 504  /50x.html;
     location = /50x.html {
         root   html;
     }
 
 }
```

 修改本地hosts:

```

 192.168.230.132 test1.bkunzhang.com
 192.168.230.132 test2.bkunzhang.com
```

 本地访问test1.bkunzhang.com，test2.bkunzhang.com成功！

###  配置2）配置反向代理两个tomcat，通过upstream子节点server的weight配置负载均衡
 需要配置两个tomcat，端口号分别为8080和30011

 ```
    upstream tomcats {
    
    	server 127.0.0.1:8081;
    	server 127.0.0.1:30011 weight=4;
    }
    
    server {
        listen       80;
        server_name  test3.bkunzhang.com;
   
        location / {
            proxy_pass http://tomcats;
            index  index.html index.htm;
        }
    
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
    
    }
 ```

## 2. nginx在windows上的使用

### 快速使用

1. 下载windows版本nginx

2. 解压，在cmd运行nginx.exe，即可以运行

### 修改nginx.conf，配置一个域名反向代理到两个配置中心服务

可以用weight配置负载均衡系数，默认1

   ```
   	upstream myapps {
       
       	server 192.168.3.64:8081 weight=3;
       	server 127.0.0.1:8081;
       	server 127.0.0.1:3301 weight=10;
       }
       
       server {
           listen       80;
           server_name  testconf.bkzh.com;
      
           location / {
               proxy_pass http://myapps; # 配置upstream名称
               index  index.html index.htm;
           }
       
           error_page   500 502 503 504  /50x.html;
           location = /50x.html {
               root   html;
           }
       }
   ```

### 查看与关闭进程

   ```
   # 查看进程
   tasklist /fi "imagename eq nginx.exe"
   
   # 关闭进程
   快速停止 nginx -s stop
   或 完整有序的关闭 nginx -s quit
   
   taskkill /F /pid 32008
   
   # 重新加载配置
   nginx -s reload
   ```

   