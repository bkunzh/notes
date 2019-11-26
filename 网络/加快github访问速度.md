## 慢的原因
GitHub 在中国大陆访问速度慢的问题原因有很多，但最直接和最主要的原因是 GitHub 的分发加速网络的域名遭到 DNS 污染。

## 操作
一般的 DNS 问题都可以通过修改 Hosts 文件来解决。

访问https://www.ipaddress.com/，搜索对应的域名的ip配置在hosts即可。
本地配置如下：（可能不同网络不一样）
```
140.82.114.4 github.com
199.232.5.194  github.global.ssl.fastly.net
185.199.108.153 assets-cdn.github.com
185.199.111.154 github.githubassets.com
```
运行 ipconfig /flushdns 手动刷新系统DNS缓存。

## 参考
- 搜索 `加快 github 访问速度`
- <https://boke112.com/6397.html>