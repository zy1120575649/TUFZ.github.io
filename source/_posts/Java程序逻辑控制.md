---
title: Java 程序逻辑控制【Java 学习笔记 07】
date: 2020-03-21 22:41:12
tags:
	- Java
	- 学习笔记
categories: Java 学习笔记
---

# if 分支结构

程序开发的过程中会存在三种程序逻辑：顺序结构、分支结构、循环结构，if 分支结构主要是针对关系表达式进行判断处理的分支操作，分支语句主要有三种使用形式，使用的关键字：if、else

<!-- more -->

```java
if (布尔表达式) {
    条件满足时执行;
} else if (布尔表达式) {
    条件满足时执行;
} else if (布尔表达式) {
    条件满足时执行;
} else {
    条件不满足时执行;
}
```

使用 if 最主要的特点就是它可以进行若干个条件判断，进行多条件判断时可以不写 else 语句，但是最好总是写上 else 语句

# switch 开关语句

switch 是一个开关语句，它主要是根据内容来进行判断，需要注意的是 switch 中可以判断的只能是数据（int、char、枚举、String），switch 不能使用逻辑判断，注意：JDK 1.7 之后才支持 String

```java
switch (数据) {
    case 数值:
        数值满足时执行;
        break;
    case 数值:
        数值满足时执行;
        break;
    default:
        所有数值均不满足时执行;
        break;
}
```

switch 语句在进行设计的时候，如果没有在每一个 case 后面追加 break 语句，那么会在第一个匹配的 case 之后继续执行，知道全部 switch 中的后续代码执行完毕或者遇见 break

# while 循环语句

在程序之中提供有 while 语句来实现循环，该语句有两种定义形式：

```java
// while
while (布尔表达式) {
    条件满足时执行;
    修改循环条件;
}
// do...while
do {
    条件满足时执行;
    修改循环条件;
} while (布尔表达式);
```

while 循环与 do...while 循环的区别：

- while 是先判断再执行
- do...while 是先执行一次再判断

实际开发中一般很少用到 do...while

# for 循环语句

for 循环定义的语法如下：

```java
for (定义循环的初始化数值; 循环判断; 修改循环数据) {
    循环语句的执行;
}
```

对于 while 和 for 循环的选择只有一个参考标准：

- 在明确确定循环次数的情况下，优先使用 for 循环
- 在不知道循环次数，但是知道循环结束条件的情况下，优先使用 while 循环

# 循环控制

在循环语句定义的时候通常会使用到的两个循环控制语句：break，continue

- break 的主要功能是退出整个循环结构
- continue 只是结束当前一次循环的执行，跳过当前一次循环

利用 continue 实现 goto 的功能（不建议开发时使用如上代码）：

```java
public class JavaDemo {
    public static void main(String[] args) {
        point: for (int x=0; x<10; x++) {
            for (int y=0; y<3; y++) {
                if (x == y) {
                    continue point;
                }
                System.out.println(x);
            }
        }
    }
}
```

# 循环嵌套

在一个循环语句之中嵌套其他循环语句，循环嵌套的层次越多，时间复杂度越高

eg. 打印乘法口诀表

```java
public class JavaDemo {
    public static void main(String[] args) {
        for (int a=1; a<10; a++) {
            for (int b=1; b<=a; b++) {
                System.out.print(a + " x " + b + "= " + (a*b) + "\t");
            }
            System.out.println();
        }
    }
}
```

eg. 打印三角形

```java
public class JavaDemo {
    public static void main(String[] args) {
        int line = 5;
        for (int x=0; x<line; x++) {
            for (int y=0; y<line-x; y++) {
                System.out.print(" ");
            }
            for (int y=0; y<=x; y++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```