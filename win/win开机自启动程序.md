## 开机自启动任意程序，注册为服务（winsw让任何Windows程序都能运行为服务）
> 使用[winsw](https://github.com/winsw/winsw/releases)  
> 使用说明见<https://github.com/winsw/winsw/blob/master/doc/installation.md>  
- 实践java项目见<https://github.com/bkunzh/spring-study/tree/master/web-test>

myapp.exe install <OPTIONS>  
myapp.exe start/restart
myapp.exe uninstall  

### 程序关闭不了
netstat -ano | findstr 9998  
taskkill -pid 进程ID  # 似乎关不了，只能用任务管理器
//查看Java进程  
wmic process where caption="java.exe" get caption,commandline,ProcessId /value  

```
winsw.xml
<service>
	<id>web-test</id>
	<name>web-test</name>
	<description>test jar windows service using winsw</description>
	<executable>java</executable>
	<arguments>-jar web-test-0.0.1-SNAPSHOT.jar</arguments>
	<logmode>rotate</logmode>
</service>
```

- 参考<https://dzone.com/articles/spring-boot-as-a-windows-service-in-5-minutes>

## 如win开机自启动jar （这种方式麻烦，用上面winsw注册服务方便些）
1. 准备好你想要开机启动的jar包，并放入任意一个目录下，本文将jar包(test.jar)放在了桌面上，即C:\Users\admin-pc\Desktop\test.jar
2. 创建一个.bat文件run.bat
java -jar C:\Users\admin-pc\Desktop\test.jar > G:\windowsStart\test_start.log
3. 创建一个.vbs文件，如test_start.vbs
```
Set ws = CreateObject("Wscript.Shell") 
ws.run "cmd /c G:\windowsStart\test_start.bat",vbhide
```
4. 将vbs文件放到“启动”目录下C:\Users\zhang\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
（运行: shell:startup 可进入目录）

- 参考<https://blog.csdn.net/qq_32599479/article/details/87861815>

