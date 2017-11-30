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

#### 静态的应用-工具类

静态的应用。

每一个应用程序中都有共性的功能，

可以将这些功能进行抽取，独立封装。

以便复用。

虽然可以通过建立ArrayTool的对象使用这些工具方法，对数组进行操作。

发现了问题：

1，对象是用于封装数据的，可是ArrayTool对象并未封装特有数据。

2，操作数组的每一个方法都没有用到ArrayTool对象中的特有数据。

这时就考虑，让程序更严谨，是不需要对象的。

可以将ArrayTool中的方法都定义成static的。直接通过类名调用即可。

将方法都静态后，可以方便于使用，但是该类还是可以被其他程序建立对象的。

为了更为严谨，强制让该类不能建立对象。

可以通过将构造函数私有化完成。

接下来，将ArrayTool.class文件发送给其他人，其他人只要将该文件设置到classpath路径下，就可以使用该工具类。

但是，很遗憾，该类中到底定义了多少个方法，对方去不清楚。因为该类并没有使用说明书。

开始制作程序的说明书。java的说明书通过文档注释来完成。

#### 文档注释

```
/**
这是一个可以对数组进行操作的工具类，该类中提供了，获取最值，排序等功能。
@author 张三
@version V1.1

*/

//javadoc -d myhelp -author -version ArrayTool.java

public class ArrayTool
{
    /**
    空参数构造函数。
    */
    private ArrayTool(){}

    /**
    获取一个整形数组中的最大值。
    @param arr 接收一个int类型的数组。
    @return 会返回一个该数组中最大值。
    */
    public static int getMax(int[] arr)
    {
        int max = 0;
        for(int x=1; x<arr.length; x++)
        {
            if(arr[x]>arr[max])
                max = x;
        }
        return arr[max];
    }

    /**
    获取一个整形数组中的最小值。
    @param arr 接收一个int类型的数组。
    @return 会返回一个该数组中最小值。
    */
    public static int getMin(int[] arr)
    {
        int min = 0;
        for(int x=1; x<arr.length; x++)
        {
            if(arr[x]<arr[min])
                min = x;
        }
        return arr[min];
    }
    /**
    给int数组进行选择排序。
    @param arr 接收一个int类型的数组。
    */
    public static void selectSort(int[] arr)
    {
        for (int x=0; x<arr.length-1 ; x++ )
        {
            for(int y=x+1; y<arr.length; y++)
            {
                if(arr[x]>arr[y])
                {
                    swap(arr,x,y);
                }
            }
        }
    }
    /**
    给int数组进行冒泡排序。
    @param arr 接收一个int类型的数组。
    */
    public static void bubbleSort(int[] arr)
    {
        for (int x=0; x<arr.length-1 ; x++ )
        {
            for(int y=0; y<arr.length-x-1; y++)
            {
                if(arr[y]>arr[y+1])
                {
                    swap(arr,y,y+1);
                }
            }
        }
    }
    /**
    给数组中元素进行位置的置换。
    @param arr  接收一个int类型的数组。
    @param a 要置换的位置 
    @param b 要置换的位置 
    */
    private  static void swap(int[] arr,int a,int b)
    {
        int temp = arr[a];
        arr[a] = arr[b];
        arr[b] = temp;
    }
    /**
    用于打印数组中的元素。打印形式是：[elemet1, element2, ...]
    */
    public static void printArray(int[] arr)
    {
        System.out.print("[");
        for(int x=0; x<arr.length; x++)
        {
            if(x!=arr.length-1)
                System.out.print(arr[x]+", ");
            else
                System.out.println(arr[x]+"]");
        }
    }
}



/*
一个类中默认会有一个空参数的构造函数，
这个默认的构造函数的权限和所属类一致。
如果类被public修饰，那么默认的构造函数也带public修饰符。
如果类没有被public修饰，那么默认的构造函数，也没有public修饰。

默认构造构造函数的权限是随着的类的变化而变化的。
*/
```

#### 静态代码块

