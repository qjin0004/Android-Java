# Java基础知识：

# Java的重要组成：

## Java语言执行流程：

==.java 的源文件== 通过编译器compiler ==编译成 .class的字节码文件==，通过解释器interpreter解释成具体平台上的机器语言。从而实现一次编译到处实行。

<img src="Android-Java基础.assets/Screen Shot 2021-01-15 at 3.23.16 pm.png" alt="Screen Shot 2021-01-15 at 3.23.16 pm" width="800"/>

## JVM/Java虚拟机



## JDK/Java开发工具包

Java Deleopment Kit 里面有一些命令，可以帮助操作

了解：Windows在配置环境变量path时，要配置到JDK安装目录下的bin目录

* $javac 编译器，将source code转化为byte code  

  i.e.  $javac Student.java

* $java 运行编译后的java程序 也就是扩展名为.class的文件-

  i.e.  $java Student



## JRE/Java运行环境

包括Java虚拟机（JVM）以及Java核心类库和支持文件等。

**JRE VS JDK** ：如果只需要运行Java程序，下载安装JRE即可，如果要开发Java软件，需要下载JDK。
sum：JDK面对developer，JRE面对用户

<img src="Android-Java基础.assets/Screen Shot 2021-01-15 at 3.33.41 pm.png" alt="Screen Shot 2021-01-15 at 3.33.41 pm" width="300"/>



可了解知识：

JavaSE：Java标准版，用于开发桌面程序 i.e. QQ 

JavaEE：Java企业版，用于开发Web程序 

JavaME：Java微型版，用于移动设备开发；在android/ios兴起后，使用的很少





# Java基础：

## 变量常量：

### 命名规范：

标识符：由 字母，数字，_ ，$ 组成，不能以数字开头。严格区分大小写，不能是Java的关键字保留字

变量：same with 标识符，并且采用camel case的方式

类名：满足pascal命名 - 一个单词首字母大写，多个单词所有首字母大写

### 变量数据类型：

<img src="Android-Java基础.assets/Screen Shot 2021-01-18 at 1.52.43 pm.png" alt="Screen Shot 2021-01-18 at 1.52.43 pm" style="zoom:50%;" />

#### 基本数据类型primitive data type：

bit 位 byte 字节，在二进制中 0/1 都是一个bit，bit是计算机中信息的最小单位

- byte/8bit -> 1 byte
- boolean/8
- char/16 -> 2 byte     
- short/16
- int/32 -> 4 byte
- float/32          字面后加f/F
- long/64 -> 8 byte      字面值在int后面接待L  i.e. 35L/037L/0x12aL
- double/64      浮点式/结尾加d/结尾加D

##### 以int为例的字面值：

* 十进制字面值：

* 八进制字面值：0开头，包括0-7的数字 i.e. 037, 056 ...

* 十六进制字面值：0x/0X开头，包括0-9的数字，以及字母a-f/A-F (a 代表 10)不区分大小写  i.e. 0x12, 0xabcf, 0XABCF 

#### 引用数据类型object data type：



### 变量存储位置：

* 局部变量local variable是存储在 stack 栈 中

  以 int n=100；为例

  * 先在stack中开辟存储int大小的空间 4字节
  * 将100存储在开辟的空间

* static variable 既不存储在stack【栈】也不存储在heap【堆】中



### 基本数据类型转换：

#### 隐式/自动类型转换：

从**数据的表示范围小的转换成大的**，不能反向；

<img src="Android-Java基础.assets/Screen Shot 2021-01-19 at 8.31.43 pm.png" alt="Screen Shot 2021-01-19 at 8.31.43 pm" style="zoom:50%;" />

#### 强制类型转换：

上述箭头的反向，也就是说，数据表示范围从大的转向小的，需要进行强制类型转换

i.e. double b = 0.321; int a = (int) b; 

### 常量：final

不能再次更改值，声明同时进行赋值，常量的变量名通常用大写定义；

```java
final double PI=3.14;
```



### 附加：

#### ASCII

#### Unicode：

