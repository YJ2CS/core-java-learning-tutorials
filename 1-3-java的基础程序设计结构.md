---
title: 1-3-Java的基础程序设计结构
url: 1-3-java的基础程序设计结构
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
no-photos: 'https://random.52ecy.cn/randbg.php?size=1&rid-6ee9'
date: 2020-11-10T22:16:00.000Z
date updated: '2020-12-26T11:50:36+08:00'

---

## 基本变量类型

## 运算符

## 字符串

## 流程控制

### 顺序结构

顺序结构就是从上到下逐行地执行，中间没有任何判断和跳转

### 分支结构

Java提供两种常见的分支控制结构if switch

#### if

if语句使用布尔表达式或者布尔值作为分支条件

else本身就是一个条件！else的隐含条件是对前面条件取反。else（ 条件2 && !(条件1) ）

#### switch

switch语句用于对多个整型值进行匹配

Java7后，switch语句后面的控制表达式的数据类型只能是byte、short、char、int四种整数类型，枚举类型和java.lang.String类型（不能是StringBuffer或者StringBuilder），不能是boolean类型

开始点和结束点非常清晰，_case 条件_ 后的花括号完全可以省略

#### break结束分支结构

break是极其重要的，一旦与case标签比较后遇到相等的值，会开始执行这个case标签后的代码，不再判断与后面的case、default标签条件是否匹配，直到遇到break才会结束

### 循环结构

#### while循环

src/v1ch03/Retirement

```java
import java.util.*;

/**
 * This program demonstrates a <code>while</code> loop.
 *
 * @author Cay Horstmann
 * @version 1.20 2004-02-10
 */
public class Retirement {
    public static void main(String[] args) {
        // read inputs
        Scanner in = new Scanner(System.in);

        System.out.print("How much money do you need to retire? ");
        double goal = in.nextDouble();

        System.out.print("How much money will you contribute every year? ");
        double payment = in.nextDouble();

        System.out.print("Interest rate in %: ");
        double interestRate = in.nextDouble();

        double balance = 0;
        int years = 0;

        // update account balance while goal isn't reached
        while (balance < goal) {
            // add this year's payment and interest
            balance += payment;
            double interest = balance * interestRate / 100;
            balance += interest;
            years++;
        }

        System.out.println("You can retire in " + years + " years.");
    }
}

```

#### do while循环

src/v1ch03/Retirement2

```java
import java.util.*;

/**
 * This program demonstrates a <code>do/while</code> loop.
 *
 * @author Cay Horstmann
 * @version 1.20 2004-02-10
 */
public class Retirement2 {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);

        System.out.print("How much money will you contribute every year? ");
        double payment = in.nextDouble();

        System.out.print("Interest rate in %: ");
        double interestRate = in.nextDouble();

        double balance = 0;
        int year = 0;

        String input;

        // update account balance while user isn't ready to retire
        do {
            // add this year's payment and interest
            balance += payment;
            double interest = balance * interestRate / 100;
            balance += interest;

            year++;

            // print current balance
            System.out.printf("After year %d, your balance is %,.2f%n", year, balance);

            // ask if ready to retire and get input
            System.out.print("Ready to retire? (Y/N) ");
            input = in.next();
        }
        while ("N".equals(input));
    }
}

```

#### 确定循环 for循环

for循环的循环迭代语句（i++）写在了for后的括号中，并没有和循环体放在一起，当使用continue来结束本次循环后，循环迭代语言一样会照常执行

初始化变量可以有多个，但这些变量应该有相同的数据类型（如int）

循环条件可以是一个包含逻辑运算符的表达式，例如 **b<10&& s<4 && p<10;**

src/v1ch03/LotteryOdds

```java
import java.util.*;

/**
 * This program demonstrates a <code>for</code> loop.
 * 此程序演示for循环
 * @author Cay Horstmann
 * @version 1.20 2004-02-10
 */
public class LotteryOdds {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);

        System.out.print("How many numbers do you need to draw? ");
        int k = in.nextInt();

        System.out.print("What is the highest number you can draw? ");
        int n = in.nextInt();

        /*
         * compute binomial coefficient n*(n-1)*(n-2)*...*(n-k+1)/(1*2*3*...*k)
         * 计算二项式系数n*（n-1）*（n-2）*…*（n-k+1）/（1*2*3*…*k）
         */

        int lotteryOdds = 1;
        for (int i = 1; i <= k; i++) {
            lotteryOdds = lotteryOdds * (n - i + 1) / i;
        }

        System.out.println("Your odds are 1 in " + lotteryOdds + ". Good luck!");
    }
}

```

#### break结束循环结构

不管是哪种循环，一旦在循环体中遇到了break，系统将完全结束该循环，开始执行循环之后的其他代码。

#### continue应用于循环结构

continue只是忽略本次循环的剩下语句，接着开始下一次循环，并不会终止循环，而break则是完全终止了循环本身。

-   Java提供了continue和break来控制循环结构。除此之外，return可以结束整个方法，当然就结束了当前的循环.

## 中断控制流程的语句 标签

对于多层循环，只要在外层循环之前留下一个标签如 _outer:_

当在内层循环中直接使用 _break outer;_ 就可以直接结束外层循环

Java中的标签是一个紧跟着英文冒号的标识符。

标签可以应用到任何语句，将其放到if语句或者块语句之前都是合法的。

