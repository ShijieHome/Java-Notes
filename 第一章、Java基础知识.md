# 一、Java 基础



## 1、基础知识

**1.1、变量命名：**必须按照**英文字母开头，后面接字母，数字和下划线**组合。

<img src="C:\Users\z00642646\AppData\Roaming\Typora\typora-user-images\image-20220307103727096.png" alt="image-20220307103727096" style="zoom: 50%;" />



**1.2、Java 数据类型分类**

<img src="C:\Users\z00642646\AppData\Roaming\Typora\typora-user-images\image-20220308091712935.png" alt="image-20220308091712935" style="zoom: 50%;" />

- **注意：**
  1. 基本类型在 java 中不属于对象，其包装类属于对象类型



**1.2、基本数据类型**

<img src="C:\Users\z00642646\AppData\Roaming\Typora\typora-user-images\image-20220308092029682.png" alt="image-20220308092029682" style="zoom: 50%;" />

- **注意：**
  1. 布尔类型：boolean，理论上布尔型只需要 1 bit，但是 JVM 会把 boolean 表示为 4 字节整数；
  2. 一个字节（byte）有 8 个二进制（bit）



**1.3、引用数据类型**

<img src="C:\Users\z00642646\AppData\Roaming\Typora\typora-user-images\image-20220308092512302.png" alt="image-20220308092512302" style="zoom:50%;" />

- **注意**：
  1. 32位系统，指针占4个字节（32 / 8 = 4）， 64位系统，指针占8个字节（64 / 8 = 8）



**1.4、方法格式**

<img src="C:\Users\z00642646\AppData\Roaming\Typora\typora-user-images\image-20220210212437674.png" alt="image-20220210212437674" style="zoom: 50%;" />

```java
class StructureAndData {
    // 程序都是从 main 方法开始执行。为了能运行这个程序，必须包含 main 方法并且创建一个实例对象。
    static public void main(String[] args) {
        int x = 100;
        int y = x; // y 是由JVM重新分配了一个储存单元，并且写入和x一样的值
        x = 200; // 此时 x 已经声明过了，可以直接赋值
        
        // 多变量声明，不建议
        int a, b, c;
        int a = 1, b = 2, c = 3;

        //常量，名称大写，表示常用的数字；常量不可以再复制改变，会报错
        final double PI = 3.14;
    
        // var 关键词，当类型名字过长，可以使用 var 省略变量类型
        StringBuilder sb1 = new StringBuilder(); // var sb2 = new StringBuilder();
    }
} // class定义结束
```



## 2、整数

> Java 计算优先级（从高到低）
> 1. 后缀：(), [], .
> 2. 一元：!, ~, ++, --
> 3. 乘性：*, /, %
> 4. 加性：+, -
> 5. 移位：<<, >>, >>>
> 6. &
> 7. ^
> 8. |
> 9. &&
> 10. ||
> 11. ? :
> 12. 赋值：+=, -=, *=, /=
>

```java
// 定义
int decimal = -2147483648;
int i = 2_000_000_000; // 加下划线更容易识别
long l = 9000000000000000000L; // long型的结尾需要加L，使用大写防止混淆
int binary = 0b1000000000; // 二进制
int octal = 0144; // 八进制
int hexa = 0xff0000; // 十六进制，15 = 0xf = ob1111

// 运算
int i3 = 12345 / 16; // 771, 整数除法只能得到整数部分，即整数只可以精确表示
int i4 = 10 % 3; // 1, 取余数

// 溢出，int 4 个字节，如果溢出不会报错，但是结果很奇怪；可以使用 long 来定义比较大的整数
int x = 15;
int y = 2147483640;
int sum = x + y; // -2147483641

// 自加和自减，比如 n++, i--; ++n 表示先加一，再引用 n ; n++ 表示先引用 n ，再加一
int n = 5;
int n1 = n++; // n1 = n = 5, n = 5 + 1 = 6
int n2 = --n; // n = 6 - 1 = 5, n2 = n = 5

// 移位
int a = 7;
int b = a << 1; // 14，左移一位乘 2
int d = a >> 2; // 1，右移一位除 2
int e = -8 >>> 1; // 2147483644, 无符号右移，不管符号位（第一位），右移后高位总是补 0。会变正数因为符号位由 1 变为 0

// 位运算，与、或、非和异或
int z1 = 0 & 1; // 0
int z2 = 0 | 1; // 1
int z3 = ~0; // 1
int z4 = 0 ^ 1; // 1, 异或口诀：同归于尽，相同为 0，不同为 1 
```



## 3、浮点数

