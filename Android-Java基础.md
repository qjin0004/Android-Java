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



## Scanner:

接受数字 nextInt() 但是如果输入是String会报错，可以使用String进行接收，然后Integer.parseInt()转换成int。

或者直接使用nextInt() 进行接受错误的话用 next() 消化空格，代码如下

```java
public static int input(){
    Scanner scanner = new Scanner(System.in);
    int input = 0; boolean flag = true;
    while(flag){
        try{
            input = scanner.nextInt();
            flag = false;
        }catch (Exception e){
            System.out.println("****不合法输入，再次输入****");
            scanner.next();
        }
    }
    return input;
}
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

### 对象实例化的过程：

Cat cat = new Cat();

#### 声明对象：

Cat cat **在声明的过程中，在内存栈stack空间中**开辟一块区域取名叫cat，但是此时并没有任何值存储在内存的这个位置中。所以此时还不能做一些属性和方法的调用

#### 实例化对象：

new Cat() 对象的**实例化操作，在内存的堆heap中**，开辟一块空间，完成了具体信息的初始化工作。

##### new

##### 构造函数：

* 没有任何构造函数的时候，java会自动创建一个default constructor

* 只要定义任意一个构造函数，java都不会帮助你创建任何

* **this关键字：**
  
  * 在给定的参数和field变量名相同是，java会使用**就近原则**将方法中的变量识别为参数，使用this去指定当前的变量是field
  * 可以在constructor使用this()调用其他构造函数，但是这句只能是方法中的第一句
  * 也可以通过this.method()调用定义的方法
  
* 如果设置值的过程中要进行验证，可以通过调用setMethod 进行实现

  ```java
  public Monkey(String name){
    this.setName(name);
  }
  
  public void setName(String name){
    if(name.length() > 1){
      this.name = name;
    }else {
      System.out.println("invalid Name");
    }
  }
  ```

  

#### sum：

声明和初始化对象是在内存的两个不同空间完成的一个是stack一个是heap，使用 = 赋值的方式将两个位置进行关联，将堆空间的内存地址 存在了stack之中【或者说：将stack中的空间指向堆中的实例化空间】，之后stack就可以对存在堆heap中的实例进行操作

<img src="Android-Java基础.assets/Screen Shot 2021-01-24 at 8.17.24 pm.png" alt="Screen Shot 2021-01-24 at 8.17.24 pm" style="zoom:50%;" />

在Java中只要使用new关键字**创建的实例所在heap的空间都是不同的**，即使使用的属性值是相同的。/也就是说：属性值相同的两个对象是不同的





## 封装：

### 含义：

将class的某些信息隐藏在类的内部，不让外界直接访问 (field -> private)，而是通过类提供的方法 get/set针对隐藏信息进行操作和访问。

### 跨包调用：

* 包名小写，一个class只能声明一个包package语句，声明可指定具体的class也可声明整个包 i.e.  import animal.*; import animal.Cat;  

* 但是*只能是下一级直接的类class，不能跨level进行声明调用；

* 不能使用import同时指定声明不同package的同名class，i.e. import animal.Cat; import machine.Cat; ❎
* 如果一个声明指定class，一个声明整个包，在直接使用class名的情况下，指的是指定声明包中的内容 i.e. import animal.Cat; import machine.*;  -> Cat cat = new Cat(); 指的是animal的cat

<img src="Android-Java基础.assets/Screen Shot 2021-01-28 at 12.41.55 pm.png" alt="Screen Shot 2021-01-28 at 12.41.55 pm" style="zoom:50%;" />

### 如何达到封装：

修改属性 visiable modifier，创建getter/setter，在getter/setter中添加属性控制语句

通过包package进行项目功能的分块管理



### static/静态:

**静态成员是在类加载的时候就存在了，不依赖于任何object产生创建。**

类加载：在执行某一类时，jvm会通过java固定的ClassLoader类，将相关类加载到jvm中用于执行

使用static修饰的是 **静态成员/类成员**。表示无论类实例化多少对象，都会**共用同一块静态空间**。

#### 静态成员 vs normal成员：

##### normal 成员：

当class的对象实例产生的时候，相关成员会产生；当对象销毁的时候，成员会进行资源释放

##### static 成员：

* 从**第一次类加载**的时候产生，类对象共享；
  当这个类不再有任何对象被使用，static 成员才会进行资源释放，生命周期长

* 可以通过对象名object name进行访问，也可以通过Class Name直接进行访问

* static 可以修饰field，method；**不能修饰class，local variable  属于语法错误**

#### static variable 静态变量：

属于class，class所有的object都共享这个变量，可以直接通过类名进行访问

```java
public class A {
    private int x;         // 实例变量 normal
    private static int y;  // 静态变量 static/class 

    public static void main(String[] args) {
        // int x = A.x;  // Non-static field 'x' cannot be referenced from a static context
        A a = new A();
        int x = a.x;
        int y = A.y;
    }
}
```

#### static method：

只能访问针对当前已经存在的方法。static是在类第一次加载的时候就存在了，所以是比normal存在的更早的。那么在normal中可以访问static成员，但是在static方法中是识别不到normal方法的，因为normal方法是依赖object为基础调用的 i.e. **this super都不应该出现**，因为这两个关键词都是和object有关的

如果一定要在static中调用normal成员，只能在static中对象实例化 new constructor，然后再使用实例化辅助调用

**static 方法只能被继承，不能被重写Override，但是如果父类定义 static void say(){...}, 子类也定义 static void say(){...}, 不报错，是被编译器理解为定义了另一个方法而非原方法的重写，因为使用@Override是不能通过的**

```java
public abstract class A {
    public static void func1(){
    }
    // public abstract static void func2();  // Illegal combination of modifiers: 'abstract' and 'static'
}

public class A {
    private static int x;
    private int y;

    public static void func1(){
        int a = x;
        // int b = y;  // Non-static field 'y' cannot be referenced from a static context
        // int b = this.y;     // 'A.this' cannot be referenced from a static context
    }
}
```

#### Static block 代码块:

##### 普通代码块:

顺序执行，先出现，先执行

##### 构造代码块：

object在被创建的时候调用，并且顺序优于构造方法；多个构造代码块会按照顺序执行。如果创建多个实例的时候，每次创建实例都会执行一次构造代码块，也就是会执行多次

可以给static field，normal field进行赋值

##### 静态代码块：

静态代码块会在class第一次加载的时候执行，优先于构造代码块； 多个静态代码块按照顺序执行。如果创建多个实例的时候，静态代码块也只执行一次，因为只在类第一次加载的时候执行

只能给static field进行赋值，normal的是不允许的；

**如果有需要只执行一次的代码，可以放在静态代码块中，用于提高效率**

方法中不设置静态代码块

```java
public class Code {
    static {
        System.out.println("code static block");
    }

    {
        System.out.println("code normal block");
    }

    public Code(){
        System.out.println("code constructor");
    }
}

public class CodeBlock {
    static {
        System.out.println("CodeBlock static block");
    }

    {
        System.out.println("CodeBlock normal block");
    }

    public CodeBlock(){
        System.out.println("CodeBlock constructor");
    }

    public static void main(String[] args) {
//        CodeBlock static block  加载codeblock class时print
        System.out.println("CodeBlock主方法"); // CodeBlock主方法
        System.out.println("产生Code实例对象");// 产生Code实例对象
//        code static block 加载code class时print
        Code code = new Code(); // code normal block code constructor
        System.out.println("产生CodeBlock实例对象"); //产生CodeBlock实例对象
        CodeBlock codeBlock = new CodeBlock();//CodeBlock normal block CodeBlock constructor
    }
}
```

Output: 

由于main方法在CodeBlock中，首先加载CodeBlock的代码，加载过程中执行CodeBlock静态语句块，之后运行Code的实例化代码，将Code相关的类(如果有父类的话，父类也算)加载进入jvm，执行Code的静态语句块，之后在执行constructor之前要执行Code的普通语句块，之后是Code的constructor。完成后做CodeBlock的实例化，因为已经加载过CodeBlock的代码，所以直接进入normal block和constructor

```xml
CodeBlock static block
CodeBlock主方法
产生Code实例对象
code static block
code normal block
code constructor
产生CodeBlock实例对象
CodeBlock normal block
CodeBlock constructor
```

##### 静态内部类：

使用static在一个class中标记的class；

静态内部类 StaticInnerClass 不能访问外部类的非静态方法，一样的原因，因为不存在。

```java
public class OuterClass {

    class InnerClass {    // 非静态内部类，并且default访问修饰符；只能先有Outer 再再基础之上有inner
    }

    static class StaticInnerClass { // 静态内部类，并且default访问修饰符【静态static相当于提升等级，可以和Outer一样的创建】
    }

    public static void main(String[] args) {
        // InnerClass innerClass = new InnerClass(); // 'OuterClass.this' cannot be referenced from a static context
        OuterClass outerClass = new OuterClass();   
        InnerClass innerClass = outerClass.new InnerClass();   // 创建inner只能在Outer object的基础上产生
        StaticInnerClass staticInnerClass = new StaticInnerClass(); 
      //static inner 相当于和Outer一个级别，所以想要使用StaticInner的时候和Outer一个方式创建
    }
}
```



## 继承：

继承是一种类和类的关系。当两个class有相同的属性和动作的时候，可以将相同的field/method抽取出来做parent class，children class可以继承所有parent class的功能和方法，并且可以增加新的属性和方法。**children不能选择性继承parent特征，没有选择余地。 i.e. Animal (name, age, eat(), sleep()); Cat (color, miao()); Dog (species, wang()); 要满足children is a parent的逻辑关系

### extends

* **子类只能继承一个父类 ！！！**
* 继承关系下，子类可以看到父类所有非私有的成员: ! private；也就是说如果field定义为private是看不到的，只能通过getter/setter进行查看设置
* 同一个父类的不同子类之间，不能相互访问对方的method； 亲兄弟明算帐
* 父类不能访问子类的方法 - 只能单向

```java
class Animal{
  
}

class Dog extends Animal{
  // 子类特有的属性和方法
}

class Cat extends Animal{
  
}
```



### visiblity modifier访问修饰符

访问权限从小到大：

| 访问修饰符 | 本类 | 同包所有 | 跨包子类 | 跨包其他 |
| :--------: | :--: | :------: | :------: | :------: |
|  Private   |  T   |          |          |          |
|  Default   |  T   |    T     |          |          |
| Protected  |  T   |    T     |    T     |          |
|   Public   |  T   |    T     |    T     |    T     |



### 方法的重载Overload

同一个class中，两个方法，method name相同，method signature (method name+parameter)不同

方法返回值，访问修饰符不做限制



### 方法的重写Override

在继承的关系中，方法名，方法参数列表 (属性，个数) 完全相同，参数列表中参数变量名可变(因为是local var)，方法的返回值return type 要一定程度上的相同，也就是说原则上是相同的，但是允许是返回值的子类也可。i.e. 父类返回Animal 子类返回Dog

访问修饰符一定范围内可以变化 (访问范围要 >= parent的访问范围，比父类强) 

调用方法时，首先查找自己是否定义了对应方法，然后查找parent是否定义了对应方法。 -- 按照顺序进行调用

**static method (类共享只能继承不能重写) 和 final method (常量方法) 不能被重写** 

```java
class Animal{
  public void eat(){
        System.out.println(this.getName() + " is eating");
    }

