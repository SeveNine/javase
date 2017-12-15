## 继承

#### 继承的概述

多个类中存在相同属性和行为时，将这些内容抽取到 单独一个类中，那么多个类无需再定义这些属性和行为，只要继承单独的那个

即可。

多个类可以称为子类，单独这个类称为父类或者超 类。

子类可以直接访问父类中的非私有的属性和行为。

通过 extends 关键字让类与类之间产生继承关系。

* class SubDemo extends Demo{} 

继承的出现提高了代码的复用性。

继承的出现让类与类之间产生了关系，提供了多态的前提。

#### 继承的特点

Java只支持单继承，不支持多继承。

* 一个类只能有一个父类，不可以有多个父类。
* class SubDemo extends Demo{} //ok 
* class SubDemo extends Demo1,Demo2...//error 

Java支持多层继承\(继承体系\)

* class A{}
* class B extends A{}
* class C extends B{}

定义继承需要注意：

* 不要仅为了获取其他类中某个功能而去继承
* 类与类之间要有所属\( " is a " \)关系，xx1是xx2的一种。

例如：

```
/*
将学生和工人的共性描述提取出来，单独进行描述，
只要让学生和工人与单独描述的这个类有关系，就可以了。

继承：
1，提高了代码的复用性。
2，让类与类之间产生了关系。有了这个关系，才有了多态的特性。


注意：千万不要为了获取其他类的功能，简化代码而继承。
必须是类与类之间有所属关系才可以继承。所属关系 is a。
class C
{
    void demo1(){}
}


class A extends C
{
    //void demo1(){}
    void demo2(){}
}

class B extends C
{
    //void demo1(){}
    void demo3(){}
}

Java语言中：java只支持单继承，不支持多继承。

因为多继承容易带来安全隐患:当多个父类中定义了相同功能，
但功能内容不同时，子类对象不确定要运行哪一个。
但是java保留这种机制。并用另一种体现形式来完成表示。多实现。


java支持多层继承。也就是一个继承体系

如何使用一个继承体系中的功能呢？

想要使用体系，先查阅体系父类的描述，因为父类中定义的是该体系中共性功能。
通过了解共性功能，就可以知道该体系的基本功能。
那么这个体系已经可以基本使用了。
那么在具体调用时，要创建最子类的对象，为什么呢？
一是因为有可能父类不能创建对象，
二是创建子类对象可以使用更多的功能，包括基本的也包括特有的。


简单一句话：查阅父类功能，创建子类对象使用功能。


下面例子就存在安全隐患
class A
{
    void show()
    {
        System.out.println("a");
    }
}
class B
{
    void show()
    {
        System.out.println("b");
    }
}

class C extends A,B
{}

C c = new C();
c.show();
不知道show哪个。


聚集：has a

聚合：比如球员聚合成球队。

组合：比如手是人身体的组成部分。




*/

class Person
{
    String name;
    int age;

}
class Student extends Person
{
        void study()
    {
        System.out.println("good study");
    }
}

class Worker extends Person
{
    void work()
    {
        System.out.println("good work");
    }
}



class ExtendsDemo 
{
    public static void main(String[] args) 
    {
        Student s = new Student();
        s.name = "zhagnsan";
    }
}
```

#### 子父类中变量的特点

```
/*
子父类出现后，类成员的特点：

类中成员：
1，变量。
2，函数。
3，构造函数。

1,变量
如果子类中出现非私有的同名成员变量时，
子类要访问本类中的变量，用this
子类要访问父类中的同名变量，用super。

super的使用和this的使用几乎一致。
this代表的是本类对象的引用。
super代表的是父类对象的引用。

*/

class Fu 
{
    public int num = 4;
}

class Zi extends Fu
{
    int num = 5;
    void show()
    {
        System.out.println(this.num+"+"+super.num);
    }
}

class  ExtendsDemo2
{
    public static void main(String[] args) 
    {
        Zi z = new Zi();
        z.show();
        //System.out.println(z.num+"...."+z.num);
    }
}
```

#### 子父类中函数的特点（重写） \(Override\)

```
/*
2,子父类中的函数。

当子类出现和父类一模一样的函数时，
当子类对象调用该函数，会运行子类函数的内容。
如同父类的函数被覆盖一样。

这种情况是函数的另一个特性：重写(覆盖)


当子类继承父类，沿袭了父类的功能，到子类中，
但是子类虽具备该功能，但是功能的内容却和父类不一致，
这时，没有必要定义新功能，而是使用覆盖特性，保留父类的功能定义，并重写功能内容。


覆盖：
1，子类覆盖父类，必须保证子类权限大于等于父类权限，才可以覆盖，否则编译失败。

2，静态只能覆盖静态。


记住：
重载：只看同名函数的参数列表。
重写：子父类方法要一模一样。
*/

class Fu
{
    void show()
    {
        System.out.println("fu show");
    }
    void speak()//以前说vb
    {
        System.out.println("vb");
    }
}

class Zi extends Fu
{
    void speak()//现在说java
    {
        System.out.println("java");
    }
    void show()
    {
        System.out.println("zi show");
    }
}


class ExtendsDemo3 
{
    public static void main(String[] args) 
    {
        Zi z = new Zi();
        z.speak();

    }
}


class Tel//旧电话本
{
    void show()
    {
        System.out.println("number");
    }

}

class NewTel extends Tel//新电话本
{
    void show()
    {
        //System.out.println("number");
        super.show();
        System.out.println("name");
        System.out.println("pic");
    }
}
```

#### 子父类中的构造函数

```
/*
3，子父类中的构造函数。

在对子类对象进行初始化时，父类的构造函数也会运行，
那是因为子类的构造函数默认第一行有一条隐式的语句 super();
super():会访问父类中空参数的构造函数。而且子类中所有的构造函数默认第一行都是super();

为什么子类一定要访问父类中的构造函数。

因为父类中的数据子类可以直接获取。所以子类对象在建立时，需要先查看父类是如何对这些数据进行初始化的。
所以子类在对象初始化时，要先访问一下父类中的构造函数。
如果要访问父类中指定的构造函数，可以通过手动定义super语句的方式来指定。

注意：super语句一定定义在子类构造函数的第一行。



子类的实例化过程。

结论：
子类的所有的构造函数，默认都会访问父类中空参数的构造函数。
因为子类每一个构造函数内的第一行都有一句隐式super();

当父类中没有空参数的构造函数时，子类必须手动通过super语句形式来指定要访问父类中的构造函数。

当然：子类的构造函数第一行也可以手动指定this语句来访问本类中的构造函数。
子类中至少会有一个构造函数会访问父类中的构造函数。
*/
class Fu //extends Object
{
    int num ;
    Fu()
    {
        //super();这个里面继承的是object
        num= 60;
        System.out.println("fu run");
    }
    Fu(int  x)
    {
        System.out.println("fu ...."+x);
    }

}

class Zi extends Fu
{
    Zi()
    {

        super();  
        //super(4);
        System.out.println("zi run");
    }
    Zi(int x)
    {
        this();
        //super();
        //super(3);如果父类中没有空参数构造函数可以手动指定
        System.out.println("zi..."+x);
    }
}

class  ExtendsDemo4
{
    public static void main(String[] args) 
    {
        Zi z = new Zi(0);
        System.out.println(z.num);
    }
}

/*
class Person
{
    private  String name;
    Person(String name)
    {
        this.name = name;
    }

    void show(){}
}
class Student extends Person
{
    Student(String name)
    {
        super(name);//直接调用父类的构造函数
    }
    void method()
    {
        super.show();
    }
}
*/
```





