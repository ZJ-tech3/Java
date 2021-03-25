# Java基本语法

## 0回顾

JDK=JRE+Java的开发工具（java,javac,javadoc）

JRE=JVM+Java的核心类库

固定写法：

```java
class name

{

	public static void main(String[]  args)

	{

	System.out.println("-----");

	}

}
```

`\n`换行

编译:javac     运行：java

编译报错：语法问题

运行问题：应该是计算错误

path环境变量：Windows操作系统执行命令时搜寻的路径

## 1关键字和保留字

关键字：赋予特殊含义的单词（**所有关键字都是小写**）

保留字：现有版本尚未使用，以后可能会用 goto、const

**注意：命名时避免使用保留字。**

## 2标识符

标识符：对各种变量、方法和类等要素命名时使用的字符序列（自己起名字的地方）

**命名规则**：

1. 26个英文大小写，0-9，_或$
2. 数字不能开头
3. 不可以使用关键字和保留字，但是可以包含
4. 严格区分大小写，长度无限制
5. 不能包含空格

如果不符合规则，编译不通过。

**命名规范**：

1. 包名：小写。
2. 类名、接口名：单词首字母大写。
3. 变量名、方法名：第**二**个单词开始首字母大写。
4. 常量名：所有字母大写，单词中间用下划线隔开。

不遵守规范，编译一样通过。

## 2.3变量

变量是程序中最基本的存储单元。包含：变量类型、变量名、存储的值。

格式：类型 变量名 = 变量值；

说明：

1. 必须先声明后使用。
2. 超出作用域就会失效。
3. 同一个作用域内不可以声明两个相同名字的变量。

### Java中的数据类型

**基本数据类型（8种）：**byte,short,int,long;float,double;char;boolean。

**引用数据类型（3种）：**类class；接口interface;数组arr。

整数类型：byte,short,int,long。

|  类型   | 空间  | 范围                                  |
| :-----: | ----- | ------------------------------------- |
|  byte   | 1字节 | -128~127                              |
|  short  | 2字节 | -2E15~2E15-1                          |
|   int   | 4字节 | -2E31~2E31-1                          |
|  long   | 8字节 | -2E63~2E63-1                          |
|  float  | 4字节 | -3.403E38~3.403E38                    |
| double  | 8字节 | -1.798E308~1.798E308                  |
|  char   | 2字节 | 字符，转义字符，Unicode字符集‘\u0043’ |
| boolean |       | true/false                            |

**说明**：

1. long必须以大写或小写L结尾；通常用int。
2. float表示数值的范围比long还大。 
3. float变量末尾以f或F结尾。
4. 通常用double.
5. a-->97  A-->65，char可以用ascII码赋值。
6. 句中的\n也会换行

### 基本数据类型之间的运算规则

前提：7种数据类型，不包含boolean类型。

1. **自动类型提升**

自动变为表示数的范围更大的数据类型

byte、short、char --> int --> long --> float --> double

前三种类型做变量时，计算结果为int。

2. **强制类型转换**

自动类型提升的逆运算。

需要使用强转符（）；可能导致精度损失；

**注意**：

* long星赋值末尾不加L，会自动变为int，所以有时候不加也不会报错。float末尾必须加，否则会报错。
* **整型常量默认为int;浮点型默认为double。**

### String类型变量的使用

1. 属于引用数据类型，字符串。
2. 使用时**必须**用一对双引号“”。
3. String可以和8种基本数据类型变量做运算，且运算只能是连接（+）运算。
4. 连接结果仍然是String类型。

**注意**：

1. String str1=4;//错误。
2. String 和int不能直接转换。

### 进制与进制之间的转换

二进制：0b或0B开头

十进制：

八进制：数字0开头

十六进制：ox或0X开头

二进制最高位：0 正数、1 负数。

正数原码、反码、补码一样；

反码：除了符号位，各个位取反；

补码：反码+1

