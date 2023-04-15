#  Java

---

## java运行机制

源文件(.java文件)-->javac编译-->字节码文件(.class文件)-->java运行-->结果

## JDK

jdk:java开发工具包

jdk = jre + java开发工具

jre(java运行环境) = jvm + java核心类库

## Java开发规范

## 数据类型

### 浮点数

浮点数=符号位+指数位+尾数位

### 字符

在java中，char的本质是一个整数，在输出时，是Unicode码对应的字符

字符型存储到计算机中，需要将字符对应的码值(整数)找出来

比如'a'

-  存储: 'a'--->码值97--->二进制--->存储
- 读取'a': 二进制--->97--->'a'--->显示

字符和码值的对应关系是通过字符编码表决定的

### 字符编码表

ASCII:一个字节表示，一共128个字符

Unicode:固定大小的编码，字母和汉字统一占2个字节，浪费空间

utf-8:大小可变的编码，字母1个字节，汉字3个字节

gbk:可表示汉字且范围更广，字母1个字节，汉字2个字节

## 原码、反码、补码

负数的反码=原码符号位不变，其他位取反

负数的补码=反码+1

- #### 计算机在运行时，都是以补码的方式来计算

## 算数运算符%(取模运算)

a % b = a - a / b * b;    (a为整数)

a % b = a - (int)a / b * b;  (a为浮点数)

## 排序

### 冒泡排序

算法描述

1. 比较相邻的元素，如果第一个比第二个大，就交换它们两个
2. 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对，这样在最后的元素应该会是最大的数
3. 针对所有的元素重复以上的步骤，除了最后一个
4. 重复步骤1~3，直到排序完成

```java
int[] array = {6, 7, 5, 4, 3, 2, 1};
int temp;
for (int i = 0; i < array.length - 1; i++) {
    for (int j = 0; j < array.length - 1 - i; j++) {
        if (array[j] > array[j + 1]) {
            //交换两数位置
            temp = array[j];
            array[j] = array[j + 1];
            array[j + 1] = temp;
        }
    }
}
//输出
for (int i = 0; i < array.length; i++) {
            System.out.println(array[i]);
        }
```

## 数组

数组属于引用类型，数组型数据是对象(Object)

#### 二维数组

声明：int[] [] a 或 int a[] [] 或 int[] a[]

## 类和对象

类是一种数据类型

对象是一个具体的实例

## 内存分配

栈：一般存放基本数据类型（局部变量）

堆：存放对象

方法区：常量池，类加载信息

#### 类加载情况

1. 创建实例对象
2. 创建子类对象实例时，父类会被加载
3. 使用类的静态成员

## 访问修饰符

控制方法和成员变量的访问权限(范围)

public：公开

protected：对子类和同一个包公开

默认：对同一个包公开

private：只有类本身

## 对象创建流程

1. 在方法区加载类信息，只加载一次
2. 在堆中分配空间
3. 完成对象初始化(默认初始化-->显示初始化-->构造器初始化)
4. 把对象在堆中的地址返回给对象名(对象的引用)

## 面向对象的三大特征

封装、继承、多态

## 封装

封装就是把抽象出的数据[属性]和对数据的操作[方法]封装到一起。数据被保护在内部，程序的其他部分只有通过被授权的操作[方法]，才能对数据进行操作

## 继承

1. 子类必须调用父类的构造器，完成父类的初始化
2. 当创建子类对象时，默认会调用父类的无参构造器，如果父类没有无参构造器，就必须在子类的构造器中用super去指定一个父类的带参构造器完成堆父类的初始化

## 方法重写与重载

#### 方法重写override

1. 子类方法的方法名和参数列表与父类一致
2. 子类方法的返回类型要与父类的一致，或是父类返回类型的子类
3. 子类方法不能缩小父类方法的访问范围

#### 方法重载overload

在同一个类中，方法名相同，形参列表不同

## 多态

方法或对象具有多种形态，它是建立在封装和继承基础之上的

#### 方法的多态

重写、重载

#### 对象的多态

1. 一个类型的编译类型和运行类型可以不一致(Animal animal = New Dog();编译类型是Animal,运行类型是Dog)
2. 编译类型在定义对象时就已经定了，不能改变，但运行类型可以改变(animal = New Cat();)
3. 编译类型看 = 左边，运行类型看 = 右边

#### 细节

#### 向上转型

1. 向上转型：父类的引用指向子类的对象
2. 不能调用子类中的特有成员

#### 向下转型

1. 只能强转父类的引用，不能强转父类的对象
2. 语法：子类类型 引用名 = （子类类型）父类引用；
3. 父类的引用必须指向当前目标类型的对象
4. 向下转型后，可以调用子类类型中的所有成员

#### instanceof比较操作符

判断对象的运行类型是否为XX类型或是XX类型的子类型

#### 动态绑定

当调用对象方法的时候，该方法会和该对象的内存地址/运行类型绑定

当调用对象属性时，没有动态绑定机制

## 比较 == 和 equal

==：既可以判断基本类型，也可以判断引用类型

    如果判断基本类型，则判断值是否相等
    
    如果判断引用类型，则判断地址是否相等

equal：只能判断引用类型

		  默认判断地址是否相同，子类中往往重写该方法，用于判断内容是否相同
	
	 	 String str1,str2;  str1.equals(str2)  若str1 = null会报错

## 类变量（静态变量）

static修饰

访问方式：类名.类变量名

               对象名.类变量名

类变量是类加载时就初始化的，它的生命周期随着类的加载开始，随着类的消亡而销毁

## main方法的理解

1. java虚拟机调用main方法，方法的访问权限必须是public
2. java虚拟机调用main方法是不必创建对象，所以用static修饰
3. main方法接收String类型的数组参数，该数组保存执行java命令时传递给所运行的类的参数

## 代码块

代码块又叫初始化块，属于类中的成员，类似于方法，将逻辑语句封装在方法提中，通过{}包围起来。但和方法不同，没有方法名，没有返回值，没有参数，只有方法体，而且不用通过对象或类显示调用，而是在加载类的时候或者创建对象的时候隐式调用。   

[修饰符]{代码}；

#### 细节

- 修饰符可选，但只能写static
- ；可写可不写
- 代码块的调用优先于构造器,静态代码块和静态属性平级，谁在前先调用谁

- 如果是静态代码块，作用是对类进行初始化，随着类的加载而执行只会执行一次，普通代码块每创建一个对象就执行


类被加载的时候

1. 创建读一下实例时（new）
2. 创建子类对象实例，父类会被加载
3. 使用类的静态成员

## 单例模式

单例：采取一定的方法，保证在整个软件系统中，对某个类只能存在一个对象实例，并且该类只提供一个取得其对象实例的方法

单例模式：1.饿汉式   2.懒汉式

#### 饿汉式

1. 构造器私有化（防止直接new拿到对象）

   ```java
   private Test(){}
   ```

2. 在类的内部创建对象

   ```java
   private static Test test = new Test();
   ```

3. 向外暴露一个静态的公共方法（getInstance）

   ```java
   public static Test getTest() {
       return test;
   }
   ```

在类加载式创建，可能存在资源浪费问题

#### 懒汉式

1. 构造器私有化

   ```
   private Test(){}
   ```

2. 定义一个static静态对象

   ```java
   private static Test test;
   ```

3. 提供一个public的static方法，返回对象

```java
public static Test getInstance(){
        if (test == null){
            test = new Test();
        }
        return test;
   }
```

线程安全问题

## final

用途

1. 不希望类被继承时
2. 不希望父类的某个方法被子类覆盖或重写
3. 不希望某个属性的值或局部变量被修改

final修饰的属性在定义时必须初始化；可以先定义，在构造器或代码块中再赋值

如果final修饰的属性是静态的，则初始的位置能是定义时或静态代码块

final和static一起使用，不会导致类加载

包装类是final类，不能被继承

## 抽象类

1. 抽象类不能被实例化
2. 如果一个类继承抽象类，那它必须实现抽象类的所有抽象方法，除非它自己声明为abstract类
3. 当一个类中有抽象方法，该类必须声明为abstract类

## 接口

1. jdk8以后，能有默认实现方法，需要用default修饰，也能有静态方法
2. 接口不能被实例化
3. 接口中的方法默认public abstract修饰
4. 一个普通类实现接口，必须实现接口中的所有方法
5. 接口中的属性默认public static final修饰
6. 接口中的属性访问 接口名.属性名
7. 接口可以继承其他接口
8. 接口的修饰符只能时public或默认

接口在一定程度上实现代码解耦[接口规范性+动态绑定]

## 内部类

一个类的内部有完整的嵌套另一个类结构,被嵌套的类称为内部类;内部类可以直接访问私有属性,并且可以体现类与类之间的包含关系

### 分类

定义在外部类局部位置上（比如方法内）

1. 局部内部类（有名类）
2. 匿名内部类（没有类名）

定义在外部类的成员位置上

1. 成员内部类（无static修饰,定义在外部类的成员位置）
2. 静态内部类（有static修饰）

#### 局部内部类

1. 定义在外部类的局部位置，通常在方法
2. 不能添加访问修饰符，但是能用final修饰
3. 可以直接访问外部类的所有成员，包含private
4. 作用域在方法体或代码块中
5. 本质仍然是一个类
6. 内部类访问外部类成员，使用 外部类名.this.成员

#### 匿名内部类

语法: new 类或接口(){};

```java
//匿名内部类
/* class OuterClass$1 implements A{
            @Override
            public void say() {
                System.out.println("B");
            }
}
编译类型:接口A
运行类型:匿名内部类OuterClass$1
*/
new A(){
            @Override
            public void say() {
                System.out.println("B");
            }
        }.say();

interface A{
    void say();
}
```

#### 成员内部类

外部其他类调用成员内部类的方式

