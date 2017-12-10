## 接口

#### 定义

```
/*
接口：初期理解，可以认为是一个特殊的抽象类
    当抽象类中的方法都是抽象的，那么该类可以通过接口的形式来表示。
class用于定义类
interface 用于定义接口。

接口定义时，格式特点：
1，接口中常见定义：常量，抽象方法。
2，接口中的成员都有固定修饰符。
    常量：public static final
    方法：public abstract 
记住：接口中的成员都是public的。


接口：是不可以创建对象的，因为有抽象方法。
需要被子类实现，子类对接口中的抽象方法全都覆盖后，子类才可以实例化。
否则子类是一个抽象类。

接口可以被类多实现，也是对多继承不支持的转换形式。java支持多实现。


*/


interface Inter
{
    public static final int NUM = 3;
    public abstract void show();
}

interface InterA
{
    public abstract void show();
}

class Demo
{
    public void function(){}
}

class Test extends Demo implements Inter,InterA
{
    public void show(){}
}


interface A
{
    void methodA();
}
interface B //extends A
{
    void methodB();
}
//接口间可以多继承
interface C extends B,A
{
    void methodC();
}

class D implements C
{
    public void methodA(){}
    public void methodC(){}
    public void methodB(){}
}


class InterfaceDemo 
{
    public static void main(String[] args) 
    {
        Test t = new Test();
        System.out.println(t.NUM);
        System.out.println(Test.NUM);
        System.out.println(Inter.NUM);

    }
}
```

#### 特点

* 接口是对外暴露的规则。
* 接口是程序的功能扩展。
* 接口可以用来多实现。
* 类与接口之间是实现关系，而且类可以 继承一个类的同时实现多个接口。
* 接口与接口之间可以有继承关系。

例子：

```
//学生
abstract class Student
{
    //学习
    abstract void study();
    //睡觉
    void sleep()
    {
        System.out.println("sleep");
    }

}
//抽烟
interface Smoking
{
    void smoke();
}
//张三是学生，必然学习，但还抽烟
class ZhangSan extends Student implements Smoking
{
    void study(){}
    public void smoke(){}
}
//李四就学习，不抽烟
class Lisi extends Student 
{
    void study(){}
}



abstract class Sporter
{
    abstract void play();
}
//运动员必须运动，但是业余也可以学习
interface Study
{
}
class wangwu extends Sport implements Study
{
    void play(){}
}
//定义在类中是必须有的，接口是不在一个体系中可有可无的
```