已知补码：补码-1--->取反得到原码---->然后计算得到结果

-128 底层位1000 0000

**计算机底层都以补码的形式存储数据。**

## 2.4运算符

分类：算术运算符、赋值运算符、比较运算符、逻辑运算符、三元运算符

### 1. 算术运算符

* 取余运算：结果的符号与被模数一样；
* byte bbq =127   ;   bb1自加1----->-128；

### 2. 赋值运算符

* += 和自增减不改变数据类型

* 数字加2，不能连用两个++：~~a++++~~
* i2=j2=10

### 3. 比较运算符

* 运算结果都是boolean型

### 4. 逻辑运算符

* &前面为false，继续判断后面
* &&前面为false，后面的直接跳过不执行
* ==和！=可以使用在数值数据类型和引用数据类型
* \> \<  \>=  \<= :只能使用在数值类型数据之间
* |与||同上

```java
//问题：
public class Test {
	public static void main (String []	args){  
		boolean x = true;
		boolean y = false;  
		short z = 42;
		if(y == true)  
		if((z++ == 42)&&(y = true))z++;  
		if((x = false) || (++z == 45)) z++;
		System. out.println("z=" + z);
	}
}
//输出结果z=43;

//问题：
public class Test {
	public static void main (String []	args){  
		boolean x = true;
		boolean y = false;  
		short z = 42;
		//if(y == true)  
		if((z++ == 42)&&(y = true))z++;  
		if((x = false) || (++z == 45)) z++;
		System. out.println("z=" + z);
	}
}
//输出结果z=46；
/*解析：
z++ == 42；先取值再运算，42 == 42，表达式值为真，再运算后z是43；&&右边要参与运算；
y = true；注意这里是赋值号，y赋值为真，则(z++ == 42)&&(y = true)为真，执行z++，z是44了；
x = false，同样注意这里是赋值号，x赋值为假，||右边要参与运算；
++z == 45；先运算再取值，运算后z是45，45 == 45，表达式为真；则(x = false) || (++z == 45)值为真，执行z++；z是46了。*/

//问题：
public class Test {
	public static void main (String []	args){  
		boolean x = true;
		boolean y = false;  
		short z = 42;
		if(y == true)  
		if((z++ == 42)&&(y = true))z++;  
		//if((x = false) || (++z == 45)) z++;
		System. out.println("z=" + z);
	}
}
//输出：z=42

//问题：
public class Test {
	public static void main (String []	args){  
		boolean x = true;
		boolean y = false;  
		short z = 42;
		if(y == true)  
		//if((z++ == 42)&&(y = true))z++;  
		if((x = false) || (++z == 45)) z++;
		System. out.println("z=" + z);
	}
}
//输出：z=42

```

### 5. 位运算符

* \>\>\>无符号右移；没有无符号左移
* 位运算符操作整型变量
* \<\<：在一定范围内，相当于*2         8\*2计算可用位运算
* \>\>：在一定范围内，相当于/2
* 乘法用位运算效率高
* 右移最高位是1，左边补1；否则补0
* 左移和无符号右移都用0补
* ^异或   ~取反（包括符号位都取反）

交换变量：常见定义临时变量；位运算（m=m^n^m）；加减计算

### 6.三元（目）运算符

**格式：**（条件表达式）？表达式1：表达式2；

**说明：**

* 条件表达式结果为boolean类型
* 结果为true，执行表达式1；结果为false，执行表达式2
* 表达式1和表达式2要求是一致的（两个表达式可以转换成一个类型）
* 能用三元运算符的都可以改写为if-else结构，反之不成立
* 三元运算符效率高，更简洁

运算符的优先级，先算的加括号。

## 2.5程序流程控制

顺序结构、分支结构、循环结构

### 1.顺序结构

### 2.1.分支结构（if-else）

二选一、多选一

**说明：**

* else是可选的，可以不写；
* 条件表达式没有交集的情况，判断和执行语句的顺序不影响
* 有交集的情况，要注意判断顺序。
* 包含情况下，范围小的写在上面。
* else配对为就近原则

