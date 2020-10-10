Windows命令查看文件的MD5_SHA256

```
certutil -hashfile yourfilenameaddress MD5

certutil -hashfile yourfilenameaddress SHA256

certutil -hashfile yourfilenameaddress SHA1

其中yourfilenameaddress代表想查看文件的路径地址（包含后缀）
```