- 外部类名.内部类名 对象名 = 外部类对象.new 内部类名()

```java
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();
```

- 在外部类中编写方法返回内部类对象

- ```java
  Outer.Inner inner = new Outer().new Inner();静态内部类
  ```

#### 静态内部类

外部其他类调用静态内部类的方式

```java
Outer.Inner inner = new Outer.Inner();
```

## 枚举

枚举是一组常量的集合，它是特殊的类，只包含一组有限的特定的对象

#### 自定义枚举类

构造器私有化

去掉set方法

定义对象

```java
private Season(String name){this.name = name}
public String getName(){return name}
public final static Season SPRING = new Season("春");
public final static Season SUMMER = new Season("夏");
public final static Season AUTUMN = new Season("秋");
public final static Season WINTER = new Season("冬");
```

#### enum关键字实现枚举

1. enum替代class
2. 多个对象","间隔
3. 常量对象写在最前面

```java
enum Season{
SPRING("春"),SUMMER("夏"),AUTUMN("秋"),WINTER("冬");
String name;
private Season(String name){this.name = name}
public String getName(){return name}
}
```

#### 细节

1. 使用enum关键字，默认继承Enum类，而且是final类
2. 如果使用无参构造器创建枚举对象，则实参列表和（）可以省略

#### 枚举方法

枚举名访问

ordinal：返回枚举对象的次序/编号，从0开始

values：返回一个含有所有枚举对象的数组

valueOf：将字符串转换成枚举对象

```java
Season spring = Season.valueOf("Spring");
```

compareTo：比较枚举对象的编号，返回编号之差

## 注解

也被称为元数据，用于修饰解释 包、类、方法、属性、构造器、局部变量等数据信息

不影响程序逻辑，但能被编译或运行

@Deprecated：用于表示某个程序元素（类、方法等）已过时

@SuppressWarings：抑制编译器警告

@interface：注解类

#### 元注解

Retention：指定注解的作用范围SOURCE、CLASS、RUNTIME

Target：指定注解可以在那些地方使用

Documented：指定该注解是否会在javadoc体现

Inherited：子类会继承父类注解

## 异常

```Java
try{}
catch{Exception e}
finally{}
```

- 系统发生异常时，系统将异常封装成Exception对象，传递给catch
- 不管try代码块是否有异常发生，始终要执行finally，通常用来释放资源
- 如果try代码块有多个异常，可以使用多个catch来捕获，但子类一次要写在父类异常前
- 如果没有显示地使用try catch或throws，默认采用throws
- 子类重写父类方法时，所抛出的异常与父类一致或时父类抛出的异常的子类

throws  异常处理的一种方式 ，在方法声明处，后面跟异常类型

throw  手动生成异常处理的关键字，在方法体中，后面跟异常对象

#### 自定义异常

继承Exception：属于编译异常

继承RuntimeException：属于运行异常

## 包装类

针对8种基本数据类型相应的引用类型

jdk5一起，收到装箱和拆箱

#### 手动装箱  基本数据类型--->包装类型

```java
int i = 10;
Integer i1 = new Integer(i);
Integer i2 = Integer.valueOf(i);
```

#### 手动拆箱  包装类型--->基本数据类型

```java
Integer j = new Integer(100);
int j1 = j.intValue();
```

#### 自动装箱

```java
int n1 = 10;
Integer n2 = ni;//底层使用Integer.valueOf()
```

#### 自动拆箱

```java
int n3 = n2;
```

#### 包装类--->String

```java
Integer i;
String str = i + "";
String str2 = i.toString();
String str3 = Integer.valueOf(i);
```

#### String--->包装类

```java
String str = "1345";
Integer i1 = str.parseInt(str);
Integer i2 = new Integer(str);
```

#### String

1. 字符串常量对象使用双引号括起来的字符序列   "你好"
2. 字符串的字符使用Unicode字符编码，一个字符（不区分字母或汉字）占两个字节
3. 字符串的本质是char数组
4. String有属性  private final char value[],value是一个final类型，value指向的地址不可修改

##### 创建String对象

方式一：String str1 = "abc";

方式二：String str2 = new String("abc");

方式一：先从常量池查看是否有"abc"的数据空间，如果有则直接指向，如果没有就重新创建然后指向，str1最终指向的是常量池的空间地址

方式二：先在堆中创建空间，里面维护了value属性，指向常量池的abc空间，如果常量池没有abc空间，则重新创建，如果有，重新通过value指向，str2最终指向的是堆中的空间地址

```java
String str = "Hel"+"lo";//创建了一个对象  --->String str = "Hello";
```

```java
String str1 = "Hello";
String str2 = "abc";
String str3 = str1 + str2;/*1.创建StringBuilder对象 StringBuilder sb = new StringBuilder()  2.sb.append(Hello)  3.sb.append(abc)  
4.String str3 = sb.toString()  */
String str4 = "Hello"+"abc";//==>等价String str4 = "Helloabc";

```

##### String方法

equalsIgnoreCase//忽略大小写，判断内容是否相同

indexOf//获取字符在字符串中第一次出现的索引，从0开始，若找不到，就返回-1

lastIndexOf//获取字符在字符串中最后一次出现的索引，从0开始，若找不到，就返回-1

substring//截取指定范围的子串，substring(index)从index处截取之后所有内容substring(start,end)从start开始，截取到位置end-1   区间[ )

trim//去前后空格

charAt//获取某索引处的字符

toUpperCase//转换成大写

toLowerCase//转换成小写

concat//拼接字符串

replace//replace(A,B)  将所有的A替换成B

split//split(",") 以，为标准对字符串分割，返回一个数组

toCharArray//将字符串转换成字符数组

compareTo//比较字符串大小，若长度不同，返回长度的差值，若相同，前者大，返回正数

format//String.format("姓名%s成绩%d",name,score)  占位符%s 字符串  %.2f 保留两位小数且四舍五入

#### StringBuffer

StringBuffer是可变长度的

父类AbstractStringBuilder中有属性 char[] value  存放在堆中

###### StringBuffer方法

append//追加

delete//delete(1,5)   删除1-4的字符，[1,5)

indexOf

insert

#### StringBuilder

非线程安全，用于字符串缓冲区被单个线程使用时

#### String、StringBuffer、StringBuilder比较

StringBuffer、StringBuilder代表可变字符序列

String：不可变字符序列，效率低，复用率高

StringBuffer：效率较高（增删），线程安全

StringBuilder：效率最高，线程不安全

#### (String)、toString、String.valueOf()比较

(String)：需要保证类型能转成String类型

toString：需要保证调用这个方法的类、方法、变量不为null，否则会报空指针

String.valueOf()：这个方法在使用的时候是有些特殊的。⼀般情况下，如果是确定类型的null传入，返回的是字符串“null”，而如果直接传入null，则会发生错误(String.valueOf(null))。

#### 日期

Date:精确到毫秒

```java
// 获取当前时间:
Date date = new Date();
System.out.println(date.getYear() + 1900); // 必须加上1900
System.out.println(date.getMonth() + 1); // 0~11，必须加上1
System.out.println(date.getDate()); // 1~31，不能加1
// 转换为String:
System.out.println(date.toString());
// 转换为GMT时区:
System.out.println(date.toGMTString());
// 转换为本地时区:
System.out.println(date.toLocaleString());
```

##### 格式化日期格式：

```java
Date d = new Date();
SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日  hh:mm:ss E");
String str = sdf.format(d);
```

##### Calendar

```java
// 获取当前时间:
Calendar c = Calendar.getInstance();
int y = c.get(Calendar.YEAR);
int m = 1 + c.get(Calendar.MONTH);//返回的月份要+1
int d = c.get(Calendar.DAY_OF_MONTH);
int w = c.get(Calendar.DAY_OF_WEEK);
int hh = c.get(Calendar.HOUR_OF_DAY);
int mm = c.get(Calendar.MINUTE);
int ss = c.get(Calendar.SECOND);
int ms = c.get(Calendar.MILLISECOND);
//返回的星期要特别注意，1~7分别表示周日，周一，……，周六
```

##### 问题

可变性：像日期和时间这样的类应是不可变的

偏移性：Date中的年份从1900开始，月份从0开始

格式化：格式化只对Date有用，Calendar无用

非线程安全，不能处理润秒（每隔两天多1s）

LocalDate（日期）

LocalTime（时间）

LocalDateTime（日期时间）:LocalDateTime dt = LocalDateTime.now(); // 当前日期和时间

格式化日期格式：DateTimeFormatter 对象名 = DateTimeFormatter.ofPattern("yyyy年MM月dd日")

```java
// 自定义格式化:
DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy/MM/ddHH:mm:ss");//2022/06/20 15:25:02
// 用自定义格式解析:
LocalDateTime dt2 = LocalDateTime.parse("2019/11/30 15:16:17", dtf);//2019-11-30T15:16:17

		LocalDateTime now = LocalDateTime.now();
        System.out.println(now);
//2023-03-30T21:13:02.284
        DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("yyyy/MM/dd HH");
        String format = dateTimeFormatter.format(now);
        System.out.println(format);
//2023/03/30 21  将DateTimeFormatter类型的日期转化成自定义类型的日期
        System.out.println(LocalDateTime.parse("2023/03/30 21", dateTimeFormatter));
//2023-03-30T21:00 将与DateTimeFormatter定义的日期格式一样的日期字符串转化成DateTimeFormatter类型
```

Instant时间戳

类似于Date

Instant-->Date

Date date = Date.from(instant);

Date-->Instant

Instant instant = new Date().toInstant();

## 集合

#### 单列集合、双列集合

Collection 接口的两个子接口List、Set ，实现的是单列集合

Map 接口的实现子类 是双列集合，存放key---value

#### Collection接口实现类特点