> 1. 与整数不同，浮点数不能精确表示，且浮点数只能进行加减乘除，不能移位运算和位运算 
> 2. 整数除法除以 0 会报错，但是浮点数除以 0 不会报错，但是会返回三个特殊值
> 3. 浮点数强制转型为整数时，浮点数会舍弃小数（而非四舍五入）。如果转型后超过了整型最大值，将返回其最大值
> 4. 浮点数可表示的范围非常大，float 类型可最大表示 3.4x10^38，而 double 类型可最大表示 1.79x10^308
> 6. 小数默认是 double 类型浮点型，在定义 float 类型时必须在数字后面跟上 F 或者 f

```java
// 浮点数
float f1 = 3.14f;
float f2 = 3.14e38f; // 科学计数法表示的 3.14x10^38
double d2 = -4.9e-324; // 科学计数法表示的 -4.9x10^-324

// 类型转换
double y = 1 - 9.0 / 10; // 0.099...98，int 和 double 运算结果是 double
double d = 1.2 + 24 / 5; // 5.2, 两个整数的运算不会自动提升

// 浮点数比较：比较两个浮点数绝对值之差是否小于一个很小的值
double r = Math.abs(x - y);
if (r < 0.00001) {
    System.out.println("x is equal to y");
} else {
    System.out.println("x is not equal to y");
}

// 溢出
double b1 = 0.0 / 0; // NaN，注意 NaN 和任何数字比较都是false, 应该用 Double.isNan(), Float.isNaN() 判断
double b2 = 1.0 / 0; // Infinity
double b3 = -1.0 / 0; // -Infinit

// 强制转换
int n1 = (int) -12.7; // -12
int n2 = (int) 1.2e20; // 2147483647
```



## 4、布尔数 

```java
// 布尔数的短路运算，根据前半部分直接返回，忽略后半部分
boolean b1 = (3 > 5) && (5 / 0 > 0); // 因为 false && anything = false，所以直接返回 false
boolean b2 = (3 < 5) || (5 / 0 > 0); // true
boolean b2 = !(3 < 5); // false
```



## 5、 三元运算

`variable x = expression ? value_1 (if true) : value_2 (if false)`

```java
// 三元运算符, b ? x : y, 根据布尔表达式结果选择返回其中一个结果
int n = -99;
int x = n > 0 ? n : -n; // 99
```



##  7、数组

> 数组特点：
>
> - 数组所有元素初始化为默认值，整型都是 0，浮点型是 0.0，布尔型是 false
> - 数组一旦创建后，大小就不可改变
> - 数组元素可以为基本类型，如 int；或者引用类型，如 String
>
> **常用方法：**
>
> - `int Arrays.binarySearch(Object[] a, Object key)`：二分法查找某值，返回索引或 -1。前提是数组已排序
> - `boolean Arrays.equals(long[] a1, long[] a2)`：判断相等，如果两个数组以相同顺序包含相同的元素，则两个数组是相等的
> - `void Arrays.fill(int[] a, int val)`：将 val 分配给数组指定范围内的每个元素，可在数组后加 fromIdx 和 toIdx
> - `void Arrays.sort(int[] a, fromIdx, toIdx)`：升序排列，可指定区间
> - `array.length`：数组长度
> - `Arrays.copyOf(arr, size), Arrays.copyOfRange(arr, fromIdx, toIdx)`：复制数组，截取部分数组
> - `Arrays.toString(arr), Arrays.deepToString(NDimArray)`：转化为字符串，多维数组


```java
// 声明数组
int[] arr; // 不推荐 int arr1[]

// 创建数组，创建变量并赋值
int[] arr1 = new int[2]; 
int[] arr2 = new int[] { 68, 79, 91, 85, 62 }; // 可用于 return new int[] {...}
int[] arr3 = {43, 43, 23, 52, 12}; // 43，简化
Arrays.fill(arr1, 0); // 可用于新建一个全零数组

// 对于引用类型，储存的是对象的引用
String[] names = {"Z", "SJ"};
String s = names[1]; // 保存引用
names[1] = "QJ"; // 原来字符串并没变，只是 names[1] 的引用指向了新建的 QJ，原来的 SJ 无法被引用到了

// 遍历 for/for each
int[] ns = {9, 1, 4, 16, 25, 3};
for(int i = 0; i < ns.length; i++) {
    System.out.println(ns[i]);
}
for(int n : ns) {
    System.out.println(n);
}
System.out.println(Arrays.toString(ns)); // 打印数组内容 [1, 4, 9, 16, 25]

// 排序
String[] ns2 = {"Shijie", "Qijing", "Meimei"};
Arrays.sort(ns); // 正序 [1, 3, 4, 9, 16, 25]
Arrays.sort(ns2); // 虽然字符串没变，但是 ns2 每个元素内存指向都变了

// 多维数组
int[][] ns3 = {{1, 2, 3}, {4, 5}, {6, 7, 8, 9}}; // array[row][col]
System.out.println(Arrays.deepToString(ns3)); // 打印多维数组，也可以多个 for each 嵌套

// 复制，而不引用数组
int[] ns = Arrays.copyOf(scores, scores.length);
int[] ns2 = Arrays.copyOfRange(scores, 2, 6) // 截取部分数组，类似 python scores[2:6]，含 2，不含 6

// 数组清零
Arrays.fill(passwordString, (char) 0x00);

// 数组排序，lambda 函数
Arrays.sort(array, (s1, s2) -> {
    return s1.compareTo(s2);
});
```



