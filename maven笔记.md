1. 有些中央仓库没有的jar包，maven会报错，所以要把jar包安装到本地仓库，如下
	- 1）通过cmd输入命令
		mvn install:install-file -Dfile=memcached-2.6.6.jar -DgroupId=com.danga -DartifactId=memcached -Dversion=2.6.6 -Dpackaging=jar
		（如果jar包当前目录有pom.xml，会读取它，可能会报错，可以把jar包复制到空目录，再执行命令）
	- 2）通过eclipse：import->install or deploy an artifact to a Maven repository->找到jar包位置，输入groupId、artifactId、version
	
2. maven设置默认JDK版本，`settings.xml的<profiles>元素下`设置
```xml
    <profile>
      <id>development</id>
      <activation>
        <jdk>1.8</jdk>
        <activeByDefault>true</activeByDefault>
      </activation>
      <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
        <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
      </properties>
    </profile>
```
3. maven镜像（settings.xml）
```XML
    <mirror>
      <id>alimaven</id>
      <name>aliyun maven</name>
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
      <mirrorOf>central</mirrorOf>
    </mirror>
    <mirror>
      <id>central</id>
      <name>Maven Repository Switchboard</name>
      <url>http://repo1.maven.org/maven2/</url>
      <mirrorOf>central</mirrorOf>
    </mirror>
    <mirror>
      <id>repo2</id>
      <mirrorOf>central</mirrorOf>
      <name>Human Readable Name for this Mirror.</name>
      <url>http://repo2.maven.org/maven2/</url>
    </mirror>
    <mirror>
      <id>ibiblio</id>
      <mirrorOf>central</mirrorOf>
      <name>Human Readable Name for this Mirror.</name>
      <url>http://mirrors.ibiblio.org/pub/mirrors/maven2/</url>
    </mirror>
    <mirror>
      <id>jboss-public-repository-group</id>
      <mirrorOf>central</mirrorOf>
      <name>JBoss Public Repository Group</name>
      <url>http://repository.jboss.org/nexus/content/groups/public</url>
    </mirror>
```
也可以在pom.xml配置spring相关 unknown ??
```xml
<repository>
    <id>spring-repo</id>
    <name>Spring Repository</name>
    <url>https://repo.spring.io/release</url>
</repository>
<repository>
    <id>spring-milestone</id>
    <name>Spring Milestone Repository</name>
    <url>https://repo.spring.io/milestone</url>
</repository>
<repository>
    <id>spring-snapshot</id>
    <name>Spring Snapshot Repository</name>
    <url>https://repo.spring.io/snapshot</url>
    <snapshots>
        <enabled>true</enabled>
    </snapshots>
</repository>
```