    public Animal run(){
        return new Animal();
    }
}

class Dog extends Animal{
  // 子类特有的属性和方法
  @Override
    public Dog run(){   // 子类的返回值一定程度上和父类相同，是父类返回值的子类
        return new Dog();
    }
}

class Cat extends Animal{
  @Override
    public void eat(){
        System.out.println("children is eating now");
    }
	//Overload
    public void eat(String name){
        System.out.println(name + " is eating");
    }
}
```



### super

#### super引用成员：

super代表父类对象的引用，可以使用super调用父类的属性field/方法method i.e. super.eat(); super.month = 10;

**父类的构造constructor不允许被继承，也不允许被重写**

#### super():

子类构造方法必然要调用父类的构造方法，如果没有指定则java默认调用的是父类的default constructor无参构造。也就是说，**在如果父类不定义default constructor，子类定义构造器时不指定，会报语法错误，因为没有默认的constructor**

如何调用父类的指定constructor，super(); / super(param..)

* 只能放在子类constructor中
* 并且是子类constructor有效代码的第一行
* this super不能同时出现在一个constructor中



### 继承下静态xx 加载顺序：

static variable/static block 优先于 normal variable/field/normal block 最后才是constactor的初始化
创建object，static variable/ static block 的发生顺序取决于代码的先后

// 网易考过

如果有继承 发生的顺序是  

* 父类静态信息(static variable/static block) 
* 子类静态信息(static variable/static block) 
* 父类(normal variable/ normal block) 
* 父类(构造函数) 
* 子类(normal variable/ normal block)  子类的normal变量要在有父类的创建之后进行
* 子类(构造函数)

```java
public class Animal {
    private String name = "miao";
    private int month = 2;
    private String species = "cat";
    private static int st1 = 22;
    private static int st2 = 23;

    static{
        System.out.println("I'm parent static block");
    }

    {
        System.out.println("I'm parent block");
    }

    public Animal(){
        System.out.println("I'm parent default constructor");
    }
}

public class Cat extends Animal{
    private double weight;
    public static int st3=44;

    static{
        System.out.println("I'm child static block");
    }

    {
        System.out.println("I'm child block");
    }

    public Cat(){
        System.out.println("I'm child default constructor");
    }
}

public class Test2 {
    public static void main(String[] args) {
        Cat cat  = new Cat();
        System.out.println(cat.getName());
    }
}
```

```xml
I'm parent static block
I'm child static block
I'm parent block
I'm parent default constructor
I'm child block
I'm child default constructor
miao
```

首先加载cat的相关所有class，cat有父类，先加载父类的static，然后是子类的static。完成加载后，读取到cat constructor，由于调用子类constructor前要先调用父类constructor，而父类的normal block通常在constructor之前被调用。



### Object类

Object是所有类的父类，一个类如果没有使用extends关键字，则表示这个类继承自Object类 (include array)；

#### equals():

判断两个引用是否指向相同的内存地址 同==功能。 ！String类中是充重写了equals() 方法判断两个值；
自定义重写equals() 

```java
@Override
    public boolean equals(Object obj){
        if(obj == null){ // avoid null getMethod()
            return false;
        }
        Animal temp = (Animal)obj; // 如果输入类型不符合，不能完成强制类型转换，会报错
        if(temp.getName().equals(name) && temp.getMonth() == month){
            return true;
        }else {
            return false;
        }
    }

```

#### toString(): 

toString() 将内容转换为String type，如果是一个Object 转换成@4554617c 形式，实际上是这个Object的hash code的无符号16进制表示

#### clone():

**clone() 是Object的固定方法(protected)，而非是实现clonable接口的方法; **

但是在针对一个class 定义一个clone() 方法的时候，首先需要实现clonable接口，其次要重写父类 (parent class) - Object protected 方法clone() 

所以一个class如果不重写override clone() 方法，他的clone() 是不能被调用的；

```java
public class CloneExample {
    private int a;
    private int b;
}

CloneExample e1 = new CloneExample();
// CloneExample e2 = e1.clone(); // 'clone()' has protected access in 'java.lang.Object'
```

**重写clone() 方法:**

如果不实现 Clonable接口，会导致CloneNotSupportedException

```java
//重写clone() 方法   // 1. implements Clonable接口 2. @Override clone() from Object class
public class CloneExample implements Cloneable {
    private int a;
    private int b;

    @Override
    public Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}

CloneExample e1 = new CloneExample();
try {
    CloneExample e2 = e1.clone();   // call clone() method
} catch (CloneNotSupportedException e) {
    e.printStackTrace();
}
```

* **浅拷贝**

  是指拷贝的对象和原始对象 指向同一对象，也就是<u>说copy内存地址</u>

  浅拷贝后果 -> 更改其一，全部更改

  ```java
  public class ShallowCloneExample implements Cloneable {
  
      private int[] arr;
  
      public ShallowCloneExample() {
          arr = new int[10];
          for (int i = 0; i < arr.length; i++) {
              arr[i] = i;
          }
      }
  
      public void set(int index, int value) {
          arr[index] = value;
      }
  
      public int get(int index) {
          return arr[index];
      }
  
    //浅拷贝 只是继承了Object.clone()方法
      @Override
      protected ShallowCloneExample clone() throws CloneNotSupportedException {
          return (ShallowCloneExample) super.clone();    
      }
  }
  
  // call method
  ShallowCloneExample e1 = new ShallowCloneExample();
  ShallowCloneExample e2 = null;
  try {
      e2 = e1.clone();
  } catch (CloneNotSupportedException e) {
      e.printStackTrace();
  }
  e1.set(2, 222);
  //因为指向同一内存地址，更改其一全部更改
  System.out.println(e2.get(2)); // 222    
  ```

* **深拷贝**

  是指拷贝的对象和原始对象 指向不同一对象，也就是说<u>仅仅copy数值</u>

  深拷贝后果 -> 更改其一，其他不受影响

  ```java
  public class DeepCloneExample implements Cloneable {
  
      private int[] arr;
  
      public DeepCloneExample() {
          arr = new int[10];
          for (int i = 0; i < arr.length; i++) {
              arr[i] = i;
          }
      }
  
      public void set(int index, int value) {
          arr[index] = value;
      }
  
      public int get(int index) {
          return arr[index];
      }
  
    //重新创建新的array，只是单纯的copy值
      @Override
      protected DeepCloneExample clone() throws CloneNotSupportedException {
          DeepCloneExample result = (DeepCloneExample) super.clone();
          result.arr = new int[arr.length];
          for (int i = 0; i < arr.length; i++) {
              result.arr[i] = arr[i];
          }
          return result;
      }
  }
  
  //call method
  DeepCloneExample e1 = new DeepCloneExample();
  DeepCloneExample e2 = null;
  try {
      e2 = e1.clone();
  } catch (CloneNotSupportedException e) {
      e.printStackTrace();
  }
  e1.set(2, 222);
  //因为内存地址不同，更改其一，不影响其他
  System.out.println(e2.get(2)); // 2
  ```

* **clone() 的替代方案**

  在选择可以 clone 的时候，可以创建一个constructor，通过传入 object创建新的值相同的object。因为是新的，所以不同内存地址，效果和深拷贝相同

  ```java
  public class CloneConstructorExample {
      private int[] arr;
      public CloneConstructorExample() {
          arr = new int[10];
          for (int i = 0; i < arr.length; i++) {
              arr[i] = i;
          }
      }
  
    // 这个是最重点的，在选择可以 clone 的时候，可以创建一个constructor，通过传入 object创建新的object
      public CloneConstructorExample(CloneConstructorExample original) {
          arr = new int[original.arr.length];
          for (int i = 0; i < original.arr.length; i++) {
              arr[i] = original.arr[i];
          }
      }
  
      public void set(int index, int value) {
          arr[index] = value;
      }
  
      public int get(int index) {
          return arr[index];
      }
  }
  ```



### final：

不希望被继承/有子类

* **final class** - String/System/...
* **final field** - 建议在声明的同时初始化。如果声明初始化拆分，初始化只能在构造方法处/构造代码块constructor block中，且一定要赋值，赋值之后不能更改
* **final method** - 方法不能被override，虽然子类不能重写此方法，但是子类可以正常继承调用，only不能修改
* **final local variable** - 建议在声明的同时初始化。如果声明初始化拆分，初始化只需要在使用当前变量前完成，且一旦赋值不能更改

Final 声明过的变量：

* primitive data type: 不能修改
* objective data type: 不能重新new赋值，但是可以在基础上更改field的值。也就是说final在描述引用数据类型的时候

```java
public final class Animal{}

final public class Animal{} // "final" "public" do not have order

public final void eat(){}
```

#### static+final：

既不希望修改，又希望全局存在 选择用static final

```java
public static final int count = 12;
public final static int count = 12;
```



### Annotation注解:

reference: https://www.cnblogs.com/peida/archive/2013/04/24/3036689.html

#### 按照运行机制分：

##### 源码注解：

注解只在源码中存在，编译成 .class 文件就不存在了 i.e. @Override 是用来给编译器看的，完成编译后注解不再存在

##### 编译注解

注解在源码和  .class 文件中都存在 i.e. 生成文档@return @param

##### 运行注解

在运行阶段还起作用，设置影响运行逻辑和结果的注解



#### 目的：

用来将任何的信息或元数据与程序元素进行关联，为程序元素加入更直观明了的说明。Annotation不影响逻辑知识起到辅助的作用



#### 元注解: 

##### @Documented - 注解信息是否加入文档

##### @Retention - 定义注解的生命周期

* RetentionPolicy.SOURCE:  在编译阶段丢弃，编译结束后没有意义 i.e. @Override
* RetentionPolicy.CLASS: 在类加载的时候丢弃 i.e. 在字节码文件的处理中有用
* RetentionPolicy.RUNTIME: 始终不会丢弃，运行时也保留，因此可以使用反射读取注解的信息，自定义通常使用这种

##### @Target - 表示该注解用于什么地方

* ElementType.CONSTRUCTOR:
* ElementType.FIELD
* ElementType.LOCAL_VARIABLE
* ElementType.METHOD
* ElementType.PACKAGE
* ElementType.PARAMETER
* ElementType.TYPE：用于描述类/接口/enum

##### @Inherited - 定义注释和子类的关系



#### 自定义注解：

Annotation继承java.lang.Annotation接口，并且不能再去继承别的类/接口

field只能被声明为public/default，且只能用八种基本数据类型 & String Enum Class annotations等数据类型 & 数组

**获取class的方法和field的注解信息，要通过java的反射来获取Annotation对象**

注解也可以没有定义field，不过这样的注解也没啥用。 

自定义Annotation需要设用到元注解

```java
import java.lang.annotation.Documented;
import java.lang.annotation.Retention;
import java.lang.annotation.Target;
import static java.lang.annotation.ElementType.FIELD;
import static java.lang.annotation.RetentionPolicy.RUNTIME;

