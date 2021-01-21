---
title: 2-3-lambda表达式与内部类
url: 2-3-lambda表达式与内部类
author: YJ2CS
avatar: '/custom/avatar.webp'
authorLink: YJ2CS.github.io
authorAbout: 愿青年摆脱了冷气，只是向前走！
authorDesc: 愿青年摆脱了冷气，只是向前走！
comments: true
categories:
  - learn-java
tags:
  - 悦读
no-photos: 'https://random.52ecy.cn/randbg.php?size=1&rid-8eec'
date: 2020-11-10T22:16:00.000Z
date updated: '2020-12-26T11:50:54+08:00'

---

## lambda表达式的定义及实现

lambda表达式是一个可传递的代码块，可以在以后执行一次或者多次。
形如:

```Java
(String first,String second)-> {
    first.length() - second.length()
}
```

如果要完成的计算无法放在一个表达式中，就可以像写方法一样，把这些代码放在{}中，并包含显式的return语句

```Java
(String first,String second) ->{
    if (first.length()<second.length()) return -1;
    else if(first.length()>second.length()) return 1;
    else return 0;
}
```

即使lambda表达式没有参数，仍然要写空括号，就像是无参方法一样

```Java
()->{
    for(int i = 100;i>=0;i++){
        System.out.println(i);
    }
}
```

如果可以推导出lambda表达式的参数类型，那么可以省略其类型,例如

```Java
Comparator<String>comp
    =(first,second)->
        first.length() - second.length();
```

在这里，编译器就可以推导出first和second必然是字符串

如果lambda表达式在某些分支返回一个值，而另外一些分支不返回值，这样是不合法的。

## 函数式接口

Java中有很多封装代码块的接口，如ActionListener或Comparator.具体来说，函数式接口是只有一个抽象方法的接口，它不存在非抽象的方法。

lambda与这些函数式接口是兼容的，即完全可以用一个lambda表达式来代替这个函数式接口对象。

需要一个**函数式接口**的对象的地方，完全可以用一个lambda表达式来代替这个函数式接口对象。

函数式接口是只有一个抽象方法的接口，它不存在非抽象的方法。

接口完全可以重新声明Object类中的方法，在声明的过程中，有可能会让某些从object类继承来的方法不再抽象，所以接口完全可以存在以下非抽象方法

不能把lambda表达式赋值给Object类型的变量，因为Object不是函数式接口

## 方法引用

## 内部类的定义及实现

定义在一个类内部的类叫内部类，包含内部类的类称为外部类。内部类可以声明public、protected、private等访问限制，

可以声明 为abstract的供其他内部类或外部类继承与扩展，或者声明为static、final的，也可以实现特定的接口。

外部类按常规的类访问方式使用内部 类，唯一的差别是外部类可以访问内部类的所有方法与属性，包括私有方法与属性。

内部类(inner class)是定义另一个类中的类。

-   内部类可以对同一个包中的其他类隐藏。
-   内部类方法可以访问定义这个类的作用域中的数据，包括原本私有的数据

非静态内部类中添加了一个隐式引用，指向实例化这个对象的外部类对象。所以通过这个指针，它可以访问外部类中的全部状态

而静态内部类中没有这个附加的指针，其相当于C++的嵌套类。

### 静态内部类

静态类（只有内部类才能被声明为静态类，即静态内部类）

1.只能在内部类中定义静态类

2.静态内部类与外层类绑定，即使没有创建外层类的对象，它一样存在。

3.静态类的方法可以是静态的方法也可以是非静态的方法，静态的方法可以在外层通过静态类调用，而非静态的方法必须要创建类的对象之后才能调用。

4.只能引用外部类的static成员变量（也就是类变量）。

5.如果一个内部类不是被定义成静态内部类，那么在定义成员变量或者成员方法的时候，是不能够被定义成静态的。

```Java
public class OutClassTest {
    int out1=1;
    static int out2=1;
    void out(){
        System.out.println("非静态");
    }
    static void outstatic(){
        System.out.println("静态");
    }
    public class InnerClass{
        void InnerClass(){
            System.out.println("InnerClass!");
            System.out.println(out1);
            System.out.println(out2);
            out();
            outstatic();//静态内部类只能够访问外部类的静态成员
        }

      // static void inner(){}  static int i=1;
      // 非静态内部类不能有静态成员（方法、属性）
    }

    /**
    * 静态内部类
    */
    public static class InnerStaticClass{
        void InnerStaticClass(){
            System.out.println("InnerstaticClass");
          //  System.out.println(out1);out();   no ok
          //  静态内部类只能够访问外部类的静态成员
            System.out.println(out2);
            outstatic();
        }
        static void innerStatic(){}  static int i=1;//静态内部类能有静态成员（方法、属性）
    }
    public static void main(String[] args){
       OutClassTest a=new OutClassTest();
        OutClassTest.InnerstaticClass b=new OutClassTest.InnerstaticClass();//创建静态内部类
        OutClassTest.InnerClass c=a.new InnerClass();//创建非静态内部类
    }
}
```

总结

-   是否能拥有静态成员

    静态内部类可以有静态成员(方法，属性)，而非静态内部类则不能有静态成员(方法，属性)。

-   访问外部类的成员
    静态内部类只能够访问外部类的静态成员,而非静态内部类则可以访问外部类的所有成员(方法，属性)。

-   静态内部类和非静态内部类在创建时有区别

```java
//假设类A有静态内部类B和非静态内部类C，创建B和C的区别为：
A a=new A();
A.B b=new A.B();
A.C c=a.new C();
```

作者：thekingisalwayslucky
链接：<https://juejin.im/post/6844903791863529480>
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

内部类中声明的所有静态字段都必须是final，并初始化为一个编译时常量。如果这个字段不是一个常量，就可能不唯一。

内部类最好不要有static方法，现任内部类中如果有static方法，这个方法明显只能访问外围类的静态字段和方法，显然这样复杂性很大，带来的好处有些得不偿失。

-   只要内部类不需要访问外围类对象，即不包含外部类的对象引用，就应该使用静态内部类。静态内部类也被称作嵌套类
-   与常规内部类不同，静态内部类可以有静态字段和方法
-   在接口中声明的内部类自动是static和public

### 匿名内部类

## 代理

-   下一节: [[2-4-发布和部署]]
