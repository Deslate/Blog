# Note3.MacOS上的从零开始 #
macOS 上几种开发环境的配置记录
## 1.Java SE 1.8 ##
### 1.1.Java版本选择
新 acBook 有足够的磁盘空间供我挥霍，所以这次我选择了专业的Android开发环境 Android Studio 3。Android 3 新增了对 Java 8 的支持（以前只支持到Java6）。所以本次选择安装 Java SE 8 update 231。
### 1.2.着手搭建 ##
[官网下载](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)之后安装即可。检查是否安装成功：

```command
java -version
```

与Windows相同，mac上需要配置环境变量。Mac上配置环境变量的方法：首先，终端输入

```command
/usr/libexec/java_home
```

返回得到Java-Home的路径，留作记录，开始配置：

```command
sudo vim /etc/profile 
```

然后可能需要登录密码，然后得到：

```command
# System-wide .profile for sh(1)
  
if [ -x /usr/libexec/path_helper ]; then
        eval `/usr/libexec/path_helper -s`
fi

if [ "${BASH-no}" != "no" ]; then
        [ -r /etc/bashrc ] && . /etc/bashrc
fi
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
Type  :qa!  and press <Enter> to abandon all changes and exit Vim
```

按下i键，进入insert模式：

```command
# System-wide .profile for sh(1)
  
if [ -x /usr/libexec/path_helper ]; then
        eval `/usr/libexec/path_helper -s`
fi

if [ "${BASH-no}" != "no" ]; then
        [ -r /etc/bashrc ] && . /etc/bashrc
fi
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
-- INSERT -- W10: Warning: Changing a readonly file
```
在其中添加：

```command
JAVA_HOME="/Library/Java/JavaVirtualMachines/jdk1.8.0_231.jdk/Contents/Home"
export JAVA_HOME
CLASS_PATH="$JAVA_HOME/lib"
PATH=".$PATH:$JAVA_HOME/bin"
```

使其变成：

```command
# System-wide .profile for sh(1)
  
if [ -x /usr/libexec/path_helper ]; then
        eval `/usr/libexec/path_helper -s`
fi

if [ "${BASH-no}" != "no" ]; then
        [ -r /etc/bashrc ] && . /etc/bashrc
fi
JAVA_HOME="/Library/Java/JavaVirtualMachines/jdk1.8.0_231.jdk/Contents/Home"
export JAVA_HOME
CLASS_PATH="$JAVA_HOME/lib"
PATH=".$PATH:$JAVA_HOME/bin"
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
-- INSERT -- W10: Warning: Changing a readonly file
```

然后按Esc键，进入保存：输入

```command
:wq! 
```

回车即可保存。要想立即生效：

```command
source /etc/profile
```

回车，运行profile指令，不会有提示。检查环境：

```command
echo $JAVA_HOME
```

返回这样一个路径

```command
/Library/Java/JavaVirtualMachines/jdk1.8.0_231.jdk/Contents/Home
yanghaowendeMacBook-Pro:~ yanghaowen$ 
```

就说明配置成功。

## 2.从 Eclipse+ADT+SDK 到 Android Studio
诚然，AndroidStudio的画风和舒适度都要比Eclipse强上不知道多少倍，但Eclipse+ADT+SDK的环境搭建的确可以帮我们更好的了解Android环境的内部结构，而且运行速度要比AndroidStudio高。不过这次要效率优先，而且内存、CPU、硬盘容量都比之前有了很大提升，不必担心运行速度，于是选择AndroidStudio 3。

### 2.1下载安装 Android Studio ###

[官网下载](https://developer.android.google.cn/studio/)

### 2.2内置Git工具
![](https://github.com/PolarisStudio/Deslate_notes/blob/master/Referring/屏幕快照%202019-10-27%20下午1.51.54.png?raw=true)

## 3.Eclipse安装
作为备用编译器，没什么好说的，到官网上下载下载器。注意如果下载太慢，换一个国内的镜像。用下载器下载eclipse时开着美国的VPN比较好。下载下来之后写一个helloworld确认能用就好了。
![haha](https://github.com/PolarisStudio/Deslate_notes/blob/master/Referring/屏幕快照%202019-10-27%20下午1.27.28.png?raw=true)

## 4.VScode安装及Git配置

## 5.VisualStudio for Mac 尝鲜

## 6.VMware:免费获取昂贵的虚拟机软件

## 7.安装 CentOS：用 Linux 开车