```
/*
静态代码块。
格式：
static
{
    静态代码块中的执行语句。
}

特点：随着类的加载而执行，只执行一次,并优先于主函数。
用于给类进行初始化的。

*/

class StaticCode
{
    int num = 9;
    StaticCode()
    {
        System.out.println("b");
    }

    static
    {
        System.out.println("a");
    }
    {
        System.out.println("c"+this.num);
    }

    StaticCode(int x)
    {
        System.out.println("d");
    }
    public static void show()
    {
        System.out.println("show run");
    }
}

class StaticCodeDemo 
{
    static
    {
        //System.out.println("b");
    }
    public static void main(String[] args) 
    {
        new StaticCode(4);//a c d 
        //new StaticCode();
        //new StaticCode();
        //System.out.println("over");
        //StaticCode.show();
        //StaticCode s = null;
        //s = new StaticCode();

        //StaticCode.show();


    }
    static
    {
        ///System.out.println("c");
    }
}
//d:\>java0217\day06>java StaticCodeDemo
//b c a over
```

#### 对象的初始化过程

```
class Person
{
    private Person(){}
    private String name = "hah";
    private int age;
    private static  String country = "cn";
    Person(String name,int age)
    {
        this.name = name;
        this.age = age;
    }

    {
        System.out.println(name+".."+age);
    }
    public void setName(String name)
    {
        this.name = name;
    }

    public void speak()
    {
        System.out.println(this.name+"..."+this.age);
    }

    public static void  showCountry()
    {
        System.out.println("country="+Person.country);
        Person.method();
    }
    public static void method()
    {
        System.out.println("method run");
    }

}

class  PersonDemo
{
    public static void main(String[] args) 
    {
        Person p = new Person("zhangsan",20);
        p.setName("lisi");
        new Person();
    }
}
/*
Person p = new Person("zhangsan",20);

该句话都做了什么事情？
1，因为new用到了Person.class.所以会先找到Person.class文件并加载到内存中。
2，执行该类中的static代码块，如果有的话，给Person.class类进行初始化。
3，在堆内存中开辟空间，分配内存地址。
4，在堆内存中建立对象的特有属性。并进行默认初始化。
5，对属性进行显示初始化。
6，对对象进行构造代码块初始化。
7，对对象进行对应的构造函数初始化。
8，将内存地址付给栈内存中的p变量。

*/
```

#### 单例设计模式

```
/*
设计模式：解决某一类问题最行之有效的方法。
java中23种设计模式：
单例设计模式：解决一个类在内存只存在一个对象。


想要保证对象唯一。
1，为了避免其他程序过多建立该类对象。先禁止其他程序建立该类对象
2，还为了让其他程序可以访问到该类对象，只好在本类中，自定义一个对象。
3，为了方便其他程序对自定义对象的访问，可以对外提供一些访问方式。

这三部怎么用代码体现呢？
1，将构造函数私有化。
2，在类中创建一个本类对象。
3，提供一个方法可以获取到该对象。



对于事物该怎么描述，还怎么描述。
当需要将该事物的对象保证在内存中唯一时，就将以上的三步加上即可。


*/

class Single
{


    private  Single(){}

    private static Single s = new Single();

    public static  Single getInstance()
    {
        return s;
    }
}


class SingleDemo 
{
    public static void main(String[] args) 
    {
        Single s1 = Single.getInstance();
        Single s2 = Single.getInstance();

        s1.setNum(23);

        System.out.println(s2.getNum());

    }
}



class Student
{
    private int age;


    private static Student s = new Student();
    private Student(){}
    public static Student getStudent()
    {
        return s;
    }



    public void setAge(int age)
    {
        this.age = age;
    }
    public int getAge()
    {
        return age;
    }
}
```

#### 饿汉式与懒汉式

```
/*
这个是先初始化对象。
称为：饿汉式。

Single类一进内存，就已经创建好了对象。
class Single
{
    private static Single s = new Single();
    private Single(){}
    public static Single getInstance()
    {
        return s;
    }
}
*/

//对象是方法被调用时，才初始化，也叫做对象的延时加载。称为：懒汉式。
//Single类进内存，对象还没有存在，只有调用了getInstance方法时，才建立对象。
class Single
{
    private static Single s = null;
    private Single(){}
    public static Single getInstance()
    {
        if(s==null)
        {
            synchronized(Single.class)
            {                
                if(s==null)
                    s = new Single();
            }
        }
        return s;
    }
}

//记录原则：定义单例，建议使用饿汉式。

class  
{
    public static void main(String[] args) 
    {
        System.out.println("Hello World!");
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



