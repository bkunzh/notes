1. 查看当前类的根路径：
```java
    String rootPath = Thread.currentThread().getContextClassLoader().getResource(".").getPath();
    System.out.println("rootPath=" + rootPath);
```