### Java Scanner 类

**具体实现步骤：**

1. 导包：import java.util.Scanner;
2. Scanner的实例化；Scanner scan=new Scanner(System.in);
3. 调用Scanner类的相关方法next()或nextXxxx()，来获取指定类型的变量

获取字符串中的字符：char a=S.charAt(0);

**注意：**需要根据相应的方法，来输入指定类型的值。如果输入的数据类型与要求的数据类型不匹配，会报异常，运行终止。

java.util.Scanner 是 Java5 的新特征，我们可以通过 Scanner 类来获取用户的输入。

下面是创建 Scanner 对象的基本语法：

Scanner s = new Scanner(System.in);

```java
import java.util.Scanner; 
 
public class ScannerDemo {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        // 从键盘接收数据
 
        // next方式接收字符串
        System.out.println("next方式接收：");
        // 判断是否还有输入
        if (scan.hasNext()) {
            String str1 = scan.next();
            System.out.println("输入的数据为：" + str1);
        }
        scan.close();
    }
}
```

### 随机数的产生

double value=Math.random();//[0.0,1.0)

公式：[]a,b]:(int)(Math.random()*(b-a+1)+a)

### 2.2.swith-case结构

```java
switch(表达式)
{
        case 常量1：
            执行语句1；
            break;
        
        case 常量2：
            执行语句2；
            break;
        
        ····
        default:
        	执行语句n；
                
}
```

**说明：**

* 执行某个语句后，仍然继续向下执行，直到遇到break或末尾结束。
* break同于跳出switch-case
* 表达式只能为6种数据类型之一：byte、short、char、int、枚举类型（5.0新增）、String类型（7.0新增）。
* 多个case结构相同，可以合并。

### <u>输入日期获取是某一年的多少天</u>

```java
 public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入年：");
        int year = scanner.nextInt();
        System.out.println("请输入月：");
        int month = scanner.nextInt();
        System.out.println("请输入日：");
        int day = scanner.nextInt();
        boolean isRun = false;
        if((year % 4 == 0 && year % 100 !=0 ) || (year % 400 == 0)){
            isRun = true;
        }
       //定义一个变量来保存天数
        int sumDays = 0;
        switch (month){
            case 12: sumDays += 30;
            case 11: sumDays +=31;
            case 10:sumDays += 30;
            case 9:sumDays += 31;
            case 8:sumDays += 31;
            case 7:sumDays += 30;
            case 6:sumDays += 31;
            case 5:sumDays += 30;
            case 4:sumDays += 31;
            case 3:
                if (isRun){
                    sumDays +=29;
                }else {
                    sumDays +=28;
                }
            case 2:sumDays += 31;
            case 1:sumDays += day;
        }
        System.out.println( "今天是："+year+"的第"+sumDays+"天");
    }

```

### 3.循环结构

for、while、do-while

**循环语句的组成部分**：初始化部分、循环条件部分、循环体部分、迭代条件部分

**注意：**

* while循环注意写条件，避免死循环。
* for和while可以相互转换，初始化条件作用范围不同
* do-while使用较少
* 不确定或不限制次数用：for(;;)或while(true)
* 结束循环break
* 最好不要三层嵌套循环

### 获取时间

```java
//当前时间的毫秒数
		long start = System.currentTimeMillis();
		long end = System.currentTimeMillis();
```

### 数字开根号

```java
int a=Math.sqrt(i);
```

### 4.break、continue的使用

break:结束当前循环，continue:结束当次循环，默认结束最近的一层。

**注意：**

**在for前面加标签label:for(···)····；break/continue label;结束指定循环。**

**外层循环控制行数，内层循环控制列数。**

衡量一个功能代码的优劣势：

1. 正确性
2. 可读性
3. 健壮性
4. 高效率与低存储：时间复杂度和空间复杂度



