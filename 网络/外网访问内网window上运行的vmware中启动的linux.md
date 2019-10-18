## vmware 设置网络
在虚拟机设置中，可以设置NAT模式或者桥接模式（如果是wifi，不要勾选复制物理网络连接状态）都能访问网络。  
NAT模式，设置的端口转发更稳定一些。

## windows 端口转发
不稳定。建议用NAT模式，可以在wmware网络设置端口转发。
cmd管理员模式运行：  
netsh interface portproxy add v4tov4 [listenaddress=localaddress] listenport=localport connectaddress=destaddress connectport=destport  

1.listenaddress -- 等待连接的本地ip地址  
2.listenport -- 本地监听的TCP端口（待转发）  
3.connectaddress -- 被转发端口的本地或者远程主机的ip地址  
4.connectport -- 被转发的端口  

下面的命令是用来展示系统中的所有转发规则：  
netsh interface portproxy show all

删除端口映射  
netsh interface portproxy delete v4tov4 [listenaddress=localaddress] listenport=localport

(通过桥接，用windows命令来转发端口，重启之后，貌似要把映射删掉，再设置。nat模式，用vmware可以设置端口转发)

参考<http://foreversong.cn/archives/1117>


## 路由器公网ip端口转发到windows端口，windows转发到linux端口
路由器端口转发

## 因为windows防火墙，所以会失败：路由器公网ip端口转发到windows端口，windows转发到linux端口
暂时关闭windows防火墙