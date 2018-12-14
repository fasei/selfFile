# Android Studio解决Java程序输出中文乱码
 

经查阅资料，发现需要手动在build.gradle中添加代码

* 新版 
```
tasks.withType(JavaCompile) { options.encoding = UTF-8 }

```


* 旧版，以gradle-1.12为例
```
tasks.withType(Compile) { options.encoding = UTF-8 }

```