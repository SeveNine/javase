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