特殊字符和所有语言字符Unicode，可用在char和String中 

```java
String b = "\u005d";
System.out.println("b:" + b); //b:]
```

#### 转义字符：

```xml
\uxxxx   -> 如上是特殊含义字符  
\'  \"   \\ 表示后面字符没有特殊含义
\r  回车(光标回到本行) \n  换行(光标下一行)  \t tab键   \b back键
```

#### 科学计数法表示浮点型数据：

```java
double d = .2; // .2表示0.2
double d1 = 1.23e5; // E/e 表示十的多少次方的十；当前表示 1.23 * 10**5
float f=1.23e5f;
```



## 运算符：

### 单目/双目/三目运算符：

针对几个操作数进行操作 i.e. ++ 单目，+ - 双目，? : 三目表达式

### 赋值运算符: = += -= *= /= %=

### 算术运算符：+ - * / % ++ --

### 关系运算符：> < >= <= !=

特殊需要注意的: 浮点数和整数进行比较，只要值相等就返回true

```java
float f = 5.0f; long l = 5;
System.out.println(f == l); // true
```

### 逻辑运算符logical: && & || | !

& vs && | vs ||:

&& 是短路运算符，如果第一个是false，则结果一定是false。只有在第一个true的情况下，操作第二个
|| 是短路运算符，只要第一个是true，则结果一定true，不再进行后面表达式运算
&  |是所有的都判断之后回复答案。

### 条件运算符：? :

```java
int max = a>b? a: b;
```

### 运算符的优先级：

<img src="Android-Java基础.assets/Screen Shot 2021-01-20 at 2.43.15 pm.png" alt="Screen Shot 2021-01-20 at 2.43.15 pm" style="zoom:50%;" />



## 流程控制：

### Switch:

JDK7.0以后表达式的值可以是基础数据类型的byte，short，int，char，以及String



### break vs continue：

break：跳出最近的循环

continue：只能在循环中，用于结束本轮循环，继续进行下一轮循环的执行

i.e. 求1+3+5+7+9

```java
int sum = 0;
for(int i = 1; i < 10; i++){
    if(i % 2== 0) continue; // 直接进入下一轮循环，本次不再执行
    sum += i;
}
System.out.println(sum);
```



## 数组：

### 一维数组的声明初始化：

int[] array = new int[10]; // 声明长度，数组都是有默认值的，因为数组属于objective data type

Int[] array = {1,2,3,4,5};

### 二维数组的声明初始化：

二维初始化过程 int[外/行/i] [内/列/j] ；

```java
int[][] nums = new int[3][4]; // int[外/行][内/列]
```

二维数组也可以只指定行数，列数之后再指定；那么每行都是一维数组，如果不再次声明每列的数组长度直接访问，会发生NullPointerException的报错。在声明每行的过程中，每行的数组长度可以不同。

```java
int[][] nums = {{1,3},{2},{3}};
```



## 传值问题：

### 基本数据类型的传值-不受影响：

```java
public void test(int n){
    n++;
    System.out.println("in method: " + n); // 11
}

public static void main(String[] args){
    Leetcode leetcode = new Leetcode();
    //方法中的传值问题
    int n = 10;
    System.out.println("before: " + n); //10
    leetcode.test(n);
    System.out.println("after: " + n); // 10
}
```

### 引用数据类型/对象/数组传值 - 受影响：

创建数组时，在内存中开辟一段连续的内存空间，数组名指向了数组内存中的第一个元素。在传参的时候，传递的是内存空间，也就是说在更改的时候直接更改的是内存空间，所以在改变后出来也受到影响

```java
public void test(int[] n){
    n[0]++;
    System.out.println("in method: " + Arrays.toString(n));//[2, 2, 3, 4]
}

public static void main(String[] args){
    Leetcode leetcode = new Leetcode();
    //方法中的传值问题
    int[] n = {1,2,3,4};
    System.out.println("before: " + Arrays.toString(n)); //[1, 2, 3, 4]
    leetcode.test(n);
    System.out.println("after: " + Arrays.toString(n));//[2, 2, 3, 4]
}
```



