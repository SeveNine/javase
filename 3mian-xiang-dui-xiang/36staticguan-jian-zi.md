## static\(静态\)关键字

static关键字：

* 用于修饰成员（成员变量和成员函数）

被修饰后的成员具备以下特点：

* 随着类的加载而加载

* 优先于对象存在

* 被所有对象所共享

* 可以直接被类名调用

  使用注意：

* 静态方法只能访问静态成员

* 静态方法中不可以写this，super关键字

* 主函数是静态的

```
/*
静态：static。
用法：是一个修饰符，用于修饰成员(成员变量，成员函数).
当成员被静态修饰后，就多了一个调用方式，除了可以被对象调用外，
还可以直接被类名调用。类名.静态成员。

static特点：
1，随着类的加载而加载。
   也就说：静态会随着类的消失而消失。说明它的生命周期最长。

2，优先于的对象存在
明确一点：静态是先存在。对象是后存在的。

3，被所有对象所共享
4，可以直接被类名所调用。

实例变量和类变量的区别：
1，存放位置。
    类变量随着类的加载而存在于方法区中。
    实例变量随着对象的建立而存在于堆内存中。
2，生命周期：
    类变量生命周期最长，随着类的消失而消失。
    实例变量生命周期随着对象的消失而消失。

静态使用注意事项：
1，静态方法只能访问静态成员。
    非静态方法既可以访问静态也可以访问非静态。
2，静态方法中不可以定义this，super关键字。
    因为静态优先于对象存在。所以静态方法中不可以出现this。
3，主函数是静态的。

静态有利有弊
利处：对对象的共享数据进行单独空间的存储，节省空间。没有必要每一个对象中都存储一份。
    可以直接被类名调用。
弊端：生命周期过长。
      访问出现局限性。(静态虽好，只能访问静态。)
*/

class Person
{
    String name;//成员变量，实例变量。
    static String country = "CN";//静态的成员变量，类变量。
    public static void show()
    {
        System.out.println("::::");
        this.haha();
    }
    public void haha()
    {}
}

class  StaticDemo
{
    public static void main(String[] args) 
    {
        Person p = new Person();
        Person.show();
    }
}
```

#### 什么时候使用static关键字

```
/*
什么使用静态？

要从两方面下手：
因为静态修饰的内容有成员变量和函数。
什么时候定义静态变量(类变量)呢？
当对象中出现共享数据时，该数据被静态所修饰。
对象中的特有数据要定义成非静态存在于堆内存中。

什么时候定义静态函数呢？

当功能内部没有访问到肺静态数据(对象的特有数据)，
那么该功能可以定义成静态的。

*/
class Person
{
	String name;
	static String country = "cn";
	public  static void show()
	{
		System.out.println(contry+"haha");	
	}

}


class  
{
	public static void main(String[] args) 
	{
		Person p = new Person();
		p.show();
		//Person.show();
	}

}

```

#### main函数

```
/*
public static void main(String[] args) 

主函数：是一个特殊的函数。作为程序的入口，可以被jvm调用。

主函数的定义：
public：代表着该函数访问权限是最大的。
static：代表主函数随着类的加载就已经存在了。
void：主函数没有具体的返回值。
main：不是关键字，但是是一个特殊的单词，可以被jvm识别。
（String[] arr）:函数的参数，参数类型是一个数组，该数组中的元素是字符串。字符串类型的数组。

主函数是固定格式的：jvm识别。

jvm在调用主函数时，传入的是new String[0];
*/

class MainDemo 
{
    public static void main(String[] args)//new String[]
    {
        String[] arr = {"hah","hhe","heihei","xixi","hiahia"};

        MainTest.main(arr);
        //往下面的主函数传值，开发没人写两个入口
    }
}

//String[] args = new String[3];
//String[] args = null;


class MainTest
{
    public static void main(String[] args)
    {
        for(int x=0; x<args.length; x++)
            System.out.println(args[x]);
    }
}
```



