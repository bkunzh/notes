## 步骤
1. 准备好你想要开机启动的jar包，并放入任意一个目录下，本文将jar包(test.jar)放在了桌面上，即C:\Users\admin-pc\Desktop\test.jar
2. 创建一个.bat文件run.bat
java -jar C:\Users\admin-pc\Desktop\test.jar > G:\windowsStart\test_start.log
3. 创建一个.vbs文件run.vbs
```
Set ws = CreateObject("Wscript.Shell") 
ws.run "cmd /c G:\windowsStart\test_start.bat",vbhide
```
4. 将vbs文件放到“启动”目录下C:\Users\zhang\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
（运行: shell:startup 可进入目录）

## 参考
- <https://blog.csdn.net/qq_32599479/article/details/87861815>