1. 有些Collection实现类能存放重复元素，有些不行
2. 有些Collection实现类有些是有序的(List)，有些是无序的(Set)
3. Collection接口没有直接的实现子类，是通过它的子接口List和Set实现

#### Collection接口遍历元素对象

1.使用Iterater(迭代器)

##### Iterater接口方法

hasNext()：判断是否还有下一个元素

next()：1、下移  2、将下移以后集合位置上的元素返回

在调用next()方法前要先调用hasNext()，若不调用且下一条记录无效，调用next()会抛出异常

2.增强for循环(底层是迭代器)

#### List

1. 元素有序且可重复
2. 每个元素都有其对应的元素索引

##### ArrayList

线程不安全，执行效率高

ArrayList中维护了一个Object类型的数组elementData     transient Object[] elementData//transient 表示该属性不会被序列化

当创建ArrayList对象时，若使用无参构造器，则初始elementData容量为0，第一次添加，则扩容为10，若需再次扩容，则扩容为1.5倍；若使用指定大小的有参构造器，则初始elementData容量为指定大小，若需再次扩容，则扩容为1.5倍

##### Vector

线程安全（同步）

扩容与ArrayList类似，但扩容是2倍 

##### LinkedList

底层实现类双向列表和双端队列特点

线程不安全

链表：三个属性 prev、next、item

增删效率高，改查效率低

#### Set

无序且无索引

不允许重复元素，至多包含一个null

##### HashSet

执行add方法后会返回一个boolean值

底层维护了一个 数组+单向链表+红黑树

1. HashSet底层是HashMap
2. 第一次添加时，table数组扩容到16，如果table数组使用到了临界值（容量*0.75），会扩容到原来的2倍[(12,16)-->(13,32)]
3. 添加一个元素时，先获取元素的hash值，hash值-->索引值，找到存储数据表table，看这个索引位置是否已经存放有元素，如果没有，直接存放，如果有，调用equals比较，如果相同，则放弃添加，如果不同，则添加到最后。
4. java8中，如果链表的元素个数>=TREEIFY_THRESHOLD（默认为8），并且table的大小>=MIN_TREEIFY_CAPACITY（默认64）就会进行树化（红黑树）                      
(8,16)-->(9,32)-->(10,64)-->(11,64)Node---TreeNode树化
##### LinkedHashSet

LinkedHashSet是HashSet子类

LinkedHashSet的底层是LinkedHashMap，底层维护了一个 数组(HashMap$Node[]  存放的元素是LinkedHashMap$Entry)+双向链表

使用链表维护元素次序,使元素看上去有序

不允许重复元素

节点有属性before、after

##### TreeSet

使用无参构造器时有默认排序方式

去重机制：如果传入一个Comparator匿名对象，就用实现的compare()方法去重，如果方法返回0，就认为是相同的元素/数据，就不添加，如果没有传入一个Comparator匿名对象，则以添加的对象实现的Comparable接口的CompareTo()方法去重

#### Map

key相同时，value替换

key和value可以为null，key为null只能有一个

为了方便遍历，会创建entrySet集合，该集合存放的元素类型为Entry，而一个Entry对象有k、v,即Set<Map.Entry<K,V>> entrySet

entrySet中，定义的类型是Map.Entry，实际存储的类型是HashMap$Node（Node<K,V> implements Map.Entry<K,V>）

HashMap线程不安全

##### 遍历

1. map.keySet()拿到key的集合   Set set = map.keySet();
2. map.values()拿到value的集合   Collection values = map.values();
3. map.entrySet()拿到K-V的集合

```java
//for each
Set set = map.entrySet();
for (Object o :set) {
Map.Entry m = (Map.Entry) o;
System.out.println("key="+m.getKey()+""+"value="+m.getValue());  }

//Iterator
Iterator iterator = set.iterator();
while (iterator.hasNext()) {
Object obj =  iterator.next();
Map.Entry entry = (Map.Entry) obj;
System.out.println("key="+entry.getKey()+""+"value="+entry.getValue());}
```

##### HashTable

key和value都不能为null

HashTable线程安全

初始大小11，到达临界值后扩容，扩容：容量*2+1

#### 比较Compare

```java
Book[] books = new Book[4];
        books[0] = new Book("红楼梦", 100);
        books[1] = new Book("金瓶梅新", 90);
        books[2] = new Book("青年文摘20年", 5);
        books[3] = new Book("java从入门到放弃", 300);
        Arrays.sort(books, new Comparator<Book>() {
            @Override
            public int compare(Book o1, Book o2) {
                int n1 = o1.getPrice();
                int n2 = o2.getPrice();
                return n1 - n2;
            }
        });

        /*Book.PriceCompare(books, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                int n1 = (Integer) o1;
                int n2 = (Integer) o2;
                return n1 - n2;
            }
        });*/
        System.out.println(Arrays.toString(books));
/*
        Book.NameCompare(books, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                int n1 = (Integer) o1;
                int n2 = (Integer) o2;
                return n2 - n1;
                */
                /*String s1 = (String) o1;
                String s2 = (String) o2;
                return s2.compareTo(s1);*//*
            }
        });
        System.out.println(Arrays.toString(books));*/



Book类
public class Book {
    private String name;
    private int price;

    public Book() {
    }
    public Book(String name, int price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getPrice() {
        return price;
    }

    public void setPrice(int price) {
        this.price = price;
    }

    public static void PriceCompare(Book[] book, Comparator comparator) {
        Book book1;
        for (int i = 0; i < book.length - 1; i++) {
            for (int j = 0; j < book.length - 1 - i; j++) {
                if (comparator.compare(book[j].getPrice(), book[j + 1].getPrice()) > 0) {
                    book1 = book[j];
                    book[j] = book[j+1];
                    book[j+1] = book1;
                }
            }
        }
    }
    public static void NameCompare(Book[] book, Comparator comparator) {
        Book book1;
        for (int i = 0; i < book.length - 1; i++) {
            for (int j = 0; j < book.length - 1 - i; j++) {
                if (comparator.compare(book[j].getName().length(), 
                                       book[j + 1].getName().length()) > 0) {
                    book1 = book[j];
                    book[j] = book[j+1];
                    book[j+1] = book1;
                }
            }
        }
    }

    @Override
    public String toString() {
        return "Book{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }
}
```



#### 工具类Collections

shuffle：随机排序

swap(List,int,int)：交换指定位置处的元素

frequency：返回指定集合中指定元素出现的次数

copy(List dest,List src)：将src内容复制到dest

## 泛型

#### 声明:interface 接口<T>{}        class 类 <K,V>{}
1. T、K、V是引用类型
2. 在给泛型指定具体类型后，可以传入该类型或其子类类型
3. ArrayList arrayList = new ArrayList();<===>ArrayList<Object> arrayList = new ArrayList<>();  默认泛型是Object
4. 编译时，检查添加的元素类型，提高安全性，减少类型转化次数
5. 静态方法中不能使用类的泛型(class A<S>{public static void hi(S s){}})
6. 泛型不具备继承性  List<Object> list=new ArrayList<String>();//错误

ArrayList<T>  表示存放到集合中的元素是T,遍历时可以直接取出T类型而不是Object

#### 自定义泛型方法