### 可变参数列表：

#### 单独可变参数：

* 一个方法只能有一个可变参数列表，当多参数的时候放在param list的最后
* java认为可变参数和array是等价的，所以如果定义了param是可变参数，可以在传参的过程中提供array; 但是如果定义的方法是array，传参不接受可变参数列表，会发生语法报错。
* 所以在定义方法重载overload的过程中 可变参数和array是一致的，会导致重复定义的问题
* 在发生overload时，带有可变参数列表的方法是最后被访问的

```java
public void sum(int... n){// 可看作有1/2/多个int param
    int sum = 0;
    for(int i:n){ // n表示可能为多个param
        sum+=i;
    }
    System.out.println("sum: " + sum);
}

public static void main(String[] args){
    Leetcode leetcode = new Leetcode();
    leetcode.sum(1);
    leetcode.sum(1,2);
    leetcode.sum(new int[]{1,3,4,5,11});
}
```

#### 单一参数+可变参数

在参数列表中，可变参数只能放在最后一个，用来接受随意的个数

```java
public void sum(int target, int... n){// 可看作有1/2/多个int param
    boolean flag = false;
    for(int i:n){ // n表示可能为多个param
        if(i == target){
            flag = true; break;
        }
    }
    System.out.println((flag)? "find" : "N/A");
}

public static void main(String[] args){
    Leetcode leetcode = new Leetcode();
    leetcode.sum(2,1); //N/A
    leetcode.sum(2,1,2); //find
    leetcode.sum(11,1,3,4,5,11); //find
}
```



## 随机数：

### Math：

Math.random() -> 生成一个[0,1)之间的double值

```java
1 + (int)(Math.random() * max); //默认min为1 生成[1,max]之间的随机整数

min + (int)(Math.random() * (max-min+1));// [min,max]
```

### Random:

random.nextInt(value);  生成一个[0,value)之间的double值

```java
Random random = new Random();
random.nextInt(max+1); //默认min为1 生成[0,max]之间的随机整数

min + random.nextInt(max-min+1); // [min,max]
```





# Java的面向对象：

## 面向对象vs面向过程

面向对象

* 优点：更具有稳定性，可扩展性，可重用性

* 缺点：不适用于所有，在改变对象定义的时候维护起来比较困难

## 类和对象：

* 类：确定对象将会拥有的特性（属性）和行为（方法）

* 对象：类的实例表现，有具体的属性值

* **类要模块化**，也就是说一个类只做一个事情，如果一个类做多个事情他的交融和耦合性就会很高，因此类能被复用的可能就会很低。

## 对象实例化的过程：

Cat cat = new Cat();

### 声明对象：

Cat cat **在声明的过程中，在内存栈stack空间中**开辟一块区域取名叫cat，但是此时并没有任何值存储在内存的这个位置中。所以此时还不能做一些属性和方法的调用

### 实例化对象：

new Cat() 对象的**实例化操作，在内存的堆heap中**，开辟一块空间，完成了具体信息的初始化工作。

* new
* 构造函数：
  * 没有任何构造函数的时候，java会自动创建一个default constructor
  * 只要定义任意一个构造函数，java都不会帮助你创建任何

### sum：

声明和初始化对象是在内存的两个不同空间完成的一个是stack一个是heap，使用 = 赋值的方式将两个位置进行关联，将堆空间的内存地址 存在了stack之中【或者说：将stack中的空间指向堆中的实例化空间】，之后stack就可以对存在堆heap中的实例进行操作

<img src="Android-Java基础.assets/Screen Shot 2021-01-24 at 8.17.24 pm.png" alt="Screen Shot 2021-01-24 at 8.17.24 pm" style="zoom:50%;" />

在Java中只要使用new关键字**创建的实例所在heap的空间都是不同的**，即使使用的属性值是相同的。/也就是说：属性值相同的两个对象是不同的











## 方法的重载：overload

两个方法，method name相同，method signature (method name+parameter)不同

