/**
 * 水果名称注解
 */
@Target(FIELD)
@Retention(RUNTIME)
@Documented
public @interface FruitName {
    String value() default "";
}
```





## 多态：

* 编译时多态：设计时多态方法重载
* 运行时多态：程序运行时动态决定调用哪个方法

必要条件：

* 满足继承
* 父类指向子类的引用

### 向上转型/隐式转型/自动转型

Parent p = new Children();

声明为父类，但是实际指向的是子类，用来体现多态。

#### 向上转型特性：

**声明的实体由于定义为父类，可以调用父类的方法，以及子类针对父类的重写方法。**

**由于实际上指向的是子类，所以在调用重写方法的时候，得到的结果是对应子类方法的结果。见下 eat() 调用**

**但是由于声明为父类，所以不能识别调用 子类中定义的父类没有的方法。 见下 run() 调用**

***

简单理解就是把子类赋值给了父类的变量。因为子类一定是父类的一部分，所以是可以自动转型的

```java
public class Animal {
    private String name;
    private int month;

    public Animal(){}

    public Animal(String name, int month){
        this.setName(name);
        this.setMonth(month);
    }

    public void eat(){
        System.out.println("animal is eating");
    }
		// getter & setter
    public void setName(String name) { this.name = name; }

    public void setMonth(int month) { this.month = month; }

    public String getName() { return name; }
}

// 子类Cat
public class Cat extends Animal{
    private double weight;

    public Cat(){}

    public Cat(String name, int month, double weight){
        super(name,month);
        this.weight = weight;
    }

    public void run(){
        System.out.println("cat is running");
    }

    @Override   // 重写方法
    public void eat(){
        System.out.println("cat is eating");
    }
}

// 子类 Dog
public class Dog extends Animal{
    private String sex;

    public Dog(){}

    public Dog(String name, int month, String sex){
        super(name, month);
        this.sex = sex;
    }

    public void sleep(){
        System.out.println("dog is sleeping");
    }

    public void eat(){
        System.out.println("dog is eating");
    }
}

//Test
public class Test {
    public static void main(String[] args) {
        Animal one = new Animal(); //1
        //子类的对象转型为父类对象，父类声明指向子类实例。
        //可以调用子类重写父类的方法和父类派生的方法
        //子类特有的方法，是不能使用的。
        //i.e. two 不能调用Cat中特有的run方法。因为实体声明为Animal无法识别run
        Animal two = new Cat(); // 2
        Animal three = new Dog();

        one.eat(); // animal is eating
        two.eat(); // cat is eating now
        three.eat(); //dog is eating
        two.getName();
        //two.run();   -> error
    }
}
```



### 强制类型转换/向下转换：

子类引用指向父类实例，也就是**把父类实体复制给子类的变量**，Cat temp = new Animal();  -> 目前是会报错，因为父类实体是更大的范围没法确认一定为具体某一类的子类。需要使用强制转换避免语法报错。

* 在强制转换且不报错的情况下，Cat temp就是和真正的cat是一样的，可以调用子类特有的方法。

* 但是强制转换的前提是后面的一定是前面的子类，不然会报错。

```java
Cat temp = (Cat) two;
temp.eat(); //cat is eating now
temp.run(); //cat is running

Dog temp2 = (Dog)two; //exception: ClassCastException 强制转换后面非对应子类的
temp2.eat();
temp2.sleep();
```

#### instanceof运算符：

**object instanceof Class**  判断左边的对象是否是右边的实例，返回boolean

对于instanceof可以判断左侧是否满足右侧的特征，true的情况：instanceof 自己/父类/父类的父类/.../Object

```java
if(two instanceof Cat){
    Cat temp = (Cat) two;
    temp.eat(); //cat is eating now
    temp.run(); //cat is running
    System.out.println("two convert to cat");
}

if(two instanceof Dog){
    Dog temp2 = (Dog)two; //exception: ClassCastException 强制转换后面非对应子类的
    temp2.eat();
    temp2.sleep();
    System.out.println("two convert to dog");
}

// -> two convert to cat
if(two instanceof Animal){
  System.out.println("Animal");  // Animal
}
if(two instanceof Object){
  System.out.println("Object"); // Object
}
```



#### 应用：

```java
public class Master {
    public void feed(Animal animal){
      	temp.eat(); // 可以提出 或 放在判断里调用 
        if(animal instanceof Cat){
          	Cat temp = (Cat)animal;
            temp.playBall();
        }

        if(animal instanceof Dog){
            Dog temp = (Dog)animal;
            temp.sleep();
        }
    }
}
```



### 抽象类abstract

abstract 不跟 static final private 并存

#### 抽象类：

i.e. Animal 有eat的动作，Cat/Dog 中eat的动作是重写了Animal中的eat因为各自eat的方式不同。在这种情况下，由于每种不同就不必要一定定义Animal的eat方法，因为没有意义 (虽然没有语法错误)。这个时候可以使用抽象类/方法

**应用场景：**父类只是知道其子类应该包含怎样的方法，但是不准确知道子类如何实现，则使用抽象abstract

**抽象类，既避免了子类设计随意性，又避免了父类无意义的实例化**

**抽象类是不能实例化的，因为抽象代表没有实际逻辑意义。可以实例化的是抽象类的子类。**

抽象类代码范例：

```java
public abstract class Animal{
  
}

public class Cat extends Animal{
  
}

//Animal a = new Animal() // error
Animal a = new Cat()  
```



#### 抽象方法：

**如果一个类中定义了抽象方法，这个类一定也是抽象类；但是抽象类中可以没有抽象方法。抽象方法是不定义方法体的，因为没有意义，但是要求子类要么重写抽象方法，要么也定义为抽象类，被接下来的子类继承**

**使用价值：**

父类中有些方法，只是限制子类必须有某些能力，且这些能力一定要实现不同的内容。第一父类实现无意义，第二提示子类完成自定义

```java
public abstract class Animal{
  public abstract void eat();
}

public class Cat extends Animal{
  @Override
  public void eat(){
    //...
  }
}
```



### 接口：

**是对于行为能力的控制，定义了某些class一定要实现的行为方法，接口不关心这些类的内部数据，也不关心方法的实现，只去规定这些类一定要实现某些方法**

因为java只支持单继承。 i.e. 模拟多代手机的迭代，一代定义call(), message()，二代继承一代+定义photo()，三代继承二代+定义video(), network()，四代继承三代+定义wechat()；  i.e. 模拟电脑可以network，手表可以call message，以及手机等。在方法和功能交叉的时候如何对行为能力进行控制时，可以使用接口进行操作



```java
// 定义接口
public interface IPhone {
    // 具有拍照的接口
    public void photo();
}

// 相机实现接口，且要实现接口中的所有方法
public class Camera implements IPhone{
    @Override
    public void photo() {
        System.out.println("camera can take a photo");
    }
}

//模拟一代手机
public class Phone {
    public void call(){
        System.out.println("call");
    }
}

//模拟二代手机，继承自一代，并且实现打电话接口
public class SecPhone extends Phone implements IPhone{
    public void network(){
        System.out.println("network");
    }

    @Override
    public void photo(){
        System.out.println("photo");
    }
}

```

* 接口通常名字定义以 i 开头 i.e. IPhone, INetwork
* 接口访问修饰符：public/default 为了让其外部可以访问，方法的访问修饰符默认是public，书写Override时可以发现。但是方法修饰符不能为protected
* 接口中抽象方法（也就是没有方法体的方法）可以不写abstract关键字限定
* 接口中不存在变量。如果定义常量，默认是public static final。

**如果在接口和子类定义了同名常量，那么如果是由子类实现的接口获取得到的是接口中定义的值；如果是由子类实现的子类实体获取得到的就是子类中定义的常量值。** 例子如下：

```java
public interface INet {
    void network(); //public void network();
  
    int TEMP = 20; //public static final int TEMP = 20;
}

public class Computer implements INet{
		public static final int TEMP = 30;
    @Override
    public void network() {

    }
}

// 如何使用
public class Test{
  public static void main(String[] args) {
    System.out.println("============");
    System.out.println(INet.TEMP); // 20
    
    //在接口和子类都有同名常量时，
    INet iNet = new Computer(); // 接口不能实例化，可以实例化他的实现类
    System.out.println(iNet.TEMP); // 20 在查找值的过程中，变量属于INet，返回INet中定义的常量数值
    Computer computer = new Computer();
    System.out.println(computer.TEMP); // 30  定义为子类，直接进入子类查找常量数值
    
  }
}
```



#### 接口的默认方法&静态方法：

在JDK1.8之后，由于之前子类必须实现接口中所有的定义方法，不方便程序的扩展和维护，如果更新接口必须更新接口下所有的子类。1.8之后引入了接口的默认方法和静态方法。

**重点：**

* **默认方法default，静态方法static都是可以带方法体的方法，并且子类不必须重写实现就可通过编译。**
* **在调用方法时，子类实体可以调用接口的默认方法default（虽然并没有完成重写），但是子类实体不能调用接口的静态方法static（因为：静态方法不能被重写*），静态方法只能通过接口名自己进行调用。**
* **default方法可以重写，static不行。重写的过程中default方法体内使用 <u>接口名.super.defaultMethod()</u> 调用父类default方法，super不能省略否则jvm会理解为调用父类静态方法。**

```java
public interface INet {
    public void network();
    public int TEMP = 20;

    // 默认方法，可以带方法体，可以不必须被子类实现
    default void connection(){
        System.out.println("默认方法");
    }

    //静态方法也可以带方法体，可以不必须被子类实现
    static void stop(){
        System.out.println("接口中的静态方法");
    }
}

public class Computer implements INet{
    public static final int TEMP = 30;
    @Override
    public void network() {}

    @Override
    public void connection() {
        // 表示调用接口中默认的方法，如果不给super会调用的static成员
        INet.super.connection();
        // add more
    }
}


public class Test{
  public static void main(String[] args){
    	Computer computer = new Computer(); // 子类实例化	
    	computer.connection(); // 子类没有重写也同样可以使用接口中的默认方法
      //computer.stop();    // error 静态方法不能被声明的子类实体调用。
      INet.stop();
  }
}
```



#### 实现多接口：

实现多接口在implents后并列写出。

当一个类class实现多接口，多借口中都定义相同名字的default method，解决方案是：**在当前类对于相同签名method进行重写。** 

```java
public class Computer implements INet,IPhone{
    public static final int TEMP = 30;
    @Override
    public void network() {}
    