修饰符 <T,E...>返回类型 方法名(参数列表//T t,E e...){}

```java
public <T> void hi(T t) {}
public static <K> void cry(K k) {}
```

若修饰符后没有 <T,E...> ,则该方法不是泛型方法，只是使用了泛型

#### 通配符

1. <?>支持任意泛型类型
2. <? extends A>支持A类及A类的子类，规定了泛型的上限
3. <? super A>支持A类及A类的父类，不限于直接父类，规定了泛型的下限

#### 擦拭法

Java语言的泛型实现方式是擦拭法（Type Erasure）。所谓擦拭法是指，虚拟机对泛型其实一无所知，所有的工作都是编译器做的

- 编译器把类型`<T>`视为`Object`；
- 编译器根据`<T>`实现安全的强制转型。

使用泛型的时候，我们编写的代码也是编译器看到的代码：

```java
Pair<String> p = new Pair<>("Hello", "world");
String first = p.getFirst();
String last = p.getLast();
```

而虚拟机执行的代码并没有泛型：

```java
Pair p = new Pair("Hello", "world");
String first = (String) p.getFirst();
String last = (String) p.getLast();
```

Java的泛型是由编译器在编译时实行的，编译器内部永远把所有类型`T`视为`Object`处理，但是，在需要转型的时候，编译器会根据`T`的类型自动为我们实行安全地强制转型

使用类似`<? extends Number>`通配符作为方法参数时表示：
- 方法内部可以调用获取`Number`引用的方法，例如：`Number n = obj.getFirst();`；
- 方法内部无法调用传入`Number`引用的方法（`null`除外），例如：`obj.setFirst(Number n);`。
即一句话总结：使用`extends`通配符表示可以读，不能写。

## 线程

#### 程序、进程和线程

程序：程序是指令的有序集合

进程：进程是运行中的程序

线程：线程由进程创建，是进程的一个实体

和多线程相比，多进程的缺点在于：

- 创建进程比创建线程开销大，尤其是在Windows系统上；
- 进程间通信比线程间通信要慢，因为线程间通信就是读写同一个变量，速度很快。

而多进程的优点在于：

多进程稳定性比多线程高，因为在多进程的情况下，一个进程崩溃不会影响其他进程，而在多线程的情况下，任何一个线程崩溃会直接导致整个进程崩溃。

#### 并发与并行

并发:同一时刻，多个任务交替执行，即单核cpu实现多任务就是并发

并行:同一时刻，多个任务同时执行

#### 创建线程

- 继承Thread类，重写run方法

```java
class B extends Thread{
    @Override
    public void run() {
        while (true){
            System.out.println("Run");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
    
    B b = new B();
        b.start();
```

- 实现Runable接口，重写run方法

```java
class C implements Runnable{
    @Override
    public void run() {
        while (true){
            System.out.println("Run");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

		C c = new C();
        Thread thread = new Thread(c);
        thread.start();
```

star()方法调用star0()(jvm调用star0())方法后，该线程不一定会立马执行，只是将线程变成了可运行状态，具体执行实际取决于cpu，由cpu统一调度

#### 线程终止

- 线程完成任务后会自动退出
- 通过变量来控制run方法退出的方式停止线程，即通知方式
- 因为未捕获的异常导致线程终止

#### 方法

interrupt：中断线程
setName：设置线程名称，使之与参数name相同
sleep：让线程休眠
yield：让出cpu，让其他线程执行，不一定成功
join：线程的插队。插队的线程插入成功，就要先执行完插入的线程的所有任务

##### interrupt、interrupted、isinterrupted

interrupt：向一个线程发送中断请求，请求结果是将被请求线程的中断标志位设置为true。需要注意的是，interrupt()并不会直接中断线程，而是仅仅向一个线程发送中断请求，至于是否会被中断，要看被请求线程是否检查了中断标志位并对其做出响应。如果被中断线程处于sleep/join/wait状态时被请求中断，就会抛出一个InterruptedException中断异常，抛出中断异常后中断标志位会被恢复为false，这就会导致无法正确响应中断请求，若要正确响应则需要额外的代码

```java
MyThread t1 = new MyThread();
        t1.start();
        Thread.sleep(1000);
        t1.interrupt();

class MyThread extends Thread {
    @Override
    public void run() {
        while (!Thread.currentThread().isInterrupted()) {
            try {
                sleep(5000);
            } catch (InterruptedException e) {
                System.out.println("InterruptedException happened");
                /*Thread.currentThread().interrupt();
           这行代码让线程捕获中断异常后再重新自己把中断标志位置为true，最终程序可以正常结束*/
            }
            System.out.println(Thread.currentThread().isInterrupted());
        }

        System.out.println("t1 stopped");
    }
}
```

interrupted：这是一个静态方法，它返回调用线程的中断标志位的状态，并将中断标志位置为false

isinterrupted：实例方法，返回线程是否已经中断的状态，它没有清理中断状态的机制

#### 守护线程

为其他线程服务的线程。当所有用户线程结束，守护线程自动结束

thread.setDaemon(true);//在start()前设置

#### 线程的状态

- New：尚未启动的线程处于此状态。 新创建的线程，尚未执行； 
- Runnable：在Java虚拟机中执行的线程处于此状态。
- Blocked：被阻塞等待监视器锁定的线程处于此状态。 运行中的线程，因为某些操作被阻塞而挂起；
- Waiting：正在等待另一个线程执行特定动作的线程处于此状态。 运行中的线程，因为某些操作在等待中；
- Timed Waiting：正在等待另一个线程执行动作达到指定等待时间的线程处于此状态。 运行中的线程，因为执行`sleep()`方法正在计时等待；
- Terminated：已退出的线程处于此状态。 线程已终止，因为`run()`方法执行完毕。

#### 线程同步

在多线程编程，一些敏感数据不允许被多个线程同时访问，此时使用同步访问技术，保证数据在任何同一时刻，最多有一个线程访问，以保证数据的完整性

##### 同步代码块

```java
synchronized(对象) {//得到对象的锁，才能操作同步代码块
    //需要被同步的代
}
```

synchronized也能声明在方法中，表示整个方法为同步方法

###### 同步方法

静态：锁为当前类本身

非静态：锁为当前对象

##### volatile

1. 读主内存到本地副本；
2. 操作本地副本；
3. 回写主内存。
4. 保证时效性而不是原子性

#### 不需要synchronized的操作

JVM规范定义了几种原子操作：

- 基本类型（`long`和`double`除外）赋值，例如：`int n = m`；
- 引用类型赋值，例如：`List<String> list = anotherList`。

`long`和`double`是64位数据，JVM没有明确规定64位赋值操作是不是一个原子操作，不过在x64平台的JVM是把`long`和`double`的赋值作为原子操作实现的。

单条原子操作的语句不需要同步，但如果是多行赋值语句，就必须保证是同步操作

#### 死锁

两个线程各自持有不同的锁，然后各自试图获取对方手里的锁，造成了双方无限等待下去，这就是死锁。死锁发生后，没有任何机制能解除死锁，只能强制结束JVM进程。

如何避免死锁：线程获取锁的顺序要一致

```java
if (t) {
    synchronized (object1) {
        System.out.println(Thread.currentThread().getName() + "  1");
        synchronized (object2) {
            System.out.println(Thread.currentThread().getName() + "  2");
        }}

}else {
    synchronized (object1) {
        System.out.println(Thread.currentThread().getName() + "  3");
        synchronized (object2) {
            System.out.println(Thread.currentThread().getName() + "  4");
        }
    }
}
/*两个线程都先获取object1，再获取object2，而不是一个先object1再object2，另一个先object2再object1*/
```

#### 释放锁

1. 同步方法/代码块执行结束
2. 当前线程在同步方法/代码块遇到break、return
3. 在同步方法/代码块出现未处理的error或exception
4. 在同步方法/代码块执行wait()方法

## IO流

文件在程序中是以流的形式来操作的

流：数据在数据源（文件）和程序（内存）之间经历的路径

#### 构造器方法

new File(String pathname)//根据路径构建一个File对象
new File(File parent,String child)//根据父目录文件+子路径
new File(String parent,String child)//根据父目录+子路径

```java
String fileName = "d:/text.txt";//String fileName = "d:\\text.txt";
File file = new File(fileName);
try {
    file.createNewFile();
} catch (IOException e) {
    e.printStackTrace();
}
```

#### 方法

getAbsoluteFile()//得到绝对路径
getParent()//得到父级目录(上一级)
length()//得到文件大小(字节)
exists()//文件是否存在
isDirectory()//是否是一个目录
mkdir()//创建一级目录
mkdirs()//创建多级目录
delete()//删除空目录及文件
createNewFile()//该方法的作用是创建指定的文件。该方法只能用于创建文件,不能用于创建文件夹
list()//String[]数组  获取一个目录中的所有文件或者文件夹的名称

```java
File file = new File("d:\\Game");
String[] arg = file.list();
for (String name :arg) {
    System.out.println(name);
}
/*Cheat Engine 7.2
DEMON.GAZE.EXTRA.rar
fate stay night
fault milestone one.rar
FLOWERS CH
HikariFieldGames
......*/
```

listFiles()//File[]数组  获取目录下当前文件以及文件对象

```java
File[] files = file.listFiles();
for (File file1 :files) {
    System.out.println(file1);
}
/*
d:\Game\Cheat Engine 7.2
d:\Game\DEMON.GAZE.EXTRA.rar
d:\Game\fate stay night
d:\Game\fault milestone one.rar
d:\Game\FLOWERS CH
d:\Game\HikariFieldGames
d:\Game\Library Of Ruina(废墟图书馆)
......
*/
```

#### 流的分类

操作数据的单位不同：字节流、字符流
数据流的流向不同：输入流、输出流
流的角色不同：节点流、处理流/包装流

#### 常用子类

FileInputStream:文件输入流
BufferedInputStream:缓冲字节输入流
ObjectInputStream:对象字节输入流

##### FileInputStream

```java
 File file = new File("d:\\read.txt");
 FileInputStream fileInputStream = null;
 byte[] buf = new byte[8];
 int len = 0;
 try {
     fileInputStream = new FileInputStream(file);
     while ((len = fileInputStream.read(buf)) != -1) {
         System.out.print(new String(buf,0,len));
     }
 } catch (IOException e) {
     e.printStackTrace();
 }finally {
     try {//关闭流
         fileInputStream.close();
     } catch (IOException e) {
         e.printStackTrace();
     }
 }
```

##### FileOutputStream

```java
File file = new File("d:\\read.txt");
FileOutputStream fileOutputStream = null;
try {//new FileOutputStream(file)创建方式write会覆盖
    //new FileOutputStream(file，true)创建方式write内容会追加
    fileOutputStream = new FileOutputStream(file);
    //write(byte[] b,int off,int length)从索引off开始，write length个字节
    fileOutputStream.write("Hello,world".getBytes());
}catch (IOException e){
    e.printStackTrace();
}finally {
    try {if(fileOutputStream!=null)
        fileOutputStream.close();
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

#### FileReader和FileWriter

用法类似FileInputStream和FileOutputStream

FileWriter使用后，要关闭(close)或者刷新(flush)，否则写入不到指定的文件

#### 节点流、处理流

节点流：从一个特定的数据源读写数据（如FileReader、FileWriter）

处理流：是“连接”在已存在的流(节点流或处理流)之上的，为程序提供更强大的读写功能，也更加灵活（如BufferedReader、BufferedWriter），使用修饰器设计模式，不会直接与数据源相连

##### BufferedReader和BufferedWriter

关闭处理流时，只需关闭外层流即可

不能操作二进制文件（声音、视频、doc、pdf等等），可能造成文件损坏

```java
String filePath = "d:\\test.txt";
BufferedReader bufferedReader = new BufferedReader(new FileReader(filePath));
BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter("d:\\test2.txt"));
String str ;
while ((str=bufferedReader.readLine())!=null)
{
    bufferedWriter.write(str);
    bufferedWriter.newLine();
}
if(bufferedReader!=null){bufferedReader.close();}
if(bufferedWriter!=null){bufferedWriter.close();}
```

##### BufferedInputStream和BufferedOutputStream

##### ObjectInputStream和ObjectOutputStream

序列化：在保存数据时，保存数据的值及数据类型
反序列化：在恢复数据时，恢复数据的值及数据类型

支持序列化机制：实现Serializable（这是一个标记接口//没有方法）接口或Externalizable接口
序列化后，保存的文件格式不是纯文本，是按它的格式来保存，后缀不重要
读取（反序列化）的顺序需要和保存到数据（序列化）的顺序一致
序列化的类中建议添加private static final long serialVersionUID = 1L;//serialVersionUID 序列化的版本号，提高兼容性
序列化对象时，默认将所有属性进行序列化，除了static和transient修饰的成员
序列化对象时，要求里面属性的类型也需要实现序列化接口
序列化具备可继承性

```java
String str = "d:\\text.dat";
ObjectOutputStream objectOutputStream = new ObjectOutputStream(new FileOutputStream(str));
objectOutputStream.writeInt(100);
objectOutputStream.writeBoolean(true);
objectOutputStream.writeDouble(22.33);
objectOutputStream.writeUTF("Hello");
if (objectOutputStream!=null) {
    objectOutputStream.close();
}
```

```java
ObjectInputStream objectInputStream = new ObjectInputStream(new FileInputStream(str));
System.out.println(objectInputStream.readInt());
System.out.println(objectInputStream.readBoolean());
System.out.println(objectInputStream.readDouble());
System.out.println(objectInputStream.readUTF());
if (objectOutputStream!=null) {
    objectInputStream.close();
}
```

#### 标准输入流/输出流

标准输入流：System.in  编译--运行类型==>  InputStream--BufferedInputStream

标准输出流：System.out  编译--运行类型==>  PrintStream--PrintStream

#### 转换流

InputStreamReader：将字节流包装成字符流

OutputStreamWriter

处理乱码

```java
String str = "d:\\test.txt";
BufferedReader br = new BufferedReader(new InputStreamReader
        (new FileInputStream(str),"gbk"));
		System.out.println(br.readLine());
		br.close();
