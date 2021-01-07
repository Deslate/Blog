# Android/AS异常处理纪实
## 1. Attempt to invoke virtual method xxxxxxxx on a null object reference

会出现问题的API版本：不完全统计：API-29

问题细节：ancivity extend AppCompatActivity implement onClickListener

报错来源：Android运行时LogCat打印

问题原因：尝试调用方法在一个空的对象上；findViewById方法无效。

问题解决：在findViewById之前先确认view：
```java
View view = View.inflate( this, (R.layout.activity_main), null);
```
## 2.NetworkOnMainThreadException

报错来源：编译时

问题原因：顾名思义，网络请求不可以在主线程中开启

解决：当然是开一个线程来处理啦。

## 3.java.net.BindException: Address already in use

这不是个报错。

## 4.Can't create handler inside thread that has not called Looper.prepare()

典型的不能在子线程做更新ui、做activity跳转的异常。 

获取到信息做判断后直接做了跳转actitvity的操作/更新UI也是不可以的！。。。？？？


## 5.org.apache.http.***类无法引用

问题来源于android版本升级之后不支持使用httpsclient。API大于22的都要在build.gradle，buildtool version后面注明：
```java
useLibrary'org.apache.http.legacy'
```

## 6.android.os.FileUriExposedException: file:///storage/emulated/0/photo.jpg exposed beyond app through ClipData.Item.getUri()