    @Override
    public void photo() {
    }
}
```



#### 继承父类并实现多接口：

一个类class只能继承唯一父类，但是可以实现多个接口。

接口的实现要放在继承后面，作为一个类只能继承唯一父类，同时实现若干接口，实现接口的时候要实现接口中所有的方法，不然也会变成抽象类。

##### 和接口中方法同名：

如果继承的父类和实现的接口中都定义了同名方法 i.e. Connection(); 在继承和实现的过程中是不报错的，默认实现的是父类派生的方法。

```java
public class Phone {
    public void call(){
        System.out.println("call");
    }

    public void connection(){
        System.out.println("Phone connection");
    }
}

public interface INet {
    public void network();
    public int TEMP = 20;

    // 默认方法，可以带方法体，可以不必须被子类实现
    default void connection(){
        System.out.println("默认方法");
    }

    //静态方法也可以带方法体，可以不必须被子类实现
    static void stop(){
        System.out.println("接口中的静态方法");
    }
}

public interface IPhone {
    // 具有拍照的接口
    public void photo();

    default void connection(){
        System.out.println("connection in IPhone");
    }
}

public class SecPhone extends Phone implements IPhone,INet{
    public void network(){
        System.out.println("network");
    }

    @Override
    public void photo(){
        System.out.println("photo");
    }
  
  	// 新加代码： version2:
  @Override
    public void connection(){
        System.out.println("sec connection");
    }
}

public class Test {
    public static void main(String[] args) {
        SecPhone secPhone = new SecPhone();
        secPhone.connection(); // 此时因为没有重写默认调用父类connection 得到Phone connection
        secPhone.connection(); // version2：此时有重写则先找重写 得到sec connection
    }
}
```

##### 和接口中的常量同名：

接口中定义field就是默认定义成 static final int 的形式，所以是常量

**如果继承的父类class中的成员和接口中的常量同名时，和方法不同 编译器无法分辨，只能在子类中定义独有的x成员才能直接使用x进行访问调用，否则就要声明具体的哪个x  i.e.  One.x; Two.x; Three.this.x;** 

```java
interface One {
    static int x = 11;
}

interface Two {
    final int x = 22;
}

class Three {
    public int x = 33;
}

public class TestOne implements One,Two{
    public void test(){
        //System.out.println(x);  // 语法错误因为One Two都包含x; can not recognize;
			//明确表示识别哪个x
      System.out.println(One.x);  
      System.out.println(Two.x);
    }

    public static void main(String[] args) {
        new TestOne().test();
    }
}

public class TestOne extends Three implements One,Two{
    public void test(){
        //System.out.println(x);  // 语法错误 can not recognize; 因为x在接口中定义为常量，是不好用的。还是不能直接使用 x 进行调用
    }

    public static void main(String[] args) {
        new TestOne().test();
    }
}

public class TestOne extends Three implements One,Two{
    private int x = 44;
    public void test(){
        System.out.println(x);  // 44;
    }

    public static void main(String[] args) {
        new TestOne().test();
    }
}

```



#### 接口的继承：

**IParent, ISon 两个接口之间存在接口的继承关系，class实现子接口，需要实现子接口以及所有父接口的方法** 

```java
public interface IParent {
    public void say();
}

public interface ISon extends IParent{
    public void run();
}

public class Demo implements ISon{ //实现接口和其所有父类接口的所有方法
    @Override
    public void run() {
    }

    @Override
    public void say() {
    }
}
```



在class的继承中，一个子类只能继承唯一父类；在接口interface的继承中，一个子类接口可以继承多个父类接口，在extends后面并列即可

```java
public interface IParent2 {
    void say2();
}

public interface ISon extends IParent, IParent2{
    public void run();
}

public class Demo implements ISon{ // 实现接口以及所有父类接口的所有方法
    @Override
    public void run() {
    }

    @Override
    public void say() {
    }

    @Override
    public void say2() {
    }
}
```

​	

##### 继承多接口处理默认同名方法

同名方法只能是default默认方法出现问题，如果是普通方法，那么只是负责定义，不存在上不知道实现哪个方法的问题

**在多接口定义default同名方法时，接口继承多接口时，会发生错误不知道实现的是哪个，解决方案：自己重新定义同名default方法**

```java
public interface IParent {
    public void say();

    default void connection(){
        System.out.println("IParent connection");
    }
}

public interface IParent2 {
    void say2();

    public void say();

    default void connection(){
        System.out.println("IParent2 connection");
    }
}

public interface ISon extends IParent, IParent2{
    public void run();

    default void connection(){
        System.out.println("ISon connection");
    }
}
```



### 内部类：

一个类定义在另一个类里面或者一个方法里面，称为内部类，与之对应的是外部类。**内部类隐藏在外部类之内，更好的实现了信息的隐藏。**

内部类的信息获取是要借助外部类的。

#### 普通内部类

1. 获取方法：无法直接实例化，因为外部帮助隐藏，需要借助外部类信息完成实例化。具体有三种方式：
   1. new 外部类().new 内部类(); 
   2. 外部object.new 内部类();
   3. 外部定义获取内部方法;

```java
public class Person {
    int age;

    public Heart getHeart(){ // 获取内部类的方法
        return new Heart();
    }

    class Heart{
        public String beat(){
            return "心脏会跳动";
        }
    }
}

public class Test {
    public static void main(String[] args) {
        Person lily = new Person();
        lily.age = 12;

        //Heart heart = new Heart(); error, no Heart class
        //方法1：通过new外部类.new内部类 进行获取
        Person.Heart heart = new Person().new Heart();
        System.out.println(heart.beat());

        //方法2：通过外部类对象.new 内部类
        heart = lily.new Heart();
        System.out.println(heart.beat());

        //方法3：在外部类中定义get内部类方法
        heart = lily.getHeart();
        System.out.println(heart.beat());
    }
}
```

2. 访问修饰符：如果内部类定义为 default 访问修饰，那么同包中是可以通过三种方法访问内部类的，但是跨包不可以，因为default只应用于同包。但是如果定义为public，那么不受限制

3. 内部类中的调用范围：内部类可以调用外部类的方法，因为先有外部类才有内部类。**方法可直接调用，field属性/method如果有同名/同method signature优先访问的是内部，如果想要调用外部类的属性使用 外部.this.field/method进行调用**
4. 外部类想要访问内部类的实例或者方法，外部类中必须通过内部类object访问，无法直接访问。i.e. new Heart().temp = 10;
5. 编译后内部类的文件名是，Outer$Inner.class

```java
public class Person {
    int age;

    // 获取内部类的方法
    public Heart getHeart(){
      new Heart().temp = 10;
        return new Heart();
    }

    public void eat(){
        System.out.println("吃");
    }

    class Heart{
        int age = 50; // 和外部同名field
      	int temp = 12;
        public String beat(){
            eat(); // 内部类可以直接调用定义在外部类的方法，因为先存在外部类再存在内部类
            //return age+"心脏会跳动"; // 调用的最近的，也就是内部类中的age；
            return Person.this.age+"心脏会跳动";
        }
    }
}
```



#### 静态内部类

类共享的，不依赖于外部类可以直接创建的

1. 静态内部类，只能直接访问外部类的静态static方法；如果需要调用非静态方法/成员，可以通过对象实例new Outer().method()/field; 
2. 不能在static中使用普通的this，因为this super都是static的禁词

```java
public class Person {
    int age;

    public Heart getHeart(){// 获取内部类的方法
        return new Heart();
    }

    public void eat(){
        System.out.println("吃");
    }

    static class Heart{
        int age = 13;
        int temp = 22;
      	public static void say(){
          System.out.println("say");
        }
      
        public String beat(){
            new Person().eat();
            return new Person().age+"心脏在跳动";
        }
    }
}
```

静态内部类实例化操作&方法调用

* 静态内部类中的静态static成员，直接通过Outer.Inner.staticField进行调用

* 静态内部类中的普通normal对象，通过内部类实例进行调用；
* 同名属性访问时：
  * 直接默认访问内部类的属性
  * 访问外部类中的static属性，使用 Outer.staticField 进行访问
  * 访问内部类中的normal属性，使用 new Outer().field 进行访问

```java
public class Test {
    public static void main(String[] args) {
        Person lily = new Person();
        lily.age = 12;
				
        // new constructor, 不需要依赖外部类，但是不认识内部类，所以内部类是Outer.Inner
        Person.Heart myHeart = new Person.Heart();
        System.out.println(myHeart.beat());
      	Person.Heart.say(); // static 方法直接通过class名字进行调用
   	}
}
```



#### 方法内部类/局部内部类

1. 定义在方法里面的类，所用范围也在方法内。和局部变量使用相似，没有static成员，没有public/private/protected..
2. 类中可以包含抽象方法abstract method，自然外面class也是abstract class，那么之后也不能进行Inner实例化，不推荐，存在这样的语法场景
3. 方法内部类是基于方法为主，如果想要得到内部类，返回值需要设置为更大的Object，而不是Inner，因为内部类只有在方法体内 { } 才可以被识别，返回时返回Inner的实体。
4. 但是通常不推荐使用方法内部类返回object，因为之后还要进行强制类型转换type casting才能使用Inner class中的对应方法，所以通常直接用方法返回内部类方法的返回值
5. 编译后的文件命名：Outer$1Inner.class

```java
public class Person {
    int age;
    public void eat(){
        System.out.println("吃");
    }

  //version1:返回内部类
    public Object getHeart(){ // 获取内部类的方法
        class Heart{
            int age = 13;
            int temp = 22;
            public String beat(){
                new Person().eat();
                return new Person().age+"心脏在跳动";
            }
        }
        return new Heart();
    }
}
```



#### 匿名内部类/没名

在程序中，对某一个类的实例只使用一次，这个时候，名字没有复用的必要，可以将类的定义和调用放在一起编写来简化程序。

无访问修饰符，无构造方法【没名】，不能出现静态static成员，匿名内部类可以实现接口，也可以继承父类，但是不能兼得。所继承/实现的就是 匿名内部类对应的Outer 例子中是People

使用场景：

* 只用到类的一个实例
* 类在定义后马上用到
* 给类命名并不会导致代码更容易被理解

编译文件：Outer$Number.class

例子：抽象类People没有定义子类，在实现的过程中，由于抽象类不能实例化，所以在调用getRead方法中，直接在调用的同时进行People的定义。

编译文件：People.class, PeopleTest.class, PeopleTest\$1.class, PeopleTest$2.com 

```java
public abstract class People {
    private String name;
    public People(){}

    public abstract void read();

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

public class PeopleTest {
    //传入不同的人调用对应的read方法

    // People是抽象类，read是抽象方法没有被定义方法内容
    public void getRead(People people){
        people.read();
    }