```

```java
OutputStreamWriter osw = new OutputStreamWriter(new FileOutputStream(str), "gbk");
osw.write("Hello,你好");
osw.close();
```

#### 打印流

PrintStream和PrintWriter

只有输出流，没有输入流

#### Properties

用于读写配置文件的集合类

父类HashTable<Object,Object>

##### 方法

load:加载文件的键值对到Properties对象
list:将数据显示到指定设备
getProperty(key):根据键获取值
setPeoperty(key,value):是指键值对到Properties对象
store:将Properties对象中的键值对存储到配置文件。idea中，保存信息到配置文件，若含有中文，会存储为unicode码

## 网络编程

网络通信：将数据通过网络从一台设备传输到另一台设备

#### ip地址

概念：用于唯一表示网络中的每台计算机/主机
ip地址组成：网络地址+主机地址

cmd---->ipconfig

#### InetAddress

getLocalHost:获取本机InetAddress对象

```java
InetAddress localHost = InetAddress.getLocalHost();
//LAPTOP-T2HL8CF5/192.168.52.1
```

getByName:根据指定主机名获取InetAddress对象

```java
InetAddress name = InetAddress.getByName("LAPTOP-T2HL8CF5");
//LAPTOP-T2HL8CF5/192.168.52.1
```

根据域名返回InetAddress对象

```java
InetAddress host = InetAddress.getByName("www.baidu.com");
System.out.println(host);
//www.baidu.com/180.101.49.12
```

getHostName:通过InetAddress对象，获取对应的主机名/域名

getHostAddress:通过InetAddress对象，获取对应的地址

#### Socket

通信两端都要有socket(套接字)，是两台机器间通信的端点，网络通信就是socket通信
socket允许程序把网络当成一个流，数据在两个socket间通过IO传输

##### TCP编程

底层使用TCP/IP协议

客户端连接到服务端后，TCP/IP随机分配一个端口号给客户端

Server端

```java
		//指定端口，等待连接
        ServerSocket serverSocket = new ServerSocket(2048);
        System.out.println("等待客户端的连接请求...");
        //若没有客户端连接2048端口，程序会阻塞，等待连接，若有客户端连接，返回socket对象
        Socket socket = serverSocket.accept();
        InputStream inputStream = socket.getInputStream();
        byte[] buf = new byte[1024];
        int len;
        while ((len = inputStream.read(buf))!=-1){
            System.out.println(new String(buf,0,len));
        }
        OutputStream outputStream = socket.getOutputStream();
        outputStream.write("hello client".getBytes());
        socket.shutdownOutput();//提示输入完毕，不然可能会一直等待
		//关闭流对象和socket
        outputStream.close();
        inputStream.close();
        socket.close();
        serverSocket.close();
```

Client端

```java
		//连接本机2048端口
        Socket socket = new Socket(InetAddress.getLocalHost(),2048);
        //得到可socket对象关联的输出流
        OutputStream outputStream = socket.getOutputStream();
        //写入数据到数据通道
        outputStream.write("hello server".getBytes());
        socket.shutdownOutput();//提示输入完毕，不然可能会一直等待
        InputStream inputStream = socket.getInputStream();
        byte[] buf = new byte[1024];
        int len;
        while ((len = inputStream.read(buf))!=-1){
            System.out.println(new String(buf,0,len));
        }
        //关闭流对象和socket
        inputStream.close();
        outputStream.close();
        socket.close();
```

###### 使用字符流

Server端

```java
ServerSocket serverSocket = new ServerSocket(2048);
Socket socket = serverSocket.accept();

BufferedReader br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
System.out.println(br.readLine());

BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
bw.write("hello client");
bw.flush();//使用字符流要手动刷新,否则数据不会写入数据通道
bw.newLine();//插入换行符，表示写入内容结束,读取必须用readLine()
bw.close();
br.close();
socket.close();
serverSocket.close();
```

Client端

```java
Socket socket = new Socket(InetAddress.getLocalHost(),2048);
BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
bw.write("hello server");
bw.flush();//要手动刷新,否则数据不会写入数据通道
bw.newLine();//插入换行符，表示写入内容结束,读取必须用readLine()
//上面两行亦可更改为bw.flush();socket.shutdownOutput();
BufferedReader br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
System.out.println(br.readLine());
bw.close();
br.close();
socket.close();
```

为什么写入数据后要调用flush()方法：以流的形式写入数据的时候，并不是一写入就立刻发送到网络，而是先写入内存缓冲区，直到缓冲区满了以后，才会一次性真正发送到网络，这样设计的目的是为了提高传输效率。如果缓冲区的数据很少，而我们又想强制把这些数据发送到网络，就必须调用flush()强制把缓冲区数据发送出去-

###### Client传输图片，Server发送消息

Server

```java
ServerSocket serverSocket = new ServerSocket(2048);
Socket socket = serverSocket.accept();

BufferedInputStream bis = new BufferedInputStream(socket.getInputStream());
int len;
byte[] buf = new byte[1024];
BufferedOutputStream bos1 = new BufferedOutputStream(new FileOutputStream("src\\a.jpg"));
while ((len = bis.read(buf))!=-1){
    bos1.write(buf,0,len);
}
bos1.flush();
//这里不用socket.shutdownOutput(),因为下面还要发送数据
BufferedOutputStream bos = new BufferedOutputStream(socket.getOutputStream());
bos.write("收到图片".getBytes());
bos.flush();
socket.shutdownOutput();

bis.close();
bos.close();
socket.close();
serverSocket.close();
```

Client

```java
Socket socket = new Socket(InetAddress.getLocalHost(), 2048);

BufferedInputStream bis1 = new BufferedInputStream(new FileInputStream("d:\\a.jpg"));
BufferedOutputStream bos = new BufferedOutputStream(socket.getOutputStream());
int len1;
byte[] buf1 = new byte[1024];
while ((len1 = bis1.read(buf1))!=-1){
    bos.write(buf1,0,len1);
}
bos.flush();
socket.shutdownOutput();

BufferedInputStream bis = new BufferedInputStream(socket.getInputStream());
int len;
byte[] buf = new byte[1024];
StringBuilder stringBuilder = new StringBuilder();
while ((len = bis.read(buf))!=-1){
    stringBuilder.append(new String(buf,0,len));
}
System.out.println(stringBuilder);

bis.close();
bos.close();
socket.close();
```

##### netstat -an指令

可以查看当前主机网络情况，包括端口监听情况和网络连接情况
netstat -an|more 可以分页显示
在dos控制台下执行//空格--下一页

##### UDP编程(了解)

DatagramSocket和DatagramPacket(数据包)实现类基于UDP协议网络程序
UDP数据报通过数据报套接字DatagramSocket发送和接收，系统不保证UDP数据报一定能安全到达目的地，也不确定什么时候能到达
DatagramPacket对象封装了UDP数据报，在数据报中包含了发送端及接收端的IP地址和端口号
UDP协议中每个数据报都给出了完整的地址信息，因此无序建立发送方和接收方的连接
数据报的大小限制在64k内，不适合传输大量数据

```java
		//DatagramSocket 既能接收数据，也能发送数据
        //收数据
        DatagramSocket datagramSocket = new DatagramSocket(2048);
        //准备DatagramPacket对象接收数据
        byte[] buf = new byte[1024];
        DatagramPacket datagramPacket = new DatagramPacket(buf, buf.length);
        //receive方法将DatagramPacket对象填充进DatagramSocket对象
        //如果没有数据发送到2048端口，就会阻塞等待
        datagramSocket.receive(datagramPacket);
        //拿到数据后，进行拆包，取出数据
        int len = datagramPacket.getLength();
        byte[] data = datagramPacket.getData();
        String str = new String(data,0,len);
        System.out.println(str);

        //发数据
        byte[] bytes = "Hello B".getBytes();
        DatagramPacket sendPacket = new DatagramPacket
        (bytes,bytes.length,InetAddress.getByName("114.213.68.189"),2049);
