# 功能
1. 抓包：本地、手机
2. 拦截请求/响应修改：修改请求、修改响应  `choose response->choose a file 可以选择一个文件作为响应，比如chrome调试的jquery是被压缩的，可以替换成原始的jquery文件，很强大`
> 修改响应不用每次断点去修改，可以通过把左侧的请求移动到自动响应器中，修改响应或者选择文件
3. 重发请求：发一样的请求或修改后再发  replay
4. 模拟请求：Composer 
5. TextWizard  timer
6. 自动响应器（Enable rules 选中第二个框，不会影响不匹配的请求，否则会拦截所有请求） AutoResponder
7. 断点、继续Go
8. tools->hosts 可以修改host，不用到系统修改hosts。在没有switch hosts时可以用
    
# 编辑自动响应器中的内容
先用fiddler自带的edit response->textview来编辑保存，再用vim编辑保存，之后可以多次编辑（别的编辑器编辑会导致响应不能解析json）
> 修改单次请求用断点，bpu/bpafter。修改多次请求，替换文件用自动响应器。

# 命令
忘了这些命令，在命令行输入 bp ，敲回车，就能看到提示了  
- bpu
- bpafter
- 用不带参数的命令可以清除断点

# 参考
- <https://juejin.im/post/5cc02b246fb9a032332b3013>
- <https://www.hangge.com/blog/cache/detail_1697.html>