    public static void main(String[] args) {
        PeopleTest peopleTest = new PeopleTest();
        // 由于People是抽象类不能实例化，而且我们认为不会复用内容的情况下
        // 使用匿名内部类的方式：在实例对象的同时，完成方法的定义和执行，只能在代码的位置使用一次
        peopleTest.getRead(new People() {
            @Override
            public void read() {
                System.out.println("man read");
            }
        });

        peopleTest.getRead(new People() {
            @Override
            public void read() {
                System.out.println("woman read");
            }
        });
    }
}

```



#### 练习：

设计接口Ball，实现BallTest class并且以成员内部类，方法内部类，以及在Test class中实现匿名内部类的操作

```java
//接口Ball
public interface Ball {
    //创建抽象方法play()：void
    void play();
}

public class BallTest {
    // 创建方法内部类
    public void info(){
        class Inner_f implements Ball{
            @Override
            public void play() {
                System.out.println("********");
                System.out.println("方法内部类");
                System.out.println("打乒乓球");
            }
        }
        new Inner_f().play();
    }

    // 创建成员内部类Inner_m
    class Inner_m implements Ball{
        public Inner_m(){}

        @Override
        public void play(){
            System.out.println("成员内部类：");
            System.out.println("打篮球");
        }
    }

    // 定义一个方法void playBall(Ball ball)，调用play()方法
    public void playBall(Ball ball){
        ball.play();
    }
}

public class Test {
    public static void main(String[] args) {
        //完成成员内部类内部测试
        BallTest.Inner_m inner_m = new BallTest().new Inner_m();
        inner_m.play();
        //完成方法内部类测试
        BallTest ballTest = new BallTest();
        ballTest.info();
        //完成匿名内部类测试
        ballTest.playBall(new Ball() {
            @Override
            public void play() {
                System.out.println("*******");
                System.out.println("匿名内部类");
                System.out.println("打排球");
            }
        });
    }
}
```



## Java常用工具类：

### 异常：

#### Throwable

<img src="Android-Java基础.assets/Screen Shot 2021-02-25 at 3.10.05 pm.png" alt="Screen Shot 2021-02-25 at 3.10.05 pm" style="zoom:80%;" />

#### try-catch-finally：



##### try-catch-finally & return：

如果有return，先finally语句再回到return转出。

#### checked exception VS unchecked exception：

checked exception：程序落点是try-catch才能通过编译，继承自Exception

unchecked exception：程序落点可以不是try-catch就能通过编译，但是在运行的过程中会跳出，继承自RuntimeException

#### throw VS throws：

throw定义在方法体内，throw的是exception类型的object。一次只能抛出一个，也就是说在某种条件下，throw new UncheckedException(); 

throws定义在method header处，throws Exception 直接给class name，一次可以抛出多个异常

throw VS throws：

* throw表示在某种条件if condition下手动抛出异常，也可让其在当前方法中处理

* throws通常是声明可能要抛出的异常，让其在下一个方法中进行处理。所以在使用throw抛出checked exception后，要么在当前方法中使用try-catch，要么在method header处再次throws出去。下面例子提供两种解决方案

#### 自定义异常：

自定义异常，定义checked exception：extends Exception，定义unchecked exception：extends RuntimeException，在constructor中使用super继承，赋值error message

```java
//自定义异常
public class HotalAgeException extends Exception{
    public HotalAgeException(){
        super("18岁以下，80岁以上由亲友陪同"); // exception message
    }
}

//方式1: throw后throws交给下一个处理
public class TryDemo {
    public static void testAge() throws HotalAgeException{
        System.out.println("input age:");
        Scanner scanner = new Scanner(System.in);
        int age = scanner.nextInt();
        if(age < 18 || age > 80){
            throw new HotalAgeException();  // 要么在此处做try-catch处理，要么throws抛出让上层处理
        }else{
            System.out.println("welcome ~");
        }
    }