/*datagramPacket = new DatagramPacket(bytes,bytes.length,InetAddress.getByName("114.213.68.189"),2049);
datagramSocket.send(datagramPacket);
*/
        datagramSocket.send(sendPacket);
        //关闭
        datagramSocket.close();








		DatagramSocket datagramSocket = new DatagramSocket(2049);
        //装数据
        byte[] bytes = "Hello A".getBytes();
        DatagramPacket datagramPacket = new DatagramPacket
        (bytes,bytes.length,InetAddress.getByName("114.213.68.189"),2048);
        datagramSocket.send(datagramPacket);

        //接收数据
        byte[] buf = new byte[1024];
        DatagramPacket receverPacket = new DatagramPacket(buf, buf.length);
        datagramSocket.receive(receverPacket);
        //拆数据
        int len = receverPacket.getLength();
        byte[] bytes2 = receverPacket.getData();
        String str = new String(bytes2,0,len);
        System.out.println(str);
        //关闭
        datagramSocket.close();


```

## 反射

ocp原则:开闭原则，在不修改源码的情况下扩展功能

反射就是Reflection，Java的反射是指程序在运行期可以拿到一个对象的所有信息。通过Class实例获取class信息的方法称为反射

类加载完后，会在堆中产生一个Class类型的对象(一个类只有一个Class对象)，这个对象包含了类的完整信息结构。通过这个对象得到类的结构。这个Class对象就像一面镜子，透过这个镜子看到类的结构

### 获取Class实例的方法

方法一：直接通过一个class的静态变量class获取，多用于参数传递：

```java
Class cls = String.class;
```

方法二：如果我们有一个实例变量，可以通过该实例变量提供的getClass()方法获取：

```java
String s = "Hello";
Class cls = s.getClass();
```

方法三：如果知道一个class的完整类名，可以通过静态方法Class.forName()获取：

```java
Class cls = Class.forName("java.lang.String");
```

基本数据类型

```java
Class cls = int.class;
```

基本数据类型对应的包装类

```java
Class<Integer> type = Integer.TYPE;
```

Class实例在JVM中是唯一的，所以，上述方法获取的Class实例是同一个实例

##### 注意一下Class实例比较和instanceof的差别

```java
Integer n = new Integer(123);

boolean b1 = n instanceof Integer; // true，因为n是Integer类型
boolean b2 = n instanceof Number; // true，因为n是Number类型的子类

boolean b3 = n.getClass() == Integer.class; // true，因为n.getClass()返回Integer.class
boolean b4 = n.getClass() == Number.class; // false,因为Integer.class!=Number.class
```

### 使用

```java
Properties properties = new Properties();
properties.load(new FileInputStream("src\\a.properties"));
String classPath = properties.getProperty("classPath").toString();
String method = properties.getProperty("method").toString();

Class cls = Class.forName(classPath);
Object o = cls.newInstance();

Method method1 = cls.getMethod(method);
method1.invoke(o);//Hello

Field name = cls.getField("name");
System.out.println(name.get(o));//null



A.java
public class A {
    public String name;

    public A(String name) {
        this.name = name;
    }

    public A() {
    }

    public void hi() {
        System.out.println("Hello");
    }
}



a.properties
classPath=temporary.A
name=Tom
method=hi
```

优点：可以动态的创建和使用对象（也是框架底层核心），使用灵活
缺点：反射基本时解释执行，对执行速度有影响

##### 反射调用优化--关闭访问检查

Method、Field、Constructor对象都有setAccessible()方法，setAccessible的作用是启动和禁止访问安全检查的开关。参数为true，反射的对象在使用时取消访问检查，提高速度

##### 细节

Class对象不是new出来的，而是系统创建的

类的字节码二进制数据（元数据）放在方法区

有Declared的方法能拿到所有属性（getConstructor----getDeclaredConstructor）

### 类加载

静态加载：编译时加载相关的类，如果没有就报错，依赖性太强

动态加载：运行时加载需要的类，如果运行时没用到该类，就不报错

##### 加载：将类的class文件读入内存，并创建一个java.lang.Class对象。此过程由类加载器完成

##### 连接

验证：对文件的安全进行校验

准备：对静态变量进行默认初始化并分配空间

```java
public int n1 = 10;//n1是实例属性，不会分配内存
public static int n2 = 20;//n2是静态变量，默认初始化为0
public static final int n3 = 30;//n3是常量，n3 = 30
```

解析：把常量池的符号引用转为直接引用

将类的二进制数据合并到jre中

##### 初始化：对类进行初始化，主要指静态成员 

执行<clinit>()方法，按顺序依次收集类中的所有静态变量的赋值动作和静态代码块中的语句，并合并。次方法会在多线程环境中被正确的枷锁、同步

### 方法

#### Field类

getModifiers:以int形式返回修饰符  public--1,private--2,protected--4,static--8,final--16,默认--0(public static=1+8=9)

getType:返回属性对应的类的Class对象

### 通过反射创建对象

newInstance()
getConstructor(Class...class)
getDeclaredConstructor(Class...class)

```java
Class cls = Class.forName("temporary.A");
Constructor constructor = cls.getDeclaredConstructor(String.class);
constructor.setAccessible(true);//爆破  构造器私有时使用
constructor.newInstance("tom");//构造器传参
```

Field f = clazz对象.getDeclaredField(属性名);
f.setAccessible(true);
f.set(o,值);//o:对象
f.get(o);
如果是静态属性，o可写成null

方法：
Method method = cls.getDeclaredMethod(hi,String.class);
method.invoke(o,"你好"/*实参列表*/);

在反射中，如果方法有返回值，统一返回Object类型

# Lambda 表达式

应用：接口中只能有一个抽象方法==>函数式接口

->:lambda操作符
->左边:lambda形参列表，即接口中的抽象方法的形参列表
->右边:lambda体，即重写的抽象方法的方法体

格式一：无参无返回值

() -> {}

格式二：lambda有一个参数，无返回值

(参数类型 参数名) -> {};

格式三：参数类型可省略,由编译器推段

(参数名) -> {}//Consumer<String> con = (str) -> {System.out.printLn(str)};

格式四：两个及以上参数，且有返回值

```java
Comparator<Integer> com = (o1,o2) -> {
System.out.println(o1);
System.out.println(o2);
return 01.compareTo(o2);
};
```

#### 函数式接口

Consumer<T>: void accept(T t)
Supplier<T>:T get()
Function<T,R>:R apply(T t)
Predicate<T>:boolean test(T t)

#### 方法引用
当要传递给lambda体的操作已经有实现的方法，可以用方法引用，

情况一、二：接口中的抽象方法的形参列表和返回值类型与方法引用的方法一致

使用格式：类(或对象)::实例方法

```java
//情况一：对象::实例方法
Consumer<String> con = str -> System.out.println(str);
con.accept("Hello");
//void accept(T t)
//void printLn(T t)类似
PrintStream p = System.out;
Consumer<String> con2 = p::println;
con2.accept("Hello");
//------------------------------------------
Employee emp = new Employee("Tom");
Supplier<String> sup = () -> emp.getName();
System.out.println(sup.get());
//Supplier   T get()
//类Employee String getName()
Supplier<String> sup = emp::getName();
sup.get();

//情况二：类::静态方法
Comparator<Integer> com = (t1,t2) -> Integer.compare(t1,t2);
System.out.println(com.compare(11,22));
//Comparator  int compare(T t1,T t2)
//Integer     int compare(T t1,T t2)
Comparator<Integer> com = Integer::compare;

//情况三：类::实例方法
Comparator<Integer> com = (t1,t2) -> t1.compareTo(t2);
//Comparator中的int  int compare(T t1,T t2)
//String中的int      t1.compareTo(t2)
Comparator<Integer> com = (t1,t2) -> String::compareTo;
//------------------------------------------
Employee emp = new Employee("Tom");
Function<Employee,String> f = e -> e.getName();
System.out.println(f.apply(emp));
//Function<T,R>   R apply(T t)
//Employee        String getName()
Function<Employee,String> f = Employee::getName;
```

# Stream API

把函数时编码风格引入java。使用Stream API能对几何数据进行操作。Stream API提供了一种高效且易于使用的处理数据的方式

Stream自己不会存储元素
Stream不会改变原对象，会返回一个新Stream
Stream操作是延迟执行的
Stream执行流程：Stream实例化-----一系列中间操作-----终止操作，产生结果，之后不会再被用

#### Stream实例化

##### 通过集合

```java
List<Employee> employees = new ArrayList<>();
//default Strean<E> stream():返回一个顺序流
Stream<Employee> stream = employees.stream();
//default Strean<E> parallelStream():返回一个并行流
Stream<Employee> parallelStream = employees.parallelStream();
```

##### 通过数组

```java
//static<T> Stream<T> stream(T[] array)：返回一个流
int[] array = {1,2,3,4};
IntStream stream = Arrays.stream(array);
//自定义数组类型：Stream<Employee> stream = Arrays.stream(employee);
```

##### 通过Stream的of()方法

```java
Stream<Integer> stream = Stream.of(1,2,3,4,5);
```

#### 中间操作

##### 筛选与切片

filter(Predicate p):接收lambda，从流中排除某些元素

```java
List<Employee> employees = new ArrayList<>();
Stream<Employee> stream = employees.stream();
stream.filter(emp -> emp.getSalary()>1000).forEach(System.out::println);
```

limit(n):使其元素不超过指定数量   employees.stream().limit(3).forEach(System.out::println);

skip(n):跳过元素，返回一个扔掉前n个元素的流,若元素不足n，返回一个空流，与limit互补employees.stream().skip(3).forEach(System.out::println);

distinct():筛选，根据流所生成元素的hashCode()和equals()去重

##### 映射

map(Function f)接受一个函数作为参数，将元素转化成其他形式或提取信息，该函数会被应用到每个元素上，并将其映射成一个新元素

```java
List<String> list = Arrays.asList("aa","bb","cc","d");
list.stream().map(str -> str.toUpCase()).forEach(System.out::println);
```

flatMap(Function f)接受一个函数作为参数，将流中的每个值换成另一个流，然后把所有流连接成一个流

```java
Stream<Stream<Character>> streamStream = list.stream().map(Test::forStreamToStream);
streamStream.forEach(s -> {
s.forEach(System.out::println);
});//a、a、b、b、c、c、d、d

