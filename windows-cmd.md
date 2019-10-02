## 检测访问一个ip路由路径
tracert baidu.com
## 查看某个端口占用情况
netstat -ano|findstr 6379
netstat -ano|find "6379"
## 杀掉某个pid的进程
taskkill -pid 5860 [-F]