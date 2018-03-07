## Java总结

[TOC]

### equals方法和"=="比较时候相等有什么区别？

> `equals`属于`Object`类的方法，和`==`比较没有区别。

- 对于`基本数据类型`的比较，比较的是`值的内容`，而不管是什么类型。
- 对于`引用数据类型`的比较，比较的是`引用变量的内存地址`(栈空间地址)
- `String`/`File`/`Date`/`包装类`重写了`equals`方法，比较的是对象的内容是否相同。


### 基本数据类型、包装类、String类的转换

```java
//基本数据类型、包装类 => String类
//调用String类重载的valueOf(XXX xx)方法
int i1 = 10;
Integer i2 = new Integer("11");
System.out.println(i1);
System.out.println(i2);
String s1 = i1 + ""; //方法1
String s2 = String.valueOf(i2); //方法2
System.out.println(s1);
System.out.println(s2);

//String类 => 基本数据类型、包装类
//调用包装类的parseXXX(String xx)方法
String s3 = "2018";
String s4 = "119";
int i3 = Integer.parseInt(s3);
int i4 = new Integer(s4);
//int i4 = (int) s4; //不行
System.out.println(i3);
System.out.println(i4);
```

### 接口(Interface)和抽象类(Abstract)的区别
> 接口是一种特殊的抽象类，是常量和抽象方法的集合。
- 接口定义的是一种功能。
- Java中类只能单继承，但是接口支持多继承，接口之间也可以继承。
- 接口可以实现不相关类的相同行为，而不需要考虑类的层次关系。
- 接口主要用来定义规范，解除耦合关系。

```java
package com.aakng.javastudy.d20180306;

public class InterfaceTest {
    public static void main(String[] args) {
        System.out.println(new B().getName());
    }
}

interface A {
    //没有构造方法
    String NAME = "商宗康"; //public final static

    String getName(); //public abstract
}

class B implements A {
    public String getName() {
        return NAME;
    }
}
```
