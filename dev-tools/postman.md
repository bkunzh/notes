## 很强大的api管理、测试工具
## tips
1. 可以写简单的脚本自动测试返回的内容是否正确
2. 可以设置多个环境  
只用简单切换就可以在不同环境访问不同ip的接口，如{{myhost}}设置在url中，这种变量除了放在url中，还可以放在request的header、body中  
环境变量、全局变量，当名称一样时，环境变量生效
3. pre-request script可以在请求开始前做一些事情，比如请求一个接口的内容做这次请求的数据用
4 可以保存请求和响应作为一个example
5. 可以发布文档，可以有多个工作空间（个人、team）。可以分组管理api
6. 更多功能在今后使用中发现，要有好奇心。postman是个很酷的软件！！