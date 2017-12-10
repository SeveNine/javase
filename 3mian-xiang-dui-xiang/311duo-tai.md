## 多态

#### 概念

```
/*
多态：可以理解为事物存在的多种体现形态。

人：男人，女人

动物：猫，狗。

猫 x = new 猫();

动物 x = new 猫();

1，多态的体现
    父类的引用指向了自己的子类对象。
    父类的引用也可以接收自己的子类对象。
2，多态的前提
    必须是类与类之间有关系。要么继承，要么实现。
    通常还有一个前提：存在覆盖。

3，多态的好处
    多态的出现大大的提高程序的扩展性。

4，多态的弊端：
    虽然提高了扩展性，但是只能使用父类的引用访问父类中的成员。

5，多态的应用

6，多态的出现代码中的特点(多态使用的注意事项)




第二个问题：如何使用子类特有方法。
*/

/*
动物，
猫，狗。
*/

class Cat extends Animal
{
    public void eat()
    {
        System.out.println("吃鱼");
    }
    public void catchMouse()
    {
        System.out.println("抓老鼠");
    }
}


class Dog extends Animal
{
    public void eat()
    {
        System.out.println("吃骨头");
    }
    public void kanJia()
    {
        System.out.println("看家");
    }
}


class Pig extends Animal
{
    public void eat()
    {
        System.out.println("饲料");
    }
    public void gongDi()
    {
        System.out.println("拱地");
    }
}

//-----------------------------------------


class DuoTaiDemo2 
{
    public static void main(String[] args) 
    {
        //Animal a = new Cat();//类型提升。 向上转型。
        //a.eat();

        //如果想要调用猫的特有方法时，如何操作？
        //强制将父类的引用。转成子类类型。向下转型。
        ///Cat c = (Cat)a;
        //c.catchMouse();
        //千万不要出现这样的操作，就是将父类对象转成子类类型。
        //我们能转换的是父类引用指向了自己的子类对象时，该引用可以被提升，也可以被强制转换。
        //多态自始至终都是子类对象在做着变化。
//        Animal a = new Animal();
//        Cat c = (Cat)a;


        /*
        毕姥爷 x = new 毕老师();

        x.讲课();

        毕老师 y = (毕老师)x;


        y.看电影();
        */
        function(new Dog());
        function(new Cat());


    }
    public static void function(Animal a)//Animal a = new Cat();
    {
        a.eat();
        /*
        if(a instanceof Animal)
        {
            System.out.println("haha");
        }
        else 
        */
        if(a instanceof Cat)
        {
            Cat c = (Cat)a;
            c.catchMouse();
        }
        else if(a instanceof Dog)
        {
            Dog c = (Dog)a;
            c.kanJia();
        }


        /*
        instanceof : 用于判断对象的类型。 对象 intanceof 类型(类类型 接口类型)  
        */

    }



}
```

#### 对象中成员的特点

```
class Fu
{
	static int num = 5;
	void method1()
	{
		System.out.println("fu method_1");
	}
	void method2()
	{
		System.out.println("fu method_2");
	}
	static void method4()
	{
		System.out.println("fu method_4");
	}
}


class Zi extends Fu
{
	static int num = 8;
	void method1()
	{
		System.out.println("zi method_1");
	}
	void method3()
	{
		System.out.println("zi method_3");
	}

	static void method4()
	{
		System.out.println("zi method_4");
	}
}
class  DuoTaiDemo4
{
	public static void main(String[] args) 
	{
		
//		Fu f = new Zi();
//
//		System.out.println(f.num);
//
//		Zi z = new Zi();
//		System.out.println(z.num);

		//f.method1();
		//f.method2();
		//f.method3();

		Fu f = new Zi();
		System.out.println(f.num);
		f.method4();

		Zi z = new Zi();
		z.method4();

	
		
/*
在多态中成员函数的特点：
在编译时期：参阅引用型变量所属的类中是否有调用的方法。如果有，编译通过，如果没有编译失败。
在运行时期：参阅对象所属的类中是否有调用的方法。
简单总结就是：成员函数在多态调用时，编译看左边，运行看右边。


在多态中，成员变量的特点：
无论编译和运行，都参考左边(引用型变量所属的类)。


在多态中，静态成员函数的特点：
无论编译和运行，都参考做左边。


*/


//		Zi z = new Zi();
//		z.method1();
//		z.method2();
//		z.method3();
	}
}	

```



