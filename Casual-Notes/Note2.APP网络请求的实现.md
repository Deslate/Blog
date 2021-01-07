# APP网络请求的实现 #

## 1. 网络请求过程 ##

[reference](https://www.jianshu.com/p/8a40f99da882)

### 1. DNS ###

Domain Name System（域名系统），互联网上作为域名和IP地址相互映射的一个分布式数据库。

#### MAC 地址 ####

![MAC](https://upload-images.jianshu.io/upload_images/3333422-15df189e79afb75b.png?imageMogr2/auto-orient/strip|imageView2/2/w/500/format/webp)

未知，通过ARP协议获取

#### IP 地址 ####

已知，如 202.201.112.232

### 2. HTTP请求 ###

#### 端口 ####

0到65535之间的一个整数，决定信息分配给哪一个应用

#### UDP ####

在数据包中插入一段数据用来标记端口信息，发送，不管接收

简单，可靠性差

#### TCP ####

```text
浏览器：你好服务器，我是 浏览器A。
服务器：你好 浏览器A，我是 服务器B。
浏览器：服务器B 你好。
```

![三次握手](https://upload-images.jianshu.io/upload_images/3333422-b9c17e41f34fd4fa.png?imageMogr2/auto-orient/strip|imageView2/2/w/482/format/webp)

```text
主动结束方：你好，我的数据发送完毕了，我要进入准备断开的状态了。（此时它虽然不再发送数据了，但是可以接受数据）
另一方：我知道了，我还没有发送完毕的，你等着吧。
另一方：我也发送完毕了，可以断开链接了。（此时它也进入准备断开的状态）
主动结束方：好的，那断开吧。
```

![四次挥手](https://upload-images.jianshu.io/upload_images/3333422-b751ca9b4892959e.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/883/format/webp)

### 3. 服务器端 ###

![Struts 2 网页应用程序框架](https://upload-images.jianshu.io/upload_images/3333422-307ca7eb5ca07f82.png?imageMogr2/auto-orient/strip|imageView2/2/w/641/format/webp)

## 2. 网络请求 for Android ##

[reference](http://blog.oneapm.com/apm-tech/344.html)

### HttpURLConnection ###

[HttpURLConnection | Android Developers](https://developer.android.com/reference/java/net/HttpURLConnection)

public abstract class HttpURLConnection
extends URLConnection

```java
URL url = new URL("http://www.android.com/");
   HttpURLConnection urlConnection = (HttpURLConnection) url.openConnection();
   try {
     InputStream in = new BufferedInputStream(urlConnection.getInputStream());
     readStream(in);
   } finally {
     urlConnection.disconnect();
   }
```

#### xUtils ####

[xUtils](https://www.jianshu.com/p/4576dd6ee411)是目前功能比较完善的一个Android开源框架

### HttpClient ###

hahaha
