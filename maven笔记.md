1. 有些中央仓库没有的jar包，maven会报错，所以要把jar包安装到本地仓库，如下
	- 1）通过cmd输入命令
		mvn install:install-file -Dfile=memcached-2.6.6.jar -DgroupId=com.danga -DartifactId=memcached -Dversion=2.6.6 -Dpackaging=jar
		（如果jar包当前目录有pom.xml，会读取它，可能会报错，可以把jar包复制到空目录，再执行命令）
	- 2）通过eclipse：import->install or deploy an artifact to a Maven repository->找到jar包位置，输入groupId、artifactId、version
	
