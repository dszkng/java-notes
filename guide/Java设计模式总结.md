## Java设计模式

> 设计模式是在大量实践中的总结和理论化的优选之后的代码结构、编程风格，以及解决问题的方式。

[TOC]

### 单例模式(Singleton)

### 模板方法(Template Method)
> 抽象类体现的就是一种模板模式的设计，抽象类作为多个子类的通用模板，子类在通用类的基础上进行扩展改造，但子类总体上会保留抽象类的行为方式。

#### 解决的问题
- 当功能内部有一部分是确定的，一部分是不确定的，这时将不确定的暴露出去，让子类来实现。
- 编写一个抽象父类，父类提供了多个子类的通用方法，并把一个或多个方法留给子类去实现，就是一种模板模式。

#### 代码实例
```java
package com.aakng.javastudy.designpattern;

//模板方法
public class TemplateMethod {
    public static void main(String[] args) {
        new SubTemplate().spendTime();
    }
}

abstract class Template {
    public abstract void code();

    public void spendTime() {
        long start = System.currentTimeMillis();
        code();
        long end = System.currentTimeMillis();
        System.out.println("执行花费时间:" + (end - start));
    }
}

class SubTemplate extends Template {
    public void code() {
        String[] arr = new String[3000];

        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

### 工厂方法(Factory Method)
> 定义一个创建对象的方法，让子类决定实例化哪个类，使一个类的实例化延迟到子类。

```java
package com.aakng.javastudy.designpattern;

//工厂方法(Factory Method)
public class TestFactoryMethod {
    public static void main(String[] args) {
        IWorkFactory lucy = new StudentWorkFactory();
        lucy.getWork().doWork();
        IWorkFactory tony = new TeacherWorkFactory();
        tony.getWork().doWork();
    }
}

interface IWorkFactory {
    Work getWork();
}

class StudentWorkFactory implements IWorkFactory {
    public Work getWork() {
        return new StudentWork();
    }
}

class TeacherWorkFactory implements IWorkFactory {
    public Work getWork() {
        return new TeacherWork();
    }
}

interface Work {
    void doWork();
}

class StudentWork implements Work {
    public void doWork() {
        System.out.println("Write homework...");
    }
}

class TeacherWork implements Work {
    public void doWork() {
        System.out.println("Ready notes...");
    }
}
```

### 代理模式(Proxy)
> 为其它对象提供一种代理，以控制对这个对象的访问。
- 代理类替代了类的执行

```java
package com.aakng.javastudy.designpattern;

public class TestProxy {
    public static void main(String[] args) {
        new ProxyObject().action();
    }
}

interface ObjectInterface {
    void action();
}

class ProxyObject implements ObjectInterface {
    ObjectInterface po;

    public ProxyObject() {
        System.out.println("代理类创建成功");
        po = new ObjectClass();
    }

    public void action() {
        System.out.println("这是代理类,开始START");
        po.action();
        System.out.println("这是代理类,执行END");
    }
}

class ObjectClass implements ObjectInterface {
    public void action() {
        System.out.println("这是被代理类");
    }
}
```