但并不提倡使用这种方式，这对程序的可读性造成了极大破坏。

但注意，Java中的标签只有放在 _外层循环语句或者if语句_ 之前才有作用。

## 大数

## 数组

### 声明数组

数组是一种数据结构,通过一个整型下标index(称为 *索引 )来访问数组中的每一个值。

例如a是一个整型数组，那么a[i]就是数组中下标为i的整数。

声明数组变量时，需要指出数组类型和数组变量的名字。

```java
int[] a;
```

但是这样的声明只是声明了变量a，并没有将a初始化为真正的数组。

java中的数组需要初始化后才能使用：

```java
int[] a = new int[100];
```

java会自动给其赋初始值。

一旦创建了数组就不能再改变它的长度。如果需要扩展数组的大小，那么应该使用数组列表ArrayList

[泛型数组列表ArrayList](1-基础知识-3-1.md#声明数组列表ArrayList)

Java中的[]运算符被预定义为完成越界检查，而且没有指针运算，即不能通过*(a1.1)来得到数组中的下一个元素

#### 数组赋初值

如果数组元素是数值型，则初值都会赋值为0或者0.00，0.0

如果数组元素是布尔型（Boolean） 初值会赋值为false

#### 数组拷贝

这个方法通常用来增加数组的大小,第二个参数是新数组的长度.如果新数组的长度小于原始数组的长度，则只拷贝前面的值

_copyof_ 方法示例:

```Java
//这个方法通常用来增加数组的大小
//第二个参数是新数组的长度
luckyNumbers = Arrays.copyOf(luckyNumbers , 2*luckyNumbers.length);
```

#### 访问数组元素

#### 数组索引越界异常

一种数组内常见的异常，数组索引越界异常java.lang.ArrayIndexOutOfBoundsException:N 最后的N就是程序员试图访问的数组索引

### foreach循环

这种循环无须根据索引N来访问数组元素， **也无须获得数组和集合长度，**

foreach循环自动遍历数组和集合中的每个元素,而不是下标值。

### 不规则数组

-   Java中的数组与C++的数组其底层实现有很大不同，但其数组指针和C++中的基本相同，即是在**堆**上分配的

src/v1ch03/LotteryArray.java

```java
/**
 * This program demonstrates a triangular array.
 * 这个程序演示了一个三角形阵列.
 * @author Cay Horstmann
 * @version 1.20 2004-02-10
 */
public class LotteryArray {
    public static void main(String[] args) {
        final int MAX = 10;

        // allocate triangular array
        int[][] odds = new int[MAX + 1][];
        for (int n = 0; n <= MAX; n++) {
            odds[n] = new int[n + 1];
        }

        // fill triangular array
        for (int n = 0; n < odds.length; n++) {
            for (int k = 0; k < odds[n].length; k++) {
                /*
                 * compute binomial coefficient n*(n-1)*(n-2)*...*(n-k+1)/(1*2*3*...*k)
                 * 计算二项式系数n*（n-1）*（n-2）*…*（n-k+1）/（1*2*3*…*k）
                 */
                int lotteryOdds = 1;
                for (int i = 1; i <= k; i++) {
                    lotteryOdds = lotteryOdds * (n - i + 1) / i;
                }

                odds[n][k] = lotteryOdds;
            }
        }

        // print triangular array
        for (int[] row : odds) {
            for (int odd : row) {
                System.out.printf("%4d", odd);
            }
            System.out.println();
        }
    }
}

```

### 命令行参数args

Java应用程序中的参数：String[] 类型的args数组，这个参数表明main方法会接受一个字符串数组args，对应命令行中程序员输入的函数

```Java
//test

```

### 数组排序

src/v1ch03/LotteryDrawing

```java
import java.util.*;

/**
 * This program demonstrates array manipulation.
 * 这个程序演示数组操作
 * @author Cay Horstmann
 * @version 1.20 2004-02-10
 */
public class LotteryDrawing {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);

        System.out.print("How many numbers do you need to draw? ");
        int k = in.nextInt();

        System.out.print("What is the highest number you can draw? ");
        int n = in.nextInt();

        // fill an array with numbers 1 2 3 . . . n
        int[] numbers = new int[n];
        for (int i = 0; i < numbers.length; i++) {
            numbers[i] = i + 1;
        }

        // draw k numbers and put them into a second array
        // 画出k个数，并将它们放入第二个数组中
        int[] result = new int[k];
        for (int i = 0; i < result.length; i++) {
            // make a random index between 0 and n - 1
            // 在0和n-1之间建立一个随机索引
            int r = (int) (Math.random() * n);

            // pick the element at the random location
            //最初result[i]的值为 r+1
            result[i] = numbers[r];

            // move the last element into the random location
            // 将最后一个元素移到随机位置
            numbers[r] = numbers[n - 1];
            n--;
        }

        // print the sorted array
        // 打印已排序的数组
        Arrays.sort(result);
        System.out.println("Bet the following combination. It'll make you rich!");
        for (int r : result) {
            System.out.println(r);
        }
    }
}

```

### Arrays常用方法

| 方法                                   | 备注                                                      |
| ------------------------------------ | ------------------------------------------------------- |
| static xxx[] copyof(xxx[] a,int end) | 这个方法通常用来增加数组的大小,第二个参数是新数组的长度.如果新数组的长度小于原始数组的长度，则只拷贝前面的值 |

-   下一节: [[2-1-类和对象]]
