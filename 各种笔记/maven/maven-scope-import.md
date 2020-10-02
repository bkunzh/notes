## 使用import scope解决maven继承（单）问题
想必大家在做SpringBoot应用的时候，都会有如下代码：

```xml
<parent>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-parent</artifactId>
	<version>1.3.3.RELEASE</version>
</parent>
```

继承一个父模块，然后再引入相应的依赖

假如说，我不想继承，或者我想继承多个，怎么做？

import scope依赖能解决这个问题。你可以把dependencyManagement放到单独的专门用来管理依赖的pom中，然后在需要使用依赖的模块中通过import scope依赖，就可以引入dependencyManagement。例如可以写这样一个用于依赖管理的pom：

```xml
<project>
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.test.sample</groupId>
	<artifactId>base-parent1</artifactId>
	<packaging>pom</packaging>
	<version>1.0.0-SNAPSHOT</version>
	<dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>junit</groupId>
                <artifactId>junit</artifactId>
                <version>4.12</version>
            </dependency>
            <dependency>
                <groupId>cn.hutool</groupId>
                <artifactId>hutool-all</artifactId>
                <version>4.6.17</version>
            </dependency>
        </dependencies>
    </dependencyManagement>
</project>
```

然后我就可以通过非继承的方式来引入这段依赖管理配置

```xml
<dependencyManagement>
	<dependencies>
		<dependency>
			<groupId>com.test.sample</groupId>
			<artifactid>base-parent1</artifactId>
			<version>1.0.0-SNAPSHOT</version>
			<type>pom</type>
			<scope>import</scope>
		</dependency>
	</dependencies>
</dependencyManagement>
 
 <dependencies>
    <dependency>
        <groupId>junit</groupId>
        <artifactid>junit</artifactId>
    </dependency>
    <dependency>
        <groupId>cn.hutool</groupId>
        <artifactId>hutool-all</artifactId>
    </dependency>
</dependencies>
```

注意：import scope只能用在dependencyManagement里面

这样，父模块的pom就会非常干净，由专门的packaging为pom来管理依赖，也契合的面向对象设计中的单一职责原则。此外，我们还能够创建多个这样的依赖管理pom，以更细化的方式管理依赖。这种做法与面向对象设计中使用组合而非继承也有点相似的味道。

那么，如何用这个方法来解决SpringBoot的那个继承问题呢？

配置如下：

<dependencyManagement>
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-dependencies</artifactId>
			<version>1.3.3.RELEASE</version>
			<type>pom</type>
			<scope>import</scope>
		</dependency>
	</dependencies>
</dependencyManagement>
 
<dependencies>
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-web</artifactId>
	</dependency>
</dependencies>

这样配置的话，自己的项目里面就不需要继承SpringBoot的module了，而可以继承自己项目的module了。

## code
java-study/code/maven/maven-scope-import

## 参考
https://blog.csdn.net/mn960mn/article/details/50894022