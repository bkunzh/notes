## 慢的原因
GitHub 在中国大陆访问速度慢的问题原因有很多，但最直接和最主要的原因是 GitHub 的分发加速网络的域名遭到 DNS 污染。

## 操作
一般的 DNS 问题都可以通过修改 Hosts 文件来解决。

访问<https://www.ipaddress.com/>，搜索对应的域名的ip配置在hosts即可。可以在F12看到哪个请求慢或者失败，搜索对应域名的ip配置hosts，可以加快速度。
当前配置如下：（可能不同网络不一样）
```
140.82.113.4 github.com
199.232.5.194  github.global.ssl.fastly.net
185.199.109.153 assets-cdn.github.com
185.199.108.154 github.githubassets.com
199.232.28.133 raw.githubusercontent.com
199.232.28.133 avatars0.githubusercontent.com
199.232.28.133 avatars1.githubusercontent.com
199.232.28.133 avatars2.githubusercontent.com
199.232.28.133 avatars3.githubusercontent.com
192.30.253.118 gist.github.com
```
运行 ipconfig /flushdns 手动刷新系统DNS缓存。

## 参考
- 搜索 `加快 github 访问速度`
- <https://boke112.com/6397.html>