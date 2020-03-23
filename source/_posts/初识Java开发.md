---
title: 初识 Java 开发【Java 学习笔记 03】
date: 2020-03-20 09:46:51
tags:
	- Java
	- 学习笔记
categories: Java 学习笔记
---

编写 Java 程序可以不使用特定编辑器，所有 Java 程序的后缀都是 `*.java`，我们可以建立一个目录保存所有的程序源代码

<!-- more -->

# Java 编程起步

定义第一个程序代码：

`Hello.java`

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello World !");
    }
}
```

Java 程序需要经过两次处理才可以正常执行：

- 对源代码程序进行编译：`javac Hello.java`，编译之后会生成一个 `Hello.class` 的字节码文件，整个过程原理就是利用 JVM 编译出一套与操作平台无关的字节码文件（`*.class`）
- 在 JVM 上进行程序的解释：`java Hello`，**注意：** 这里解释的是字节码文件，字节码文件的后缀（`*.class`）是不需要编写的

解释一下第一个程序：

1. 在 Java 程序开发中最基础的单元是类，所有的程序都必须封装在类当中执行，而类的基本定义语法如下：

```java
[public] class 类名称 {}
```

在程序中定义的类名称是：`Hello`，类的定义有两种形式：

- `public class 类名称 {}`：类名称必须与文件名称保持一致，在一个 `*.java` 文件里只能有一个 `public class` 定义
- `class 类名称 {}`：类名称可以与文件名称不一致，但是编译后的 `*.class` 的名称是 `calss` 定义的类，解释的时候要求解释生成的 `*.class` 字节码文件，在一个 `*.java` 文件里面可以有多个 `class` 定义，并且编译之后会生成不同的 `*.class` 文件

**注意：** 关于源代码类定义的问题：

- 在项目开发中，很少会出现在一个 `*.java` 源代码里面定义多个 `class` 类的情况，所以一般在一个 `*.java` 源代码里就定义一个 `public class` 类就够了
- Java 语言有着明确的要求，定义类名称的时候要求每一个单词的首字母必须大写，eg. HelloWorld、TestDemo 这样才符合标准

2. 主方法：是所有程序执行的起点，并且一定要定义在类中，Java 的主方法定义：

```java
public class 类名称 {
    public static void main(String args[]) {
        // 程序的代码由此开始执行
    }
}
```

**注意：** `String args[]` <=> `String [] args`

必须记住主方法怎么写，即使没有代码补全也能写出来，主方法所在的类统一称为 “主类”，所有的 “主类” 都使用 `public class 类名称 {}` 来定义

3. 屏幕打印（系统输出）：可以直接在命令行方式下进行内容的显示，有如下两种语法：

- 输出之后追加换行：`System.out.println(输出内容);`
- 输出之后不追加换行：`System.out.print(输出内容);`

# JShell 工具

Shell 是脚本程序的含义，在很多编程语言里面为了方便使用者进行代码开发，都会有 Shell 交互式编程环境，可能只是为了一些简短的程序验证，但是在 Java 里面需要编写很多的结构代码才能实现，所以为了解决这样的麻烦，提供了 JShell 指令，直接 cmd 执行指令 `jshell` 即可

除了可以直接在 JShell 命令之中进行程序的编写之外，也可以将一些内容交给一些文件来进行保存

eg. 在 `D:/hello.txt ` 写入如下内容

```
system.out.println("hello");
```

在 JShell 执行指令

```
/open d:/hello.txt
```

屏幕能够成功输出 `hello`

所以使用 JShell 只需要编写核心结构的代码即可，减少了对于结构化的需求，执行指令 `/exit` 即可退出 JShell 交互式界面

# CLASSPATH 环境属性

CLASSPATH 完整理解非常复杂，这里暂时了解其概念

eg. 在 `D:/JavaCode` 下有一个叫 `Hello.class` 的字节码文件，当前用户所在的目录为 `D:/JavaCode`，那么在这种情况之下可以直接使用 `java` 命令进行 `Hello.class` 字节码文件的解释，但是如果现在用户脱离了这个目录，去到了 `C:/` （C 盘目录下并没有 `Hello.class` 字节码文件），如果再次执行程序解释，会出现错误提示：`找不到或无法加载主类 Hello`

如果我们要执行不同目录下的程序，就需要依靠 CLASSPATH 环境属性

定义 CLASSPATH 环境属性：`SET CLASSPATH = D:/JavaCode`

设置了 CLASSPATH 之后，这个时候在 Java 程序解释的时候会自动通过 CLASSPATH 所设置的路径进行类的加载，所以可知：JVM 解释程序的时候需要得到 CLASSPATH 的支持

但是在默认情况下，所有解释的类都是从当前所在的目录中加载的，所以可知：CLASSPATH 的默认设置为当前所在目录加载类文件，很明显如果在非当前目录设置 CLASSPATH 就会使整个系统操作混乱，所以最好采用默认的设置，如果这时候想只通过当前目录加载，则可以将 CLASSPATH 设置为 `.`

eg. 设置从当前所在路径加载类 `SET CLASSPATH = .`

有些时候如果安装了一些与 Java 开发相关的程序，它可能会自动修改默认的 CLASSPATH，所以就需要自己设置回来

**注意：** 现在 CLASSPATH 是在一个命令行下的配置，如果该命令行关闭了，那么相关的属性配置也将消失，所以应该将其定义为全局属性，则可以直接在系统中追加一个属性信息

配置方法：新建用户变量 `CLASSPATH = .`

PATH 和 CLASSPATH 的区别？

- PATH：是操作系统提供的路径配置，定义所有可执行程序的路径
- CLASSPATH：是 JRE 提供的，用于定义 Java 程序解释时的类加载路径，默认设置为当前目录加载，可以通过 `SETCLASSPATH = 路径` 的命令形式来进行定义

JVM 解释字节码文件的寻访过程：JVM ➡ CLASSPATH 定义的路径 ➡ 加载字节码文件，所以 CLASSPATH 是 Java 定义的环境属性，是在 Java 程序解释的时候使用的