    public static void main(String[] args) {
        try{
            TryDemo.testAge();
        }catch (HotalAgeException e){
            System.out.println(e.getMessage()); // 打印exception语句
          	e.printStackTrace(); // 抛出exception错误
        }catch (Exception e){
            System.out.println("input number"); // 针对之前nextInt给String的情况进行提醒
        }
    }
}


// throw checked exception, 直接使用try-catch进行解决
public static void testAge(){
  System.out.println("input age:");
  Scanner scanner = new Scanner(System.in);
  try{
    int age = scanner.nextInt();
    if(age < 18 || age > 80){
      throw new HotalAgeException();
    }else{
      System.out.println("welcome ~");
    }
  }catch (HotalAgeException e){
    System.out.println(e.getMessage());
  } catch (Exception e){
    System.out.println("enter int");
  }
}

public static void main(String[] args) {
  TryDemo.testAge();
}
```



 

#### 异常链：

```java
public class Try {
    public static void main(String[] args) {
        try {
            testThree();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    public static void testOne() throws HotalAgeException {
        throw new HotalAgeException();
    }

    public static void testTwo() throws Exception {
        try {
            testOne();
        } catch (HotalAgeException e) {
//            e.printStackTrace();
            throw new Exception("我是新产生的异常1");
        }
    }

    public static void testThree() throws Exception {
        try {
            testTwo();
        } catch (Exception e) {
            //e.printStackTrace();
            throw new Exception("我是新产生的异常2");
        }
    }
}
```

捕获一个异常后再抛出另一个异常，进而形成一个异常链。当异常链生成的时候，之前的exception会被覆盖，只显示最后一个exception，如何解决？

两种写法：相关于Throwable类，正常是通过new Exception("message"); 

* new Exception("message", exceptionObject); // 使用旧的异常直接创建绑定好的新的异常
* newExceptionObject.initCause(previousExceptionObject); //先创建新异常，使用initCause将旧异常绑定在新异常上

```java
public class Try {
    public static void main(String[] args) {
        try {
            testThree();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    public static void testOne() throws HotalAgeException {
        throw new HotalAgeException();
    }

    public static void testTwo() throws Exception {
        try {
            testOne();
        } catch (HotalAgeException e) {
            //第一种，直接创建绑定好之前exception的新exception实例
            throw new Exception("我是新产生的异常1",e);
        }
    }

    public static void testThree() throws Exception {
        try {
            testTwo();
        } catch (Exception e) {
            //第二种，先创建再绑定之前的exception
            Exception newE = new Exception("我是新产生的异常2");
            newE.initCause(e);//将之前的exception和新的进行封装
            throw newE;
//            throw new Exception("我是新产生的异常2",e);
        }
    }
}
//结果：异常顺序保存下来
```





# Java的多线程

## 进程 vs 线程：

### 进程process：

计算机的核心是CPU，一个CPU一次只能运行一个进程，其他处于非运行状态。进程之间是不共享内存空间的，也就是说他们的memory space是相互独立的。

CPU的执行时间被分成小块，每块叫 “时间片”，CPU所表现出的多项目同步运行，是在多个软件之间快速的交换给人们感官上的同步，这个过程也叫时间片轮转 content-switching

### 线程thread：

线程是进程的一部分，一个进程包含很多个线程，而在这个进程中的多线程是共享当前进程的内存空间的。thread有两种运行模式concurrency和parallel。parallel是多线程之间并行运行，concurrency是可能单线程有序运行也可能多线程并行运行。线程间也会进行content-switching，由于线程之间内存共享，所以切换的代价比进程之间切换的代价小。



## 线程的创建：

### 创建Thread类/Thread子类：

Thread类是Object子类实现了Runnable接口

<img src="Android-Java基础.assets/Screen Shot 2021-02-25 at 3.37.58 pm.png" alt="Screen Shot 2021-02-25 at 3.37.58 pm" style="zoom:80%;" />

#### 常用的Thread构造方法：

##### 常用方法：

* run()： 线程相关的代码写在此方法中，此方法一般都需要重写
* start()：启动线程
* sleep(long m)：线程休眠 m 毫秒的方法
* join()：优先执行调用join方法的线程，类似抢占资源

##### 模拟线程运行：

**启动线程两步： 1. 创建Thread子类对象 2. 调用start() 启动线程**

* getName() 可以直接调用，因为是Thread定义的方法，父类方法可以直接使用
* 启动线程是使用Thread object调用start() 方法实际执行的是 run() 方法中的内容。

* 所有线程只能启动一次，start一次，如果start多次会抛出IllegalThreadStateException

  

模拟主线程和自定义线程：

```java
//自定义线程从Thread中继承
public class MyThread extends Thread {
    public void run(){
        System.out.println(getName()+" - thread is running"); //getName父类Thread定义的方法
    }
}
//运行
public class ThreadTest {

  //当前是两个线程在运行，主方法有一个线程，myThread也有一个线程
    public static void main(String[] args) {
        System.out.println("主线程1");
        MyThread myThread = new MyThread();
        myThread.start(); // 表示启动线程, 然后执行的是run中的内容
        System.out.println("主线程2");
    }
}

/*  打印顺序随机，看谁先获取CPU使用权。
		主线程1
    主线程2
    Thread-0 - thread is running
*/
```



模拟两个自定义线程的运行：

```java
public class MyThread extends Thread{
    public MyThread(String name){
        super(name); // 自定义名字，使用name定义Thread名称
    }

    public void run(){
        for(int i = 1; i <= 10; i++){
            System.out.println(getName()+" is running "+ i);
        }
    }
}

public class ThreadTest {
    public static void main(String[] args) {
        MyThread mt1 = new MyThread("线程1");
        MyThread mt2 = new MyThread("线程2");
        //线程1 2运行的打印的顺序，是取决于线程抢占CPU资源的能力
        mt1.start();
        mt2.start();
    }
}

```



### 实现Runnable接口的对象：

只有一个 run() 方法，Runnable 是Java中用来实现线程的接口，任何实现线程功能的类都必须实现该接口

获取当前Thread名称，通过Thread.currentThread().getName() 获取正在运行的线程名称（currentThread是 static method）

**三步： 1. 定义Runnable实现类对象 2. 通过他创建线程类的对象 3. 启动线程**

```java
public class PrintRunnable implements Runnable{
    @Override
    public void run() {
        //获取当前正在运行的线程的线程名：Thread.currentThread().getName()
        System.out.println(Thread.currentThread().getName() + "is running ");
    }
}

public class Test {
    public static void main(String[] args) {
        PrintRunnable pr = new PrintRunnable();
        Thread thread = new Thread(pr);
        thread.start();
    }
}
```

#### 实现Runnable的类可以被多个线程共享

**Thread是可以共用一个Runnable实现类「下面例子，pr被thread 和thread1共享」，Runnable实现类主要做的事情是定义做的事情，这样适用于多个线程处理同一资源的情况**

```java
public class PrintRunnable implements Runnable{
    @Override
    public void run() {
        //获取当前正在运行的线程的线程名：Thread.currentThread().getName()
        int i = 1;
        while(i <= 10){
            System.out.println(Thread.currentThread().getName() + "is running "+ (i++));
        }
    }
}

public class Test {
    public static void main(String[] args) {
        PrintRunnable pr = new PrintRunnable();
        Thread thread = new Thread(pr);
        thread.start();
      //        PrintRunnable pr1 = new PrintRunnable();
        Thread thread1 = new Thread(pr);
        thread1.start();
    }
}
```

**多线程处理同一资源的简单模型：**

```java
public class PrintRunnable implements Runnable{
    int i = 1;
    @Override
    public void run() {
        //获取当前正在运行的线程的线程名：Thread.currentThread().getName()
        while(i <= 10){
            System.out.println(Thread.currentThread().getName() + "is running "+ (i++));
        }
    }
}

public class Test {
    public static void main(String[] args) {
        PrintRunnable pr = new PrintRunnable();
        Thread thread = new Thread(pr);
        thread.start();
        Thread thread1 = new Thread(pr);
        thread1.start();
    }
}
```

输出结果 - 多线程处理同一资源（随机结果，也可能全部是0/1，但是还是在多线程的模式下操作的）

```xml
Thread-0is running 1
Thread-1is running 2
Thread-0is running 3
Thread-1is running 4
Thread-0is running 5
Thread-1is running 6
Thread-0is running 7
Thread-1is running 8
Thread-0is running 9
Thread-1is running 10
```





### 为什么两种方式创建线程：

* 因为Java不支持多继承，如果类已经继承了一个父类，就不能继承Thread变成一个线程，但是可以实现多个接口，所以使用Runnable接口帮助处理
* 不打算重写/继承Thread中的其他方法，因为变成一个线程只需要有run方法即可，对于父类Thread的其他方法如果不想继承，可以直接使用Runnable进行控制



## 线程的状态和生命周期：

### 线程的状态：

#### 新建 new：

new Thread 创建线程的状态

#### 可运行状态Runnable/就绪：

创建好线程对象调用start方法后，属于可运行状态，不是运行状态，是否运行取决于对cpu的抢夺

#### 正在运行状态Running：

线程获取了cpu使用权就可以进入Running状态

#### 阻塞状态Blocked：

线程暂停运行进入阻塞状态

#### 终止Dead：

线程不在运行的状态



### 线程的生命周期：

<img src="Android-Java基础.assets/Screen Shot 2021-03-05 at 11.38.31 am.png" alt="Screen Shot 2021-03-05 at 11.38.31 am" style="zoom:80%;" />

正在运行状态Running变成可运行状态Runnable，发生的是cpu使用时间到期/时间片用完；

阻塞Blocked 是打断线程执行，让其暂停等待，那么几种Thread的自带method： join(), wait(), sleep(), I/O请求，阻塞状态Blocked 结束回退运行，非正在运行Running(变成Running只能是抢到cpu的使用权限)，所以回退的是Runnable状态，对应是以上几种自带方法的解决方式。



## 线程的调度：

### sleep()

#### intro：

是Thread类的固定方法，让正在执行的线程在指定的毫秒数内进行休眠(暂停执行)，也就是状态从Running->Blocked，传入的参数就是所谓的休眠时间，单位是毫秒。调用过程中可能会抛出InterruptedException（中断线程的一种checked exception，也就是说必须解决）的异常，需要使用try-catch进行处理

源代码中定义为：

```java
public static void sleep(long millis){
  //。。。
}
```



#### 使用场景：

计时计次 - 比如指定的时间完成多少次 【如果实现时钟功能时，计算每秒给出 sleep(1000) 会产生误差，因为阻塞状态之后是进入可运行状态Runnable之后再是Running状态】

定期刷新数据

i.e. - 1: 

```java
public class MyThread implements Runnable{
    @Override
    public void run() {
        for(int i = 1; i <=30; i++){
            System.out.println(Thread.currentThread().getName() + "执行第"+i+"次！");
            //想让每1s执行一次循环
            try {
                Thread.sleep(1000); //1k毫秒 = 1s
                // 如果有人中断线程会发生异常
            } catch (InterruptedException e) {
                e.printStackTrace();
            } 
        }
    }
}

public class SleepDemo {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        Thread t = new Thread(myThread);
        t.start();
        Thread t1 = new Thread(myThread);
        t1.start();
    }
}
```

i.e. - 2: 

横向每隔1s打印出 a-z：

```java
public class Letter implements Runnable{
    char[] letter = new char[26];

    public Letter(){
        int a = 97;
        for(int i = 0; i < letter.length; i++){
            letter[i] = (char)(a+i);
        }
    }
    
    @Override
    public void run() {
        for(char e: letter){
            System.out.print(e);
            try {
                Thread.sleep(1000);
            } catch (InterruptedException interruptedException) {
                interruptedException.printStackTrace();
            }
        }
    }
}

public class SleepDemo {
    public static void main(String[] args) {
        Letter letter = new Letter();
        Thread thread = new Thread(letter);
        thread.start();
    }
}
```



### join:

Thread类方法，final方法，不能被重写。join() 表示加入，**抢先执行/抢占资源。 线程A调用join() 方法，那么其他线程要等待调用该方法的线程结束工作后才能执行。**

#### join():

```java
public final void join(){
}
```

抢占资源，等调用他的线程执行完毕之后，其他线程再进行执行， 会抛出InterruptedException需要try-catch处理

```java
public class MyThread extends Thread{
    public void run(){
        for(int i = 1; i <= 10; i++){
            System.out.println(getName() + "正在执行"+i+"次");
        }
    }
}

class JoinDemo{
    public static void main(String[] args) {
        MyThread mt = new MyThread();
        mt.start();
      	//original: 执行顺序是：mt和main线程随机执行
      	//current: 执行顺序是：mt抢占cpu资源，都执行完以后，main再继续执行
        try {
            mt.join(); // mt线程抢先执行
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        for(int i = 1; i <= 10; i++){
            System.out.println("main thread正在执行"+i+"次");
        }
        System.out.println("主线程运行结束！");
        
    }
}
```

#### join(millis):

调用join(millis)方法的线程，**在接下来的millis时间内，抢占cpu，时间过后，失去优先性继续随机执行。**

```java
public class MyThread extends Thread{
    public void run(){
        for(int i = 1; i <= 500; i++){
            System.out.println(getName() + "正在执行"+i+"次");
        }
    }
}

class JoinDemo{
    public static void main(String[] args) {
        MyThread mt = new MyThread();
        mt.start();
        try {
            mt.join(25); // mt线程抢先执行25millis时间，然后主线程和
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        for(int i = 1; i <= 20; i++){
            System.out.println("main thread正在执行"+i+"次");
        }
        System.out.println("主线程运行结束！");
    }
}
/**output：
...
Thread-0正在执行252次
Thread-0正在执行253次
Thread-0正在执行254次
Thread-0正在执行255次
Thread-0正在执行256次
main thread正在执行1次 // 抢占资源时间结束，开始随机
Thread-0正在执行257次
main thread正在执行2次
Thread-0正在执行258次
main thread正在执行3次
Thread-0正在执行259次
main thread正在执行4次
Thread-0正在执行260次
main thread正在执行5次
...**/
```



### 线程的优先级：

#### 优先级：

Java线程提供10个优先级，优先级可以使用

* 数字表示：1-10数字，数字越大优先级越高，超过范围会抛出异常；
* main方法的主线程默认优先级为5.
* 优先级常量表示：【优先级常量是Thread中定义的static final值，所以调用时用Thread帮助调用：Thread.MAX_PRIORITY】
  * MAX_PRIORITY: 表示最高10
  * MIN_PRIORITY: 表示最低1
  * NORM_PRIORITY: 表示普通normal优先级， 为默认优先级5

#### Thread优先级固定方法：

```java
public int getPriority(){}  // Thread中定义获取优先级的方法
public void setPriority(int newPriority){} // Thread中设置线程优先级的方法
```

```java
public class MyThread extends Thread{
    private String name;
    public MyThread(String name){
        this.name = name;
    }
    public void run(){
        for(int i = 1; i <= 10; i++){
            System.out.println("线程"+name+"正在运行"+i);
        }
    }
}

class PriorityDemo{
    public static void main(String[] args) {
        //获取main thread的优先级
        int mainPriority = Thread.currentThread().getPriority();
        System.out.println("main thread priority: "+mainPriority);
        MyThread mt1 = new MyThread("线程1");
        mt1.setPriority(10);
        mt1.setPriority(Thread.MAX_PRIORITY); // static final value
      	mt1.start();
        System.out.println("mt1 priority: "+mt1.getPriority());
    }
}
```

优先级的设置是和操作系统环境和cpu的工作环境是有关系的 i.e. 

```java
public class MyThread extends Thread{
    private String name;
    public MyThread(String name){
        this.name = name;
    }
    public void run(){
        for(int i = 1; i <= 50; i++){
            System.out.println("线程"+name+"正在运行"+i);
        }
    }
}

class PriorityDemo{
    public static void main(String[] args) {
        //获取main thread的优先级
        MyThread mt1 = new MyThread("线程1");
        MyThread mt2 = new MyThread("线程2");
        mt1.setPriority(Thread.MAX_PRIORITY); // static final value
        mt2.setPriority(Thread.MIN_PRIORITY);
        mt1.start();
        mt2.start();
    }
}
```

当mt1先被开启，然后是mt2的时候: 

```xml
线程线程1正在运行1
线程线程1正在运行2
线程线程1正在运行3
线程线程2正在运行1
线程线程1正在运行4
```

当mt2先被开启，output的结果依旧是随机的，虽然mt2比mt1优先级低，但是由于mt2先开启， mt2可能以快速的时间完成了工作，没有受到mt1的影响

sum up：在java中优先级高的线程不一定会比优先级低的先运行，取决于OS以及cpu的环境



## 同步&死锁：

### 多线程运行过程问题：

* 线程的运行顺序是不确定的，各个线程是通过竞争cpu时间而获得运行机会的。

* 各线程什么时候得到cpu时间，占用多久是不可预测的
* 一个正在运行的线程在什么地方被暂停是不确定的

多线程在某种情况下出现问题 i.e. 模拟银行，针对一个Bank账户，设立存款save 取款drawback两个线程，分别对bank进行操作，在一定程度上接续进行是没有问题的。但是当多用户针对Bank进行操作时，在线程执行的过程中会发生干扰，我们使用代码sleep方法模拟干扰；将sleep加在不同的位置上

```java
//Bank
public class Bank {
    private String account;
    private int balance;
    public Bank(String account, int balance){
        this.account = account;
        this.balance = balance;
    }

    public void setAccount(String account) {
        this.account = account;
    }

    public void setBalance(int balance) {
        this.balance = balance;
    }

    public String getAccount() {
        return account;
    }

    public int getBalance() {
        return balance;
    }

    @Override
    public String toString(){
        return "Bank [account:"+account+", balance"+balance+"]";
    }

    //存款 $100
    //由于干扰，每次在线程执行的过程中，使用sleep进行模拟；将sleep加在不同的位置上
    public void saveAccount(){
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        balance+=100;
        System.out.println("after saving: $"+balance);
    }

    //取款 $200
    public void drawAccount(){
        balance -= 200;
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("after drawback: "+ balance);
    }
}

//取款线程
public class DrawAccount implements Runnable{
    Bank bank;
    public DrawAccount(Bank bank){
        this.bank = bank;
    }

    @Override
    public void run() {
        bank.drawAccount();
    }
}
//存款线程
public class SaveAccount implements Runnable{
    Bank bank;
    public SaveAccount(Bank bank){
        this.bank = bank;
    }

    @Override
    public void run() {
        bank.saveAccount();
    }
}

//执行主方法
public class Test {
    public static void main(String[] args) {
        Bank bank = new Bank("1001",1000);
        //创建线程对象
        SaveAccount saveAccount = new SaveAccount(bank);
        DrawAccount drawAccount = new DrawAccount(bank);
        Thread saveThread = new Thread(saveAccount);
        Thread drawThread = new Thread(drawAccount);
        //启动线程
        saveThread.start();
        drawThread.start();
        //为了让存取款线程先执行，最后才是主线程的输出bank信息语句，给存取款线程join
        try {
            saveThread.join();
            drawThread.join();
            //save, draw线程发生随机
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(bank);
    }
}
//在sleep的干扰下，执行就会出现一定问题 --- 解决问题：同步线程
```



### 线程的同步/互斥：

在多线程同时操作时 i.e. 存取款，在一个线程工作的情况下，不允许其他线程对账户balance进行操作。需要将Bank对象进行锁定，使用关键字synchronized实现

#### synchronized：

* 用在成员方法

  ```java
  public synchronized void saveAccount(){}
  ```

* 静态语句块

  ```java
  public static synchronized void saveAccount(){}
  ```

* 语句块

  ```java
  synchronized(obj){
  }
  ```

Bank 例子应用：

```java
//存款 $100
//由于干扰，每次在线程执行的过程中，使用sleep进行模拟；将sleep加在不同的位置上
// 同步方法例子
public synchronized void saveAccount(){
    try {
        Thread.sleep(1000);
    } catch (InterruptedException e) {
        e.printStackTrace();
    }
    balance+=100;
    System.out.println("after saving: $"+balance);
}

//取款 $200
public void drawAccount(){
    synchronized (this){ // 同步语句块例子， 传入obj就是自身bank所以this
        balance -= 200;
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("after drawback: "+ balance);
    }
}
```



### 线程间通信：

i.e. 生产者消费者，Queue类作为容器，存储变量n初始化为0，两个线程维护变量n：生产者Producer类，消费者Consumer类，至少要有生产才能去消费，所以涉及线程间的通信。

要求像生产面包一样，生产一个消费一个，不能生产一次消费多次（缺货），也不能生产多次消费一次（滞销）

#### wait(): 

**使线程从Running变成Blocked阻塞状态，让其等待**

wait() 方法可以直接调用，需要使用try-catch进行InterruptedException的处理。在某种if condition的条件下，让线程进入等待。

但是存在危险，如果两个线程全部处于等待的状态，没有人更改条件，那么会造成死锁：

i.e. 例子：（代码中去掉两行notifyAll则是死锁）消费者线程在wait状态，生产者生产完成后更改flag，但是消费者还是处于wait，反之亦然，两个线程都在wait状态导致死锁。



**整个过程思路：容器的getter setter，双线程访问容器并且伴随着反复循环，以及main class method**

**在过程中，发现存在数字不匹配，生产1消费1生产2消费1生产3消费2.... 说明多个线程同时访问了上一个还没有生产完，但是又被消费了。解决方法是 同步 synchronized 更改和获取只能让单线程进行操作。**

**在过程中，又发现出现此类情况，生产2消费2生产3生产4消费4生产5消费5... 情况，没有达到生产一个消费一个的效果，所以使用boolean变量和wait让线程在指定的情况下进入等待的状态，从而完成线程间的通信，告诉彼此线程的完成程度。**

**在过程中，又发现两个线程彼此等待会发生死锁的情况，使用notify对应方法帮助线程进行唤醒。**

```java
//Queue 容器
public class Queue {
    private int n;
    // false时表示容器里是没有数据的，只能去生产不能消费。
    // true的时候可以被消费表示有，但是不能被生产。
    boolean flag = false;

    public Queue(){
        n = 0;
    }

    public synchronized void setN(int n) {
        if(flag){ // 容器中有数据，生产要等
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println("生产："+n);
        this.n = n;
        flag = true; // 容器中已经有数据
      	notifyAll(); // 状态更新，唤醒所有线程
    }

    public synchronized int getN() {
        if(flag == false){ // false时，没有，消费进入等待
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println("消费："+n);
        flag = false;
      	notifyAll(); // 状态更新，唤醒所有线程
        return n;
    }
}
//生产
public class Producer implements Runnable {
    //共享Queue类，所以设置Queue为属性，并且constructor赋值
    Queue queue;
    public Producer(Queue queue){
        this.queue = queue;
    }

    @Override
    public void run() {
        int i = 0;
        while (true){
            queue.setN(i++);
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
//消费
public class Consumer implements Runnable {
    Queue queue;
    Consumer(Queue queue){
        this.queue = queue;
    }

    @Override
    public void run() {
        while (true){
            queue.getN();
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
//Main
public class Test {
    public static void main(String[] args) {
        Queue queue = new Queue();
        // 启动线程
        new Thread(new Producer(queue)).start();
        new Thread(new Consumer(queue)).start();
    }
}
```

#### Notify(): 唤醒指定等待线程

#### notifyAll(): 唤醒所有等待线程



# 设计模式：

遇到常见问题的解决方案：23种

**创建型模式**： 单例模式，工厂方法模式，抽象工厂模式，原型模式

**结构型模式：** 桥接模式，代理模式，享元模式，外观模式，装饰器模式，组合模式，适配器模式

**行为型模式：** 备忘录模式，解释器模式，命令模式，中介者模式，观察者模式，策略模式，状态模式，模版方法模式，访问者模式，迭代子模式，责任链模式

## 创建型模式：

### 单例模式：

#### 特性：

**一个类有且只有唯一实例产生工作，且当前类可以自行实例化向整个系统提供**

关键点：

* private static field -> 声明class的全局唯一实体
* public static getter -> 系统对全局唯一实体的基本获取
* private constructor -> 自行创建能力，且避免其他类的实体化

##### 缺点：

扩展比较困难。如果实例化对象后长期不使用会被jvm默认进行垃圾回收，造成对象状态丢失

##### 使用场景：

创建对象时，占用资源过多，同时又需要使用该类对象

对系统内资源要求统一读写时，i.e.配置文件读写

当多个实例存在可能引起逻辑错误时，用来保持唯一 i.e. printer，叫号机。。



#### 饿汉式：

对象在类创建的过程（constructor中）实例化

不管用不用，先创建出来  -- 一种空间换时间的方式，在操作的时候速度是快的，但是存在周期长，类加载工作量大

```java
public class Singleton {
    //饿汉  声明同时初始化，也能确保
    private static Singleton uniqueSingleton = new Singleton();

    private Singleton(){
    }

    public static Singleton getInstance(){
        return uniqueSingleton;
    }
}
//Test
public class Test {
    public static void main(String[] args) {
        Singleton s1 = Singleton.getInstance();
        Singleton s2 = Singleton.getInstance();
        System.out.println("equals: "+ s1.equals(s2));  // return true 说明同一实体
    }
}
```

#### 懒汉式：

懒汉精髓：先不创建，等到用的时候在创建，也就是说等到static public method中实例化，也就是系统用的时候调用再创建

用时间换空间的编码形式

* 懒汉: 线程不安全。 -- 多线程同时进入判断为null则会初始化多个实例违背原则

```java
public class Singleton {
    //懒汉 - 不在声明同时初始化
    private static Singleton uniqueInstance;

    private Singleton(){
    }

    public static Singleton getInstance(){
        if(uniqueInstance == null){ // 检查是否被初始化
            uniqueInstance = new Singleton();
        }
        return uniqueInstance;
    }
}
```



#### 线程锁：

由于线程不安全，<u>在get method上**加锁 synchronized**保证一个时间点只有一个线程可以进入访问，从而避免反复实例化</u>

```java
public class SynSingleton {
    private static SynSingleton uniqueSynSingleton;

    private SynSingleton(){
    }

    public static synchronized SynSingleton getInstance(){
        if (uniqueSynSingleton == null){
            uniqueSynSingleton = new SynSingleton();
        }
        return uniqueSynSingleton;
    }
}
```





# Android

## android基本使用：

module 在android中是独立的项目，project是一个几个项目共同存在的区间 通常有相同的配置文件等。

<img src="Android-Java基础.assets/Screen Shot 2021-03-09 at 5.56.26 pm.png" alt="Screen Shot 2021-03-09 at 5.56.26 pm" style="zoom:50%;" />

我们正常新建出来的都是android的project，在每一个新建的project中都会默认创建一个叫“app”的module，后期也可以通过new->module创建，创建完成后会显示在和app同一个level中（通过点击Android系统文件夹可以查看）。删除module：从module-> open module setting -> 找到点击module 点击 - 左上减号 -> 之后再右键module -> delete。导入module -> 选择new import module -> 给出source directory

配置文件：

Project中：具体真实的在计算机中的物理路径

app中：【适用程序员逻辑】 

* manifest配置文件（所有的activity都要在此注册，Main通常注册好的，使用new->Activity 创建的话，是直接会被加入到manifest中的）
* java源文件
* res-resource资源目录（drawable图像图形相关用xml编写，mipmap放置图片资源，layout放置xml布局资源文件，values放置所有常量资源 i.e. 颜色字符串etc）

<img src="Android-Java基础.assets/Screen Shot 2021-03-09 at 6.00.37 pm.png" alt="Screen Shot 2021-03-09 at 6.00.37 pm" style="zoom:50%;" />

### Gradle：

android主流的编译工具

所有的gradle文件：

* 项目：
  * setting.gradle: 记录哪些module应该被加入编译过程
  * build.gradle: 配置应用到所有项目间
* Module：
  * build.gradle: 对于当前目录的配置。当和项目的build.gradle配置重复，则项目的会被覆盖（做sdk，依赖配置）

Gradle中的部分配置：在app/build.gradle中：

minSdkVersion：最小API level 不设置的话，默认是1，如果手机设备低于这个版本，则手机会阻止这个app的安装

compileSdkVersion：编译的SDK版本，默认是最新的

targetSdkVersion：目标版本，同一个项目在不同设备版本不同会有运行差别。处理在不同sdk版本中兼容问题，用于匹配运行程序的api行为

dependencies：依赖配置，依赖的库

### 快捷键：

* 提示：control+option+space
* 格式化代码：command+option+l
* 撤销：command+z  反撤销 command+shift+z
* 代码自动修正：option+enter
* 代码跳转：command+b
* 关键字全局搜索：command+shift+f   当前文档查找： command+f

### 调试技巧：

* 写日志：弊端：加入代码重新运行整个程序

* debug调试：断点

* 断点+日志：打断点，右键断点，取消suspend选择，选择evaluate and log，在下面加入要打印的表达式

  <img src="Android-Java基础.assets/Screen Shot 2021-03-10 at 10.52.37 am.png" alt="Screen Shot 2021-03-10 at 10.52.37 am" style="zoom:40%;" />

### 导入项目版本兼容问题：

通常有三个可能：

1. 导入项目的build.gradle和当前工具的不同，寻找下面标志，更改

```xml
dependencies{
	classpath 'com.android.tools.build:gradle:3.0.1'
}
```

2. Gradle-wrapper.properties - 在项目/gradle/wrapper/ 原因：对应路径没有找到对应的包，解决：尝试手动下载，最后一句通常为

   ```xml
   distributionUrl=https\://services.gradle.org/distributions/gradle-4.1-all.zip
   ```

   复制放在迅雷中去掉https后面的\:后手动下载

3. module中的build.gradle文件问题

### gradle更新问题：

* Error：Unable to tunnel through proxy. Proxy returns "HTTP/1.1 400 Bad Request"

  solution： 

  1. setting -> Build, Execution, Deployment > gradle-> use local gradle distribution -> add local path（android studio本地安装包路径中的gradle/m2repository/com/android/tools/build/gradle）选择版本高的

  2. Gradle0wrapper.properties中的distributionUrl中修改为当前工具的版本
  3. 查看本地gradle的版本号， 到项目中查找build.gradle中dependencies的classpath 将gradle改为对应的版本号

* gradle 一直处于更新状态

  solution：

  1. 项目gradle低于工具gradle，将工具关掉，找到工具对应的文件夹（AS安装目录中第一个gradle下的gradle版本号）使用文本编辑器打开gradle-wrapper.properites中的distributionUrl称为对应的版本，重开工具即可
  2. 工具升级了，但是项目还是高于工具，手动下载gradle版本，路径去掉s然后打开下载
  3. 有墙：将gradle-wrapper.properites中的distributionUrl中的https变成http

* Gradle project sync failed...

  ![Screen Shot 2021-03-10 at 3.34.48 pm](Android-Java基础.assets/Screen Shot 2021-03-10 at 3.34.48 pm.png)

  打开以后idead.log 找到最后就是原因，如果是没有对应sdk版本，可以在build.gradle中compileSdkVersion，buildToolsVersion, compilem, implementation...中修改版本

### 中文乱码：

* setting中file encoding -- IDE/Global encoding, Project encoding, file or director encoding和property file encoding 设置为支持中文i.e. UTF-8
* 单个java右键file encoding
* module的gradle中添加： compileOption.encoding="GBK"





## Activity：

每个activity都要在manifest文件中注册才能在app中显示出来，也可以直接使用new->activity创建会被直接加入到manifest中。或者手动加入：

```xml
<activity android:name=".SecActivity"></activity>
```

manifest中主页配置：表示打开app即为MainActivity的页面

```xml
<activity android:name=".MainActivity">
  <intent-filter>
    <action android:name="android.intent.action.MAIN" />
    <category android:name="android.intent.category.LAUNCHER" />
  </intent-filter>
</activity>
```

### 基础介绍：

Activity是一个可视的界面，AppCompatActivity是Activity的一个子类，所有的Activity都要继承于AppCompatActivity。

onCreate方法是Activity的初始化入口（放置所有的初始化设置），

```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);// link this class to layout xml file.
    }
}
```

链接activity和layout file的方式：setContentView(layoutResourceId); 

R.layout.xxxxactivity: layout文件夹下的xxxxactivity.xml文件，R是在package层面的一个被系统自动生成的class，对应着一个编码id，所以使用R.layout.xxxactivity在R class中对应一个id 【R：为每一个资源按照类别分配一个索引ID，使程序可以通过 **R.类别名.资源名** 去操作对应资源】

#### 关于文件目录

gen目录下的文件是adt自动生成的，不需要开发者维护

src存放所有java代码

res存放资源文件

assets存放随程序打开的文件是需要维护的。



### Manifest：

在android中，系统会将package作为应用程序唯一识别标识，所以在manifest的配置中要设置对应的package值。所有的activity都要在mainfest中进行注册才能在app中显示。在activity中Intent-filter查看哪个是启动页面。

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.testapplication">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".SecActivity"></activity>
        <activity android:name=".MainActivity">
            <intent-filter> //设置为启动页面
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```



### 布局：

布局文件名全部小写。

#### 布局种类：

##### 线性布局LinearLayout：

垂直布局/水平布局，如果有从左到右/上到下的逻辑规律就可以使用

定义线性布局：layout->new->layout resource file -> 命名layout file全小写可以_ 数字，数字不能开头，更改root element

**重要属性：**

* android:layout_width / android:layout_height: 对应值 match_parent / wrap_content / 直接给数值 "200dp(xml像素)/sp(字体)"

* android:layout_margin 外边距； android:layout_padding 内边距

* android:orientation: "vertical" / "horizontal"

* android:layout_weight: 权重，占比百分比，linear layout中特有的性质，**通常用在linear layout内部的元素上**，并且要把对应的宽高属性调整为 "0dp" (水平就是宽，垂直就调高)。对应值随意数字，表示分配比例不是具体像素 i.e. android:layout_weight="1"。如果并列有三个元素，其中一个定义了layout_weight的话，程序是先放置两个没有定义权重的，再用定义权重的元素进行填补。【等比分配父空间的剩余空间】

  * 如果想要两个元素水平均分，则可以把两个元素都设置为width="0dp" weight="1"	
  * 如果想要使用weight值正比例分配父空间剩余空间，需要将空间宽/高调整为 “wrap_content”
  * 如果想要使用weight反比例分配父空间剩余空间，将宽高调整为"match_parent"

  <img src="Android-Java基础.assets/Screen Shot 2021-03-11 at 3.43.38 pm.png" alt="Screen Shot 2021-03-11 at 3.43.38 pm" style="zoom:50%;" />

  <img src="Android-Java基础.assets/Screen Shot 2021-03-11 at 4.02.10 pm.png" alt="Screen Shot 2021-03-11 at 4.02.10 pm" style="zoom:50%;" />

* Android:layout_gravity: 重力，分清楚方向，如果在水平方向使用weight被定义的情况下，就不能再使用水平方向的重力了

  * 垂直方向的 bottom, top, center, centre_vertical 
  * 水平方向的 right, left, center_horizontal





##### 相对布局RelativeLayout：

位置和添加顺序无关，通过选取参照物，来决定在参照物的哪个位置，属性之间相互不冲突可以使用多个

附加：给一个控件添加id：android:id="@+id/xxxx"   引用一个控件的id："@id/xxxx" 【表示添加有 “+” 】

* 相对父容器：以下属性值为 true/false
  * android:layout_alignParentRight
  * android:layout_alignParentTop
  * android:layout_alignParentBottom
  * android:layout_alignParentLeft
  * android:layout_centerInParent
  * android:layout_centerHorizontal
  * android:layout_centerVertical
* 相对其他控件：以下属性值为 其他控件的id
  * 在参照物的某边：
    * android:layout_toRightOf
    * android:layout_toLeftOf
    * android:layout_above
    * android:layout_below
  * 和参照物的某边线对齐
    * android:alignTop
    * android:alignBottom
    * android:alignLeft
    * android:alignRight

Example:

<img src="Android-Java基础.assets/Screen Shot 2021-03-14 at 6.54.52 pm.png" alt="Screen Shot 2021-03-14 at 6.54.52 pm" style="zoom:50%;" />

暂时效果

<img src="Android-Java基础.assets/Screen Shot 2021-03-14 at 6.59.35 pm.png" alt="Screen Shot 2021-03-14 at 6.59.35 pm" style="zoom:33%;" />

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:orientation="horizontal"
        android:layout_weight="2"
        android:background="#f00">

        <RelativeLayout
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="2">
            
            <ImageView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:src="@mipmap/ic_launcher" />
            
            <TextView
                android:layout_width="match_parent"
                android:layout_height="60dp"
                android:text="复仇者联盟"
                android:layout_alignParentBottom="true"
                android:textSize="36sp"/>
        </RelativeLayout>

        <LinearLayout
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:orientation="vertical"
            android:layout_weight="1">

            <RelativeLayout
                android:layout_width="match_parent"
                android:layout_height="0dp"
                android:layout_weight="1"
                android:background="#ff0">
            </RelativeLayout>

            <RelativeLayout
                android:layout_width="match_parent"
                android:layout_height="0dp"
                android:layout_weight="1"
                android:background="#0f0">
            </RelativeLayout>
        </LinearLayout>
    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:orientation="horizontal"
        android:layout_weight="1"
        android:background="#0f0">
<!-- 因为要在下半部元素中的左上角添加icon所以内部元素适用relative layout-->

        <RelativeLayout
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:background="#ff0">
        </RelativeLayout>

        <RelativeLayout
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:background="#f0f">
            <ImageView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:src="@mipmap/ic_launcher" />
        </RelativeLayout>

        <RelativeLayout
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:background="#0ff">
            <ImageView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:src="@mipmap/ic_launcher" />
        </RelativeLayout>
    </LinearLayout>
</LinearLayout>
```







##### 帧布局FrameLayout：

<img src="Android-Java基础.assets/Screen Shot 2021-03-11 at 1.17.42 pm.png" alt="Screen Shot 2021-03-11 at 1.17.42 pm" style="zoom:33%;" />

一层叠在一层上，上方叠在下方如果上方过大会遮盖下方内容

##### 表格布局TableLayout：

<img src="Android-Java基础.assets/Screen Shot 2021-03-11 at 1.18.25 pm.png" alt="Screen Shot 2021-03-11 at 1.18.25 pm" style="zoom:33%;" />

##### 网格布局GridLayout：

<img src="Android-Java基础.assets/Screen Shot 2021-03-11 at 1.18.49 pm.png" alt="Screen Shot 2021-03-11 at 1.18.49 pm" style="zoom:33%;" />

##### 约束ConstraintLayout：

<img src="Android-Java基础.assets/Screen Shot 2021-03-11 at 1.38.04 pm.png" alt="Screen Shot 2021-03-11 at 1.38.04 pm" style="zoom:33%;" />

### 布局编码：

#### java代码实现

缺点：相对麻烦，例子是单独的View，如果在l1的基础上增加其他控件i.e. viewObject.addView(View view); ... 代码量大不直观

```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        //使用java实现布局编码
        //1.根布局为线性布局
        LinearLayout l1 = new LinearLayout(this); // context:指当前MainActivity
        //2.设置宽高
        l1.setLayoutParams(new LinearLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,
                ViewGroup.LayoutParams.MATCH_PARENT));
        //setLayoutParams()参数需要传入linearLayout.LayoutParams的object，创建时参数分别为宽高。
        //3.背景设置红色
        l1.setBackgroundColor(Color.RED);
        //4.指定此Activity的内容试图为该线性布局
        //setContentView(layout xml id / View view);
        setContentView(l1);
    }
}
```

#### xml实现

















