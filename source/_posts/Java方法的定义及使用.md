---
title: Java 方法的定义及使用【Java 学习笔记 08】
date: 2020-03-23 13:59:09
tags:
	- Java
	- 学习笔记
categories: Java 学习笔记
---

在程序之中，很多情况下需要重复执行一些代码，方法（method）也称之为函数，需要注意的是，进行方法定义有一个前提：方法在主类中定义并且由主方法直接调用

<!-- more -->

# 方法的定义

方法的返回值可以使用 Java 中定义的数据类型（基本数据类型、引用数据类型），在方法之中可以进行返回数据的处理，如果要返回数据就是用 return 来描述，return 返回的数据类型与方法返回值的数据类型相同，如果不返回数据则该方法可以使用 void 进行声明

关于方法名称与变量的定义命名要求：

- 方法名称：第一个单词字母小写，而后每个单词的首字母大写
- 变量名称：第一个单词字母小写，而后每个单词的首字母大写

方法的定义可以方便使用者重复调用，所有的程序都是从主方法开始的，方法定义不要太长，应使单个方法容易理解

在进行方法定义的时候，如果方法的返回值类型为 void，那么可以利用 return 来结束调用

# 方法重载

当方法名称相同，参数的类型或者个数不同的时候就叫方法重载

eg. 不同类型的数据进行加法

```java
public class JavaDemo {
    public static void main(String[] args) {
        System.out.println(sum(10, 10));
        System.out.println(sum(20.0, 10.1));
        System.out.println(sum(10, 10, 10));
    }
    public static int sum(int x, int y) {
        return x + y;
    }
    public static int sum(int x, int y, int z) {
        return x + y + z;
    }
    public static double sum(double x, double y) {
        return x + y;
    }
}
```

同一个方法名称可以根据调用时传递的不同参数的类型或个数实现不同方法体的调用，这就实现了方法重载的定义，方法的重载与方法的返回值类型没有任何关系，只与参数有关，但是实际开发中：只要是方法重载，建议保持其方法的返回值类型相同

eg. `System.out.println();` 就是一个系统自带的方法重载，它可以接收不同数据类型的参数

# 方法递归调用

方法的递归调用指的是一个方法自己调用自己，利用递归调用可以解决一些重复且麻烦的问题，在进行方法递归调用时，需要考虑如下问题：

- 一定要设置方法递归调用的结束条件
- 每一次调用的过程之中一定要修改传递的参数条件

eg. 利用递归求 1 + 2 + 3 + ... ... + 1000

```java
public class JavaDemo {
    public static void main(String[] args) {
        System.out.println(sum(1000));
    }
    public static int sum(int num) {
        if (num == 1) {
            return 1;
        }
        return num + sum(num - 1);
    }
}
```

递归可以简化代码调用，但是实际开发很少会出现递归，大部分情况下都只是考虑一些简单的处理逻辑，递归如果使用不当，则会造成内存溢出

eg. 计算 1! + 2! + 3! + ... ... + 90!

```java
public class JavaDemo {
    public static void main(String[] args) {
        System.out.println(sum(90));
    }
    public static double sum(int num) {
        if (num == 1) {
            return 1;
        }
        return fan(num) + sum(num -1);
    }
    public static double fan(int num) {
        if (num == 1) {
            return 1;
        }
        return num * fan(num - 1);
    }
}
```

实际上有一部分递归是可以通过循环来完成的，但是使用递归要比使用循环结构更清晰简洁