Stream<Charactor> charactorStream = list.stream().flatMap(Test::forStreamToStream);
charactorStream.forEach(System.out::println);//a、a、b、b、c、c、d、d


//将字符串中的多个字符构成的集合转化为对应的Stream实例
Class Test{
    public static Stream<Charactor> forStreamToStream(String str){//aaa->a、a、a
        ArrayList<Charactor> list = new ArrayList<>();
        for(Charactor c :: str.toCharArray()){
            list.add(c);
        }
        return list.stream();
    }
}
```

map和flatMap，类比list.add()和list.addAll()

##### 排序

sorted():产生一个新流，其中按自然顺序排序

比较对象需要实现Comparable接口

```java
List<Integer> list = Arrays.asList(24,65,2,5,6,7,865);
list.stream().sorted().forEach(System.out::println);
```

sorted(Comparator com):产生一个新流，其中按比较器顺序排序

```java
List<Employee> employees = new ArrayList<>();
employees.stream().sorted((e1,e2) -> Integer.compare(e1.getAge(),e2.getAge())).forEach(System.out::println);
```

#### 终止操作

##### 匹配与查找

allMatch(Predicate p) 检查是否匹配所有元素
anyMatch(Predicate p)
noneMatch(Predicate p) 检查是否没有匹配的元素
findFrist;返回第一个元素
findAny
cout
max(Comparator com):返回流中最大值
min(Comparator com)
forEach(Consumer c):内部迭代
collect:把当前流转化为一个集合

##### 归约

reduce(T iden,BinaryOperator b) 可以将流中元素反复结合起来，得到一个值，返回T

```java
//计算1-10和
List<Integer> list = Arrays.asList(1,2,3,4,5,6,7,8,9,10);
list.stream().reduce(0,Integer::sum);
```

reduce(BinaryOperator b) 可以将流中元素反复结合起来，得到一个值，返回Option<T>

##### 收集

collect(Collector c):将流转化为其他形式

```java
List<Employee> employees = new ArrayList<>();
List<Employee> empList = employees.stream().filter(emp -> emp.getSalary()>1000).collect(Collectors.toList());//转为List
```

#### Optional<T>类

保存类型T的值代表这个值存在，保存null表示这个值不存在

Optional.of(T t):创建一个Optional实例，t必须非空
Optional.empty():创建一个空的Optional实例
Optional.ofNullable(T t):t可以为null

# 数据库

普通的表的本质是文件

DDL:数据定义语言(create表、数据库)
DML:数据操作语言(insert,update,delete)
DQL:数据查询语言(select)
DCL:数据控制语言(一般用于管理数据库的用户权限)

character set:指定数据库采用的字符集，如不指定，默认utf8
collate：指定数据库字符集的校对规则（默认utf8_general_ci//不区分大小写   utf8_bin//区分大小写）
engine:存储引擎

### 语句

#### 数据类型

##### 数值类型

tinyint:占1个字节
smallint:占2个字节
mediumint:占3个字节
int:占4个字节
bigint:占8个字节
float:占4个字节
double:占8个字节

//默认有符号，无符号unsigned-->id int unsigned

decimal[M,D]:定点数，M指定总位数 max==65 默认10，D指定小数点位数  max==30 默认0
bit(M):位类型，M指定位数，1-64，默认1(8==1字节)，按位显示即二进制显示

##### 文本类型

char(size):0-255字符
varchar(size):size0-65535字节，其中1-3个字节用来记录大小
text:0-65535
longtext:0-2^32-1

##### 二进制类型

blob:0-65535
longblob:0-2^32-1

##### 日期类型

date:日期  年、月、日
time:时间 时、分、秒
datetime:日期时间  YYYY-MM-DD HH:mm:ss
timestamp:时间戳(login_time TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP 更新和插入时自动更新当前时间)


#### 创建

创建数据库、表的时候，可以用反引号``规避关键字

SHOW DATABASES//查看当前数据库服务器中的所有数据库

SHOW CREATE DATABAS 数据库名//查看数据库的定义信息

DROP DATABASE 数据库名

##### 表

添加列：ALTER TABLE 表名 ADD column名 属性名 ......
修改列：ALTER TABLE 表名 MODIFY(column名 属性名 ......)
删除列：ALTER TABLE 表名 DROP column名  ......
修改表名：RENAME TABLE 表名 to 新表名
修改字符集:ALTER TABLE 表名 charset/(character set) 字符集
修改列名：ALTER TABLE 表名 CHANGE  old_field_name  new_field_name field_type
desc 表名：查看表的列
drop TABLE 表名

##### CRUD
insert into 表名 (...) values (...),(...)...
delete from 表名 where  ......
select [distinct去重] *|column1 [[as]别名] ,column2 .... from 表名 [[as]别名] where  ......
order by column  asc升序(默认)  desc降序
count:返回行的总数 count(*) 返回所有满足条件的行数   count(column) 排除null
sum(column) 返回满足条件的行的数值的和
group by column having ...(select * from table_name group by column having ...)

###### 函数

is (NOT) NULL:判断是否为null
concat 拼接
ucase(column)转大写
lcase(column)转小写
substring(str,position,length) 截取
left(column,length) 从左边提取length个字符
length():长度
format(number,位数) 保留小数位数
CURRENT_TIMESTAMP()/NOW():当前时间戳/当前时间
DATE_ADD(date,INTERVAL d_value d_type):在date中加上日期或事件
//where DATE_ADD(send_time,INTERVAL 10 minute) >= NOW() 查询10分钟内发布的信息的筛选条件
DATE_SUB(date,INTERVAL d_value d_type):在date中减去日期或事件
//where DATE_SUB(NOW(),INTERVAL 10 minute) <= send_time
DATEDIFF(date1,date2):两个日期差(天)  date1-date2
unix_timestamp():返回1970-1-1到现在的秒数
FROM_UNIXTIME():把一个unix_timestamp秒数转成指定格式的日期
//select FROM_UNIXTIME(1819483100,'%Y-%m-%d %H:%i:%s') from dual

###### 加密函数、系统函数

USER():查询用户  --用户@IP地址
DATABASE():查询当前使用数据库名称
MD5(str):为字符串算出一个MD5 32的字符串
SHA1(str):加密函数

###### 流程控制函数
if(expr1,expr2,expr3):expr1为true==>返回expr2,否则返回expr3
IFNULL(expr1,expr2):若expr1非null，返回expr1，否则返回expr2
CASE WHEN expr1 THEN expr2 WHEN expr3 THEN expr4 ELSE expr5 END:expr1为true==>返回expr2,否则,若expr3为true==>返回expr4,否则返回expr5

###### 分页查询
select ... limit start,rows:从start+1行开始取(start从0开始)，取出rows行

###### 其余查询

select * from student where (id,name) = (select id,name from...//子查询)
表复制：insert into 表1 [字段] select 字段/* from 表2-----将表2查询到的结果插入到表1
create 表1 like 表2----将表2的结构复制到表1
any
all
union all:取得两个结果集的并集，不会去重  select ...  union all select ...
union:去重
左外连接：表1 left join 表2 on 条件
右外连接：表1 right join 表2 on 条件
复合主键:PRIMARY KEY(column1,column2 ...)
unique:列不能重复  null除外
外键:FOREIGE KEY(本表字段) REFERENCES 主表名(主键或unique字段)
check:强制行数据满足某种条件
自增长:auto_increment//ALTER TABLE 表名 auto_increment=开始增长的值

##### 索引
CERATE [UNIQUE] INDEX 索引名 ON 表(字段)
ALTER TABLE 表名 ADD INDEX 索引名 (字段)
DROP INDEX 索引名 ON 表名
ALTER TABLE 表名 DROP PRIMARY KEY
查询索引:SHOW INDEX FROM 表名

##### 事务
保证数据的一致性，由一组相关的dml语句组成
start transaction:开启事务
savepoint 保存点名字:设置保存点
rolback to 保存点名字:回退事务
roolback:回退到事务开始
commit:提交事务，无法回滚

###### 事务隔离级别
脏读:一个事务读取另一个事务尚未提交的修改时，产生脏读//事务未提交
不可重复读:同一查询在统一事务中进行多次，由于其他事务所做的删除、修改操作，每次返回不同的结果集
幻读:同一事务中，多次对整表进行查询统计，每次返回不同的结果集
查看事务隔离级别：select @@transaction_isolation
设置事务隔离级别:set transaction isolation level 级别
隔离级别
读未提交(Read uncommited):出现情况--->脏读-不可重复读-幻读-不加锁
读已提交(Read commited):不可重复读-幻读-不加锁
可重复读(Repeatable read):不加锁
可串行化(Serializable):加锁
mysql默认可重复读

##### 存储引擎
MYISAM:不支持事务、外键，访问速度快，支持表级锁
InnoDB:支持事务
MEMORY:存储在内存中，关闭mysql，数据会丢失，但表结构还在

##### 视图
视图是一个虚拟表，其内容由查询定义，数据来自对应的真实表(基表)
创建视图:create view 视图名 as select 语句
alter view 视图名 as select 语句
show create view 视图名
drop view 视图名

##### 用户管理
create user '用户名' @ '允许登录的位置' identified by '密码'
drop user '用户名' @ '允许登录的位置'
set password = password('密码')//改自己密码
set password for  '用户名' @ '登录的位置' = password('密码')//改别人密码
mysqladmin -u用户名 -p旧密码 password 新密码//-u用户名、-p旧密码各自是一个整体，不要有空格

##### 权限
grant 权限列表 on 库.对象名(*.* 所有对象) to '用户名' @ '登录的位置' [identified by '密码'] (写了 若用户存在，就是修改密码，若不存在，就是创建用户)
revoke 权限列表 on 库.对象名(*.* 所有对象) from '用户名' @ '登录的位置'
刷新权限:flush privileges


### 备份、恢复数据库（DOS执行）

备份:mysqldump -u 用户名 -p -B 数据库1 数据库2 数据库n > 文件名.sql(存储路径 例d:\\test.sql)
         mysqldump -u 用户名 -p 密码 数据库 表1 表2 表n> d:\\文件名.sql
恢复:source 文件名.sql(进入mysql命令行执行 即cmd--> mysql -u root -p)


# JDBC

为访问不同的数据库提供统一接口

```java
//注册驱动--加载Driver类
CLass.forName("com.mysql.cj.jdbc.Driver");
Strng url = "jdbc:mysql://localhost:3306/数据库名?serverTimezone=Asia/Shanghai&characterEncoding=UTF-8";
String user = "root";
String password = "123456";
Connection connection = DriverManager.getConnection(url,user,password);
```

```java
Properties properties = new Properties();
properties.load(new FileInputStream("src\\mysql.properties")); 
Strng url = properties.getProperty("url");
String user = properties.getProperty("user");
String password = properties.getProperty("password");
CLass.forName(properties.getProperty("driver"));
Connection connection = DriverManager.getConnection(url,user,password);
//sql
String sql = "常规sql语句";
//执行静态sql语句，并返回生成的结果对象
Statement statement = connection.createStatement();
int rows = statement.executeUpdate(sql);//若是dml语言，返回受影响的行数
//查询select  statement.executeQuery(sql)
statement.close();
connection.close();
```

#### ResultSet

表示数据库结果集的数据表，通常通过执行查询数据库的语句生成

```java
ResultSet resultSet = statement.executeQuery(sql);
while(resultSet.next()){
    resultSet.getInt(1);//获取该行的第1列数据  resultSet.getInt("列名");
    resultSet.getString(2);//获取该行的第2列数据
}
resultSet.close();
```

previous():向上移动一行

#### Statement

Statement:存在sql注入(sql注入是利用某些系统没有对用户输入的数据进行充分的检查，而在用户输入数据中注入非法的sql语句段或命令，恶意攻击数据库)

PreparedStatement:预处理

```java
Properties properties = new Properties();
properties.load(new FileInputStream("src\\mysql.properties")); 
Strng url = properties.getProperty("url");
String user = properties.getProperty("user");
String password = properties.getProperty("password");
String driver = properties.getProperty("driver");
CLass.forName(driver);
Connection connection = DriverManager.getConnection(url,user,password);
String sql = "select id from student where id = ? and grade = ?";
PreparedStatement preparedStatement = connection.prepareStatement(sql);
//第一个参数设置sql语句中参数的索引,第二个参数设置值
preparedStatement.setString(1,st_id);
preparedStatement.setString(2,st_grade);
ResultSet resultSet = preparedStatement.executeQuery();
while(resultSet.next()){
    resultSet.getInt(1);//获取该行的第1列数据
    resultSet.getString(2);//获取该行的第2列数据
}
resultSet.close();
preparedStatement.close();
connection.close();



