## 目录
- [目录](#目录)
- [1. 本地代码实验](#1-本地代码实验)
  - [1.1. eg1（cmd）](#11-eg1cmd)
  - [1.2. eg2（在git bash中，利用find命令穷举java文件）](#12-eg2在git-bash中利用find命令穷举java文件)
- [2. 参考 抛开IDE，了解一下javac如何编译](#2-参考-抛开ide了解一下javac如何编译)

## 1. 本地代码实验
### 1.1. eg1（cmd）
`javac -d . -encoding utf-8 UserServiceHandler.java UserService.java`
### 1.2. eg2（在git bash中，利用find命令穷举java文件）

```sh
find src -name "*.java"
find src -name '*.txt'

-- 报错javac只能复制编译java文件生成的class文件，其他文件可能别的工具复制，比如maven或者IDE，手动就麻烦了
-- javac: 无效的标记: src/main/java/com/bkunzh/proxy_study/cglib/a.txt
javac -d mytarget -encoding utf-8 $(find src -name '*.txt')

-- 编译java文件，复制生成的class文件到指定目录
 javac -classpath "D:\software\jdk1.8.0_221\jre\lib\charsets.jar;D:\software\jdk1.8.0_221\jre\lib\deploy.jar;D:\software\jdk1.8.0_221\jre\lib\ext\access-bridge-64.jar;D:\software\jdk1.8.0_221\jre\lib\ext\cldrdata.jar;D:\software\jdk1.8.0_221\jre\lib\ext\common-library-1.0-SNAPSHOT.jar;D:\software\jdk1.8.0_221\jre\lib\ext\dnsns.jar;D:\software\jdk1.8.0_221\jre\lib\ext\jaccess.jar;D:\software\jdk1.8.0_221\jre\lib\ext\jfxrt.jar;D:\software\jdk1.8.0_221\jre\lib\ext\localedata.jar;D:\software\jdk1.8.0_221\jre\lib\ext\nashorn.jar;D:\software\jdk1.8.0_221\jre\lib\ext\sunec.jar;D:\software\jdk1.8.0_221\jre\lib\ext\sunjce_provider.jar;D:\software\jdk1.8.0_221\jre\lib\ext\sunmscapi.jar;D:\software\jdk1.8.0_221\jre\lib\ext\sunpkcs11.jar;D:\software\jdk1.8.0_221\jre\lib\ext\zipfs.jar;D:\software\jdk1.8.0_221\jre\lib\javaws.jar;D:\software\jdk1.8.0_221\jre\lib\jce.jar;D:\software\jdk1.8.0_221\jre\lib\jfr.jar;D:\software\jdk1.8.0_221\jre\lib\jfxswt.jar;D:\software\jdk1.8.0_221\jre\lib\jsse.jar;D:\software\jdk1.8.0_221\jre\lib\management-agent.jar;D:\software\jdk1.8.0_221\jre\lib\plugin.jar;D:\software\jdk1.8.0_221\jre\lib\resources.jar;D:\software\jdk1.8.0_221\jre\lib\rt.jar;F:\gh\Java-study\code\proxy\target\classes;E:\m2_repository\cglib\cglib\3.3.0\cglib-3.3.0.jar;E:\m2_repository\org\ow2\asm\asm\7.1\asm-7.1.jar;E:\m2_repository\junit\junit\4.12\junit-4.12.jar;E:\m2_repository\org\hamcrest\hamcrest-core\1.3\hamcrest-core-1.3.jar;E:\m2_repository\ch\qos\logback\logback-classic\1.2.3\logback-classic-1.2.3.jar;E:\m2_repository\ch\qos\logback\logback-core\1.2.3\logback-core-1.2.3.jar;E:\m2_repository\org\slf4j\slf4j-api\1.7.25\slf4j-api-1.7.25.jar;E:\m2_repository\org\projectlombok\lombok\1.18.12\lombok-1.18.12.jar" -d mytarget -encoding utf-8 $(find src -name "*.java")
```

 ## 2. 参考 抛开IDE，了解一下javac如何编译
<https://imshuai.com/using-javac#header-6>
