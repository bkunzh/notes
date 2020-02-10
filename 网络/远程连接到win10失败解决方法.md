## 方法
- 计算机属性设置中的允许远程连接要打开
- telnet ip 3389
- 检查服务是否有启动
    - Remote Desktop Services
    - Remote Desktop Configuration
- netstat -aon|findstr "3389"

## 参考
<https://blog.csdn.net/duan_zhihua/article/details/52512294>  
win 10  在端口 3389: 连接失败

