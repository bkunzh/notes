1. 基本配置
**log4j.properties**(放到classpath下，比如src/test/resources)
```
log4j.rootLogger=DEBUG, stdout

log4j.category.org.apache.commons.beanutils=INFO

log4j.appender.stdout=org.apache.log4j.ConsoleAppender

log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=%d %p [%c] - %m%n

```
> 更多配置请google

2. maven配置
```
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>slf4j-api</artifactId>
			<version>1.7.18</version>
		</dependency>
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>slf4j-log4j12</artifactId>
			<version>1.7.18</version>
			<scope>test</scope>
		</dependency>
```

99. 一个疑问 unknown ??

配置`log4j.category.logger`和`log4j.logger`有区别吗？为什么前者可以关掉apache工具的调试日志，后者不行，如下：
```
#关闭apache beanutils的调试信息
log4j.category.org.apache.commons.beanutils=INFO
#以下不行，不知道为什么。 log4j.category vs log4j.logger
#log4j.org.apache.commons.beanutils=INFO
```
> 暂时没搜到有效资料，有时间可以研究下why
见<https://github.com/bkunzhang/potato-orm/blob/16c967cd52/src/test/resources/log4j.properties>配置，实验可以以这个为依据（这里指向某个提交历史）