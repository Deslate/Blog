# Note4.PHb-APP Knowledge Base
## 1.REST接口
https://www.zhihu.com/question/20111251

https://blog.csdn.net/u013063153/article/details/54345117

## 2.AndServer

http://www.cocoachina.com/articles/55237

（我也不知道AndroidStudio是什么毛病，第一个工程怎么弄也不能导入jar。从头开始新建空工程一点一点写之后运行成功。。。）

### 1.AndServer 概述
### 2.ServerBuilder（）
### 3.AndServer中的编程时注解
#### I.@Controller
#### II.@RestController


## 3.inetadderss

InetAddress的实例对象包含以数字形式保存的IP地址，同时还可能包含主机名（如果使用主机名来获取InetAddress的实例，或者使用数字来构造，并且启用了反向主机名解析的功能）。InetAddress类提供了将主机名解析为IP地址（或反之）的方法。

getByName（String host）：根据主机获取对应的InetAddress对象。

getByAddress（byte[] addr）：根据原始IP地址来获取对应的InetAddress对象。

getByAddress(String host, byte[] addr) 
          根据提供的主机名和 IP 地址创建 InetAddress。

getByAddress(byte[] addr) 
          在给定原始 IP 地址的情况下，返回 InetAddress 对象。

getAllByName(String host) 
          在给定主机名的情况下，根据系统上配置的名称服务返回其 IP 地址所组成的数组。

equals(Object obj) 
          将此对象与指定对象比较。

getCanonicalHostName() 
          获取此 IP 地址的完全限定域名。

getHostAddress() 
          返回 IP 地址字符串（以文本表现形式）。

getHostName() 
          获取此 IP 地址的主机名。

getLocalHost() 
          返回本地主机。



https://www.cnblogs.com/albertrui/p/8397600.html