## 8、基本类型转换

1. 整型、实型（常量）、字符型数据可以混合运算。运算中，不同类型的数据先转化为同一类型，然后进行运算。
2. 转换从低级到高级：`byte, short, char -> int -> long -> float -> double`
3. 必须满足转换前的数据类型的位数要低于转换后的数据类
4. 如果两数类型不一致，则结果为较大类型整数。如果强制将大范围整数转小，则高位直接扔掉，结果会错误
5. 强制转换：`(type) value`

```java
char c1 = 'a'; 
int i1 = c1; // 97，char 自动类型转换为 int

char c2 = 'A'; 
int i2 = c2 + 1; // 65 + 1 = 66，char 类型和 int 类型计算

int i1 = 123;
byte b = (byte) i1; // 123
```



## 9、分支和循环

**1、if - else**

```java
if(布尔表达式 1) {
    ...;
} else if(布尔表达式 2) {
    ...;
} else if(布尔表达式 3) {
    ...;
} else {
    ...;
}
```



**2、switch**

> switch 语句中的变量类型可以是： byte、short、int、char 和 String.

```java
int option = 3;
switch (option) {
    case 1: // 冒号
        System.out.println("Selected apple");
        break; // break不能丢
    case 2: // 两个选项, 一个动作
    case 3:
        System.out.println("Selected Orange");
        System.out.println("Good Choice");
        break;
    default: // 其他
        System.out.println("Selected nothing");
        break;
}
```



**3、while / do - while**

```java
// while
int sum = 0;
int n = 1;
while (n <= 100) {
    sum += n;
    n++;
}

// do while
sum = 0; // 不能重复申明，已经申明过了
int i = 1;
do {
    sum += i;
    i++;
} while (i <= 100);

System.out.println(sum); //5050
```



**4、for / for each**

```java
// for 
int[] nums = {1, 3, 45, 423, 12};
sum = 0;
for (int k = 0; k < nums.length; k++) { // for循环中三个条件可不全，用分号
    sum += nums[k];
}

// for each
for (int n1 : nums) { // 用冒号
    ...;
}

// break 跳出当前循环体；用 continue 跳出本次循环，进行下一次循环
for (int i2 = 10; i2 > 0; i2--) {
    if (i2 % 2 == 1) {
        continue;
    }
    System.out.println(i2); // 10 8 6 4 2
}
```



## 10、变量类型

> Java 支持的变量类型有：
>
> 1. **类变量**：独立于方法之外的变量，用 static 修饰
> 2. **实例变量**：独立于方法之外的变量，不过没有 static 修饰
> 3. **局部变量**：类的方法中的变量

```java
public class Variable{
    static int allClicks = 0; // 类变量
    String str = "hello world"; // 实例变量
    
    public void main(){
        int i = 0; // 局部变量
    }
}
```



**1、局部变量**

- 局部变量声明在方法、构造方法或者语句块中
- **局部变量没有默认值，所以局部变量被声明后，必须经过初始化，才可以使用**
- 访问修饰符不能用于局部变量
- 局部变量的作用域：

<img src="C:\Users\z00642646\AppData\Roaming\Typora\typora-user-images\image-20220210212713877.png" alt="image-20220210212713877" style="zoom:67%;" />

```java
public void pupAge(){
    int age;
    age = age + 7; // Error，未初始化，不可使用
}
```



**2、实例变量**

- 实例变量声明在一个类中，但在方法、构造方法和语句块之外
- **实例变量具有默认值，不初始化也可以直接使用。数值型变量是 0，布尔型变量是 false，引用类型变量是 null**。
- 变量的值可以在声明时指定，也可以在构造方法中指定
- 访问修饰符可以修饰实例变量
- 实例变量可以直接通过变量名访问。但在静态方法以及其他类中，就应该使用完全限定名：`ObejectReference.VariableName`
- **类变量（即静态变量）**和实例变量相似，但必须用 static 声明，且声明之后不可变。静态变量储存在静态存储区。经常被声明为常量。类变量被声明为 public static final 类型时，类变量名称一般建议使用大写字母。

```java
public class Employee{
    // 私有变量，仅在该类可见
    private double salary;

    //设定 salary 的值
    public void setSalary(double empSal){
        salary = empSal;
    }  
}
```
