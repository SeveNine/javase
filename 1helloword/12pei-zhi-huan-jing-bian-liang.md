## JDK安装

首先去java官网把食盒自己的JDK安装在电脑上

## 环境变量的配置

首先配置

**PATH**：jdk安装目录下的bin目录（环境变量间用；隔开，位置越在前面越快被找到）。

* 例如C:/Program Files/Java/jdk9.0.1/bin

* 在dos中任意目录运行一个程序（javac）的时候系统在当前目录找不到程序（javac.exe），然后系统就会去path环境变量中寻找。

**JAVA\_HOME**：jdk的安装目录，方便修改与供使用。

* 例如：C:\Program Files\Java\jdk9.0.1

* Eclipse等软件就是通过搜索JAVA\_HOME变量来找到并使用安装好的jdk。

**CLASS\_PATH**：jdk安装目录下的lib子目录中的dt.jar和tools.jar

* 例如：.;C:\Program Files\Java\jdk1.6.0\_21\lib\dt.jar;C:\Program Files\Java\jdk1.6.0\\_21\lib\tools.jar

* 指定类搜索路径，要使用已经编写好的类，前提当然是能够找到它们，JVM就是通过CLASSPATH来寻找类的，而且不同于PATH，JVM会先寻找CLASS\_PATH，然后在本地目录下寻找，所以要先在本地目录找需要在最前面加一个.，最后面不用加；

还可以简化一下：

CLASSPATH= .;%JAVA\_HOME%\lib\dt.jar;%JAVA\_HOME%\lib\tools.jar

JAVA\_HOME = C:\Program Files\Java\jdk9.0.1

PATH  = %JAVA\_HOME%\bin;

%变量名%，为动态获取某一环境变量的值。

因为PATH和CLASSPATH都使用到了JAVA\_HOME，也可以使用绝对路径，两者皆可。

在doc中直接打指令set path=xxx为临时配置环境变量，只在当前窗口有效。

**不要一味的照搬，理解最重要。**

