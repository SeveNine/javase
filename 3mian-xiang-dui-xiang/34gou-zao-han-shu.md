## 构造函数

特点：

* 函数名与类名相同
* 不用定义返回值类型
* 不可以写return语句

作用： 给对象进行初始化。

注意：

* 默认构造函数的特点。 
* 多个构造函数是以重载的形式存在的。

```
/*
对象一建立就会调用与之对应的构造函数。
构造函数的小细节：
当一个类中没有定义构造函数时，那么系统会默认给该类加入一个空参数的构造函数。

当在类中自定义了构造函数后，默认的构造函数就没有了。

构造函数和一般函数在写法上有不同。

在运行上也有不同。
构造函数是在对象一建立就运行。给对象初始化。
而一般方法是对象调用才执行，给是对象添加对象具备的功能。

一个对象建立，构造函数只运行一次。
而一般方法可以被该对象调用多次。

什么时候定义构造函数呢？
当分析事物时，该事物存在具备一些特性或者行为，那么将这些内容定义在构造函数中。
*/

class Person
{
    private String name;
    private int age;

    /*
    构造代码块。
    作用：给对象进行初始化。
    对象一建立就运行，而且优先于构造函数执行。
    和构造函数的区别：
    构造代码块是给所有对象进行统一初始化，
    而构造函数是给对应的对象初始化。

    构造代码快中定义的是不同对象共性的初始化内容。

    */
    {
        cry();
    }

    Person()
    {
        System.out.println("A: name="+name+",,age="+age);

    }
    //构造函数的重载，带自己起的名字的人
    Person(String n)
    {
        name = n;
        System.out.println("B: name="+name+",,age="+age);

        //cry();构造代码块中已经有了

    }
    /*
    public void setName(String n)
    {
        name  = n;
    }
    public String getName()
    {
        return name;
    }
    */
    Person(String n,int a)
    {
        name = n;
        age = a;
        System.out.println("C: name="+name+",,age="+age);
        //cry();
    }

    public void cry()
    {

        System.out.println("cry......");
    }
}

class  PersonDemo2
{
    public static void main(String[] args) 
    {
        Person p1 = new Person();



        Person p2 = new Person("lisi");

        //System.out.println(p2.getName());

        //Person p3 = new Person("wnagu",10);


    }
}
```



