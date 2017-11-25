## 注释

注释对于增加程序可读性非常重要。

单行注释：//内容

多行注释：/\*内容\*/

文档注释：/\*\*内容\*/

举例说明：

```java
/**
作者:旺财
版本：V1.0
功能：这个类是用于输出hello world。
*/
public class HelloWorld    //这是我的第一个类，叫HelloWorld，应与.java文件名同名，否则会报错，因为有public修饰符
{  
	/*
	main函数可以保证该类的独立运行。
	它是程序的入口。
	它会被JVM所调用。
	*/
	public static void main (String[] args)

	{

		System.out.println("HelloWorld");    //输出语句，打印小括号中的内容

	}
}
```



