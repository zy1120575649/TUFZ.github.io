---
title: Java 基本概念【Java 学习笔记 04】
date: 2020-03-20 14:15:55
tags:
	- Java
	- 学习笔记
categories: Java 学习笔记
---

注释是程序开发之中的一项重要组成技术，合理的注释能使项目维护更加方便

<!--more -->

# 注释

在 Java 语言里面注释一共有三类：

- 单行注释：// xxxxxx
- 多行注释：/* xxxxx */
- 文档注释：/** xxxxx */，文档注释里面还需要很多的选项，一般建议共同开发工具控制

eg. 定义单行注释

```java
public class JavaDemo {
    public static void main(String[] args) {
        // 单行注释：下面的语句是进行一行提示信息的输出
        System.out.println("Hello World !");
    }
}
```

eg. 定义多行注释

```java
public class JavaDemo {
    public static void main(String[] args) {
        /*
        单行注释：
        下面的语句是进行一行提示信息的输出
        */
        System.out.println("Hello World !");
    }
}
```

如果使用开发工具开发时，还是单行注释会比较方便，而对于一些重要的类和方法都建议使用文档注释

# 标识符与关键字

在任何程序之中，都是一个结构的整合体，在 Java 语言里面有不同的结构，eg. 类、方法、变量结构等，对于不同的结构一定要有不同的说明，对于结构的说明实际上就是标识符，是有命名要求的，但是一般都是要求有意义的单词所组成，同时对于标识符的组成在 Java 之中定义如下：

- 由字母、数字、_、$ 所组成
- 不能使用数字开头
- 不能使用 Java 中的保留字（关键字）

最简单的定义标识符的形式：使用英文开头，对于 $ 一般都有特殊的含义，不建议出现在自己所编写的代码之中

关键字：系统对于一些结构的描述处理，有特殊的含义，eg. public、class 等，Java 中的关键字一共有如下内容：

- 不需要背，必要时可上网查

对于关键字的定义不需要背，对于部分关键字有一些简短说明

- JDK 1.4 =》assert 关键字，用于异常处理
- JDK 1.5 =》enum 关键字，用于枚举定义
- 未使用到的关键字：goto、const
- 还有一些属于特殊含义的单词，严格来讲不算关键字：true、false、null