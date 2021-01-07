# Start Spring Boot <small>with IDEA</small>

## 环境

### Java

### Maven

以mac为例, 下载 [apache-maven-3.6.3-bin.tar.gz](http://mirror.bit.edu.cn/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz) (Windows 下载[apache-maven-3.6.3-bin.zip](http://mirror.bit.edu.cn/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip))，解压至特定路径，如`tar -xzvf .../apache-maven-3.6.3-bin.tar -C ~/maven`, 解压后为`apache-maven-3.6.3`的文件夹，然后修改环境变量(以下为mac中的操作): `vim ~/.bash_profile`中添加：

```
M2_HOME=解压后的绝对路径
export M2_HOME
```

`:wq`之后`source ~/.bash_profile`使配置文件生效，输入`man -v`检查安装是否成功：

```
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
Maven home: /Users/yanghaowen/Maven/apache-maven-3.6.3
Java version: 1.8.0_231, vendor: Oracle Corporation, runtime: /Library/Java/JavaVirtualMachines/jdk1.8.0_231.jdk/Contents/Home/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "mac os x", version: "10.15.3", arch: "x86_64", family: "mac"
```

### IDEA

