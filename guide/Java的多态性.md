## Java的多态性

[TOC]

> 多态性简单理解就是一种事物的多种表现形态，Java面向对象的多态性体现主要有三个方面。

### 方法重载(Overload)/重写(Overwrite)

### 子类对象的多态性

> 让父类对象的引用指向子类的实例(对象)，在调用父类对象的方法时，实际上调用的是子类对象中的方法。`子类对象的多态性不包括属性`

```java
Person p = new Man();
System.out.println(p.age); //实际调用父类(Person类)对象的属性

```

### 程序运行的多态性

> 程序运行时分为编译和运行两个阶段

- 编译时看左边，将此引用变量理解成父类的对象
- 运行时看右边，关注于真正对象的实体(子类的对象)

### 接口(Interface)的多态性
> 接口与具体的实现类之间也存在多态
```java
package com.aakng.javastudy.d20180306;

//多态
public class PolymorphismTest {
    public static void main(String[] args) {
        Tony tony = new Tony();
        PolymorphismTest.test1(tony);
        PolymorphismTest.test2(tony);
        PolymorphismTest.test3(tony);
    }

    public static void test1(Runner r) {
        r.run();
    }

    public static void test2(Swimmer s) {
        s.swim();
    }

    public static void test3(Coding c) {
        c.coding();
    }
}

interface Runner {
    void run();
}

interface Swimmer {
    void swim();
}

interface Coding {
    void coding();
}

class Tony implements Runner, Swimmer, Coding {
    public void run() {
        System.out.println("running...");
    }

    public void swim() {
        System.out.println("swimming...");
    }

    public void coding() {
        System.out.println("coding...");
    }
}
```