user=root
password=123456
driver=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/test
```

CallableStatement:存储过程

#### 事务

JDBC程序中，当一个Connection对象创建时，默认自动提交事务

setAutoCommit(false):取消自动提交事务//Connection方法--setAutoCommit()、commit()、rollback()

#### JDBC批处理

addBatch():添加需要批量处理的SQL语句或参数
executeBatch():执行
clearBatch():清空
若要使用批处理，在url中添加?rewriteBatchedStatements=true
批处理往往和PreparedStatement一起使用，既减少编译次数，又减少运行次数

#### 数据库连接池

预先在缓冲池中放入一定数量的连接，当需要建立数据库连接时，只需从缓冲池中取出一个连接，使用完毕后放回缓冲池，当应用程序向连接池请求的连接数超过最大连接数时，这些请求将被加入到等待队列中

##### C3P0

```java
//创建数据源对象
ComboPooledDataSource comboPooledDataSource = new ComboPooledDataSource();
//读取mysql.properties相关信息
.......//省略
//给数据源设置相关参数
comboPooledDataSource.setDriverClass(driver);
comboPooledDataSource.setJDBCUrl(url);
comboPooledDataSource.setUser(user);
comboPooledDataSource.setPassword(password);
//设置初始化连接数
comboPooledDataSource.setInitialPoolSize(数量);
//最大连接数
comboPooledDataSource.setMaxPoolSize(数量);
Connection connection = comboPooledDataSource.getConnection();
connection.close();
```

##### Druid(德鲁伊)

```java
Properties properties = new Properties();
properties.load(new FileInputStream("src\\druid.properties"));
DataSource dataSource = DruidDataSourceFactory.createDataSource(properties);
Connection connection = dataSource.getConnection();
connection.close();
```

#### Apatch-DBUtils

QueryRunner类:封装了sql的执行，是线程安全的，自动关闭连接

ResultSetHandler接口:将数据按要求转化为另一种数据    

```java
//Druid拿到连接connection
//QueryRunner
QueryRunner queryRunner = new QueryRunner();
String sql = "select * from student where id >= ?"; 
//执行相关方法，返回ArrayList结果集
/*new BeanListHandler<>(Student.class)：将resultSet转化为Student类对象，封装到ArrayList集合中  底层用反射机制获取Student类属性*/
List<Student> list = queryRunner.query(connection,sql,new BeanListHandler<>(Student.class),1);//查询id>=1
//返回单行单列 Object o = queryRunner.query(connection,sql,new ScalarHandler(),1);



执行dml
String sql = "update student set name = ? where id = ?"; 
int affectedRow = queryRunner.update(connection,sql,"张三",1);//返回受影响的行数
```


# 正则表达式

\ \d:表示一个任意的数字

```java
String content = "查询的内容"；
String s = "\\d\\d\\d\\d";
//创建模式对象[即正则表达式对象]
Pattern pattern = Pattern.compile(s);
//创建匹配器 按照即正则表达式对规则去匹配content
Matcher matcher = pattern.matcher(content);
//开始匹配
while(matcher.find()){
    System.out.println(matcher.group(0));
}
```

():分组

/*group(0):表示匹配到的整体的字符串
group(1):表示匹配到的字符串的第一组。。。
*/

#### 语法

- ```java
  /*
  转意号\\:在java正则表达式中两个\\代表其他语言中的一个\
  []:[abc] 匹配a、b、c中的任意一个字符
  [^]:[^abc] 匹配除a、b、c之外的任意一个字符、数字、特殊字符
  
  -:A-Z 任意单个大小字母
  .:匹配除\n以外的任何字符        a..b：a开头，b结尾，中间包括两个任意字符
  \\d:匹配单个数字字符        \\d\\d\\d-->\\d{3}    (\\d)?:有可能有一个数字，有可能没有                                  (\\d)*任意个数字字符
  \\D:匹配当非数字字符-->[^0-9]
  \\w:匹配数字、单个大小写字符-->[0-9a-zA-Z]
  \\W:[^0-9a-zA-Z]
  \\s:匹配任何空白字符(空格、制表符等)
  \\S:匹配任何非空白字符
  |:ab|cd ab或cd
  *:指定字符出现0次或n次
  +:指定字符至少出现1次
  ?:指定字符最多出现1次(此字符紧跟其它限定符(*、+、?、{n}、{n,}、{n,m})之后，匹配模式是非贪心的)
  {n,}:指定至少n个匹配 [abcd]{3,}-->由a、b、c、d中字母组成的任意长度不小于3的字符串
  {n,m}:length长度区间[n,m]
  ^:指定起始字符   ^[0-9]+ 至少以一个数字开头
  $:指定结束字符 ^[0-9]+[a-z]+$ 至少以一个小写字母结尾
  \\b:匹配目标字符串的边界  边界指目标字符串的结束位置或字符串间有空格
  \\B:匹配目标字符串的非边界
  (?i)abc:表示abc都不区分大小写
  a(?i)bc:表示bc都不区分大小写
  a((?i)b)c:表示只有b不区分大小写
  Pattern pattern = Pattern.compile("abc",Pattern.CASE_INSENSITIVE);表示abc都不区分大小写
  (?<name>pattern):命名捕获  将匹配到的字符串捕获到一个组名或编号名称中
  //非捕获分组，无法用matcher.group()
  (?:pattern):匹配pattern但不捕获该匹配的子表达式，即它是一个非捕获匹配，不存储供以后使用的匹配
  industr(?:y|ies)=industry|industries
  (?=pattern):非捕获匹配  Windows(?=95|98|2000)匹配Windows95/98/2000中的Windows
  (?!pattern):Windows(?=95|98|2000)不匹配Windows95/98/2000中的Windows，匹配其他Windows例如Windows7、Windows8中的Windows
  */
  ```

  java匹配默认贪婪匹配，即匹配多的

"aaaaaa"   a{3,4}  匹配结果:aaaa

boolean b = pattern.matches(pattern,content)//matcher.matches():整体匹配
matcher.repalceAll(str):返回替换后的字符串

反向引用：()里的内容被捕获后，可以在()后被使用。内部反向引用\ \分组号，外部反向引用$分组号

匹配5个连续的相同数字：(\ \d)\ \1{4}

ABBA类型(1221、4554)：(\ \d)(\ \d)\ \2\ \1

(.)\ \1+规则捕获后使用matcher.repalceAll("$1"):我我我要要学习-->我要学习

去重:content = Pattern.compile("(.)\ \1+").matcher(content).replaceAll("$1");
