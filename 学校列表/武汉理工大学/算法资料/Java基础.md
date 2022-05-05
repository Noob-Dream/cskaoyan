# Java基础

## JRE、JDL、JVM的区别与联系

JVM ：英文名称（Java Virtual Machine），就是我们耳熟能详的 Java 虚拟机。它只认识 xxx.class 这种类型的文件，它能够将 class 文件中的字节码指令进行识别并调用操作系统向上的 API 完成动作。所以说，jvm 是 Java 能够跨平台的核心，具体的下文会详细说明。

JRE ：英文名称（Java Runtime Environment），我们叫它：Java 运行时环境。它主要包含两个部分，jvm 的标准实现和 Java 的一些基本类库。它相对于 jvm 来说，多出来的是一部分的 Java 类库。

JDK ：英文名称（Java Development Kit），Java 开发工具包。jdk 是整个 Java 开发的核心，它集成了 jre 和一些好用的小工具。例如：javac.exe，java.exe，jar.exe 等。

显然，这三者的关系是：一层层的嵌套关系。JDK>JRE>JVM

## java程序编写-编译-运行的过程

编写：我们将编写的java代码保存在".java"结尾的源文件中

编译：使用javac.exe命令编译我们的java源文件。格式：javac 源文件名.java

编译的过程：编译以后，会生成一个或多个字节码文件。字节码文件的文件名与java源文件中的类名相同。

运行：使用java.exe命令解释运行我们的字节码文件。格式：java 类名



## java 程序注意

在一个java源文件中可以声明多个class。但是，只能最多有一个类声明为public

而且要求声明为public的类的类名必须与源文件名相同



程序的入口是main()方法。格式是固定的

每一行执行语句都以";"结束。



## java数据类型

long型需要在数字后面加L或者l

如：  

```java
long a = 212312312312124L;
//或者
long b = 213212412312312l;
```

float 型 末尾加 “F”或者“f”



## 输出语句

System.out.println():先输出数据，然后换行
System.out.print():只输出数据

## 输出数组

* 调用Array.toString(a)，返回一个包含数组元素的字符串，这些元素被放置在括号内，并用逗号分开

```java
int[] arr = {1,2,3,4,5}; 
	System.out.println(Arrays.toString(arr));
```

输出：[1, 2, 3, 4, 5]



* 传统的for循环方式

  ```java
  for(int i=0;i<array.length;i++)
  {
        System.out.println(array[i]);
  }
  ```

  

* for each循环

  ```java
  for(int a:array)
      System.out.println(a);
  ```


## 注释

### 单行注释

//xxxx

### 多行注释

/*     .....     */

### 文档注释

**/\****  ....   */

说明注释允许你在程序中嵌入关于程序的信息。你可以使用 javadoc 工具软件来生成信息，并输出到HTML文件中。

说明注释，使你更加方便的记录你的程序信息。

在开始的 **/\**** 之后，第一行或几行是关于类、变量和方法的主要描述。

之后，你可以包含一个或多个各种各样的 **@** 标签。每一个 **@** 标签必须在一个新行的开始或者在一行的开始紧跟星号(*).

多个相同类型的标签应该放成一组。例如，如果你有三个 **@see** 标签，可以将它们一个接一个的放在一起。

@author 作者

@version 版本

例子：

```java
/*
 * <p>项目名称: ${project_name} </p> 
 * <p>文件名称: ${file_name} </p> 
 * <p>描述: [类型描述] </p>
 * <p>创建时间: ${date} </p>
 * <p>公司信息: ************公司 *********部</p> 
 * @author <a href="mail to: *******@******.com" rel="nofollow">作者</a>
 * @version v1.0
 * @update [序号][日期YYYY-MM-DD] [更改人姓名][变更描述]
 */
```

```java
/**
 * @Title：${enclosing_method}
 * @Description: [功能描述]
 * @Param: ${tags}
 * @Return: ${return_type}
 * @author <a href="mail to: *******@******.com" rel="nofollow">作者</a>
 * @CreateDate: ${date} ${time}</p> 
 * @update: [序号][日期YYYY-MM-DD] [更改人姓名][变更描述]     
 */
```

```java
/**
 * 获取  ${bare_field_name}
 */



/**
 * 设置   ${bare_field_name} 
 * (${param})${field}
 */
```

## Java 关键字

定义：被java语言赋予了特殊含义，用作专门用途的字符串（单词）

特点：关键字中所有字母均为小写

![Xnip2020-01-03_16-14-57](/Users/yangshucheng/Documents/截图/Xnip2020-01-03_16-14-57.jpg)

![image-20200103161246326](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200103161246326.png)

|          | 数据       | 类型     | 关键字       |          |
| -------- | ---------- | -------- | ------------ | -------- |
| class    | interface  | enum     | byte         | short    |
| int      | long       | float    | double       | char     |
| boolean  | void       |          |              |          |
|          | 流程控制   | 关键字   |              |          |
| if       | else       | switch   | case         | default  |
| while    | do         | for      | break        | continue |
| return   |            |          |              |          |
|          | 访问权限   | 关键字   |              |          |
| private  | protect    | public   |              |          |
|  | 类、函数 | 变量修饰符 | 的关键字 |                      |
| abstract | final      | static   | synchronized |          |
| |类与类   | 之间关系   | 的关键字 ||
| extends  | implements |          |              |          |
| |建立实例 | 判断实例   | 的关键字 |              |
| new | this | super | instanceof |          |
|          | 异常处理 | 的关键字 |              |          |
| try | catch | finally | throw | throws |
|          | 包 | 的关键字 |              |          |
| package | import |          |              |          |
|          | 其他修饰符 | 的关键字 |              |          |
| native | strictfp | tracnsient | volatile | assert数据 |
|          | 数据类型值 | 的字面值 |              |          |
| true | false | null |              |          |

## Java保留字

goto

const

自己命名时要避免使用这些保留字

## 标识符的使用

定义：凡是自己可以起名字的地方都叫标识符

设计到的结构：包名、类名、接口名、变量名、方法名、常量名

规则：
* 由26个英文字母大小写，0-9 ，_或 $ 组成
* 数字不可以开头。
* 不可以使用关键字和保留字，但能包含关键字和保留字。
* Java中严格区分大小写，长度无限制。
* 标识符不能包含空格。

## Java中的名称命名规范

* Java中的名臣命名规范
  * **包名**：多单词组成时所有字母都小写：xxxyyyzzz
  * **类名、接口名**：多单词组成时，所有单词的数字母大写：XxxYyyZzz
  * **变量名、方法名**：多单词组成时，第一个单词的首字母小写，第二个单词开始每个单词首字母大写：xxxYyyZzz
  * **常量名**：所有字母都大写。多单词时每个单词用下划线：XXX_YYY_ZZZ
* 注意1：在起名字时，为了提高阅读性，要尽量有意义，见名知意
* 注意2：java采用Unicode字符集，因此标识符也可以使用汉字，但是不建议使用

## Java变量的分类

### 按数据类型分

#### 基本数据类型

![image-20200103155706233](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200103155706233.png)

* 数值型
  * 整数类型(byte,short,int,long)
  * 浮点类型(float,double)
* 字符型(char)
* 布尔型(boolean)

#### 引用数据类型

* 类(class) 比如：Sting
* 接口(interface)
* 数组( [] )

#### 详细说明

1. 整型：byte(1字节=8bit)\short(2字节)\int(4字节)\long(8字节)

   ①byte范围：-128~127

   ②声明long型变量，必须以"l"或者"L"结尾

   ③通常，定义整型变量时，使用int型

   ④整型的常量，默认类型是：int型

   ![image-20200103155828118](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200103155828118.png)

2. 浮点型：float(4字节)/double(8字节)

   ①浮点型，表示带小数点的数值

   ②float表示数值的范围比long还大

   ③定义float类型变量时，变量要以"f"或者"F"结尾

   ④通常，定义浮点型变量时，使用double型

   ⑤浮点型的常量，默认类型为：double

   ![image-20200103160237992](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200103160237992.png)

3. 字符型：char（1字符=2字节）

   ①定义char型变量，通常使用一对' ',内部只能写一个字符

   ②表示方式：

   ​	1.声明一个字符

   ​	2.转义字符

   ​	3.直接使用Unicode值来表示字符型常量

   

   ![image-20200103160330788](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200103160330788.png)

4. 布尔型：boolean

   ①只能取两个值之一：true、false

   ②常常在条件判断、循环结构中使用

### 按变量的分类-按声明的位置的不同分类

* 在方法体外，类体内声明的变量称作**成员变量**

* 在方法体内部声明的变量称作**局部变量**

  ![image-20200103171603330](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200103171603330.png)

## 变量声明

* 声明变量
    语法:<数据类型> <变量名称> 

  ​     例如:int var;

* 变量的赋值
    语法:<变量名称> = <值> 

  ​     例如:var = 10;

* 声明和赋值变量
    语法: <数据类型> <变量名> = <初始化值> 

  ​     例如:int var = 10;

### 使用变量注意

1. Java中每个变量必须先声明，后使用 

2. 使用变量名来访问这块区域的数据 

3. 变量的作用域:其定义所在的一对{ }内 

4. 变量只有在其作用域内才有效 

5. 同一个作用域内，不能定义重名的变量

## 基本数据类型变量间运算规则

* 涉及到的基本数据类型：除了boolean外的其他7种

* 自动类型转换（只涉及到7种基本数据类型）

  结论：当容量小的数据类型的变量与容量大的数据类型的变量做运算时，结果自动    提升为容量大的数据类型

  byte、char、short --> int --> long -->float --> double

  特别的：当byte、char、short 三种类型的变量做运算时，结果为int型

  说明：此时的容量大小指的是，表示数的范围的大和小。比如float容量要大于long的容量

* 强制类型转换（只涉及7种基本数据类型）：自动类型提升运算的逆运算

  1. 需要使用强转符：()

  2.  注意点：强制类型转换，可能导致精度损失

```java
//判断是否能通过编译
//1)
short s = 5; 
s = s-2; //判断:no。原因：2是int型的，那么java会把s自动提升为int型，那么结果s+2为int型赋给一个short型会出错，会损失精度，改为s+=2就不会了，因为+=是一个运算符号，java会把2当成short型来处理
//2) 
byte b = 3;
b = b + 4; //判断:no
b = (byte)(b+4); //判断:yes
//3)
char c = ‘a’;
int i = 5;
float d = .314F; 
double result = c+i+d;//判断:yes
//4)
byte b = 5;
short s = 3;
short t = s + b; //判断:no。原因：s+b自动转换成int型，int型赋值给short型会出错，会损失精度
```



## String与8种基本数据类型间的运算

1. String属于引用数据类型，翻译为：字符串
2. 声明String类型变量时，使用一对双引号" "
3. 当把任何基本数据类型的值和字符串(String)进行连接运算时(+)，基本数据类型的值将自动转化为字符串(String)类型
4. String可以和8种基本数据类型做运算，且运算只能是连接运算：+
5. 运算的结果仍然是String类型

* 避免

  String s = 123;//编译错误

  String s1 = "123";

  int i = (int)s1;//编译错误

```java
		String s2 = "a";
		String s3 = "";

		//char c = '';//编译不通过,不能为空

		//***********************
		int number = 1001;
		String numberStr = "学号：";
		String info = numberStr + number;// +：连接运算
		boolean b1 = true;
		String info1 = info + b1;// +：连接运算
		System.out.println(info1);

		//***********************
		//练习1
		char c = 'a';//97   A:65
		int num = 10;
		String str = "hello";
		System.out.println(c + num + str);//107hello
		System.out.println(c + str + num);//ahello10
		System.out.println(c + (num + str));//a10hello
		System.out.println((c + num) + str);//107hello
		System.out.println(str + num + c);//hello10a

		//练习2
		//*	*
		System.out.println("*	*");//* *
		System.out.println('*' + '\t' + '*');//93
		System.out.println('*' + "\t" + '*');//* *
		System.out.println('*' + '\t' + "*");//51*
		System.out.println('*' + ('\t' + "*"));//* *


		//***********************

		//String str1 = 123;//编译不通过
		String str1 = 123 + "";
		System.out.println(str1);//"123"
		
		//int num1 = str1;
		//int num1 = (int)str1;//"123"

		int num1 = Integer.parseInt(str1);
		System.out.println(num1);//123
```

## 二进制

对于整数，有四种表示方式:

* 二进制(binary):0,1 ，满2进1**.以0b或0B开头**。
* 十进制(decimal):0-9 ，满10进1。
* 八进制(octal):0-7 ，满8进1. 以**数字0开头**表示。
* 十六进制(hex):0-9及A-F，满16进1. **以0x或0X开头**表示。此处的A-F不区分大小写。 如:0x21AF +1= 0X21B0

计算机以二进制补码方式存储

* 进制基本转换

  ![image-20200103204104582](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200103204104582.png)



## 算数运算符

### 运算符之一：算术运算符

1.  \+   \-   \*   /   %  (前)++ (后)++ (前)-- (后)-- +
2.  (前)++ :先自增1，后运算    ++a
    (后)++ :先运算，后自增1    a++
3.  (前)-- :先自减1，后运算    --a
    (后)-- :先运算，后自减1    a--
4.   %:取余运算
    结果的符号与被模数的符号相同
    开发中，经常使用%来判断能否被除尽的情况。

### 运算符之二：赋值运算符

=  +=  -=  *=  /=  %= 

【典型代码】

```java
int j1 = 10;
int i2,j2;//连续赋值
i2 = j2 = 10;
int i3 = 10,j3 = 20;
```

【特别说明】

1. 运算的结果不会改变变量本身的数据类型

    ```java
    //练习1
    int i = 1;
    i *= 0.1;
    System.out.println(i);//0
    i++;
    System.out.println(i);//1
    ```

2. 变量的常见处理方法

   ```java
   //开发中，如果希望变量实现+2的操作，有几种方法？(前提：int num = 10;)
   //方式一：num = num + 2;
   //方式二：num += 2; (推荐)	
   //开发中，如果希望变量实现+1的操作，有几种方法？(前提：int num = 10;)
   //方式一：num = num + 1;
   //方式二：num += 1; 
   //方式三：num++; (推荐)
   ```

3. 关于赋值符号 = 两边的类型必须一致

```java
short a = 1;
//a = a + 2;  //编译出错，左右两边类型不一致
a += 2; //不会改变变量本身的数据类型
System.out.println(a); 
```


注意a的类型：a如果是short类型的变量，在和int类型的1进行运算时会自动的将short->int, 然后执行复制操作符“=”,就会发生类型的错误，左边是short类型，右边是int类型的变量

### 运算符之三：比较运算符

* ==  !=  >  <  >= <=  instanceof

* 结论：
  1. 比较运算符的结果是boolean类型
  2. 区分 ==（比较是否相等）  和  = （赋值）
  3. \>  \<  \>=  \<=  : 只能使用在数值类型的数据之间
  4. == : 不仅可以使用在数值类型数据之间，还可以使用在其他引用类型变量之间

```java
Account acct1 = new Account(1000);
Account acct2 = new Account(1000);
boolean b1 = (acct1 == acct2);//比较两个Account是否为同一个账户
boolean b2 = (acct1 != acct2);//比较两个Account是否为不同账户
```

### 运算符之四：逻辑运算符

* &  && |  || ! ^

![image-20200128212154109](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200128212154109.png)

* 区分& 与 &&
  相同点1：& 与  && 的**运算结果相同**
  相同点2: 当符号左边是true时，二者都会执行符号右边的运算
  不同点：当符号左边是false时，**&继续执行**符号右边的运算。**&&不再执行符号**右边的运算。
  开发中，**推荐使用&&**
* 【特别说明】：逻辑运算符操作的都是boolean类型的变量

### 运算符之四：位运算符

* \<<       \>>     \<<<      \>>>   |  &  ^
* \<<       \>>         (有符号移位运算)
* \<<<      \>>>      (无符号移位运算)
* 位运算符操作的都是整型的数据

* << ：在一定范围内，每向左移1位，相当于 * 2

​      \>> :  在一定范围内，每向右移1位，相当于 / 2

* 【面试题】 最高效方式的计算2 * 8 ？  2 << 3  或 8 << 1

### 交换两个变量的办法

* 异或( ^ )与或( | )的不同之处是:当左右都为true时，结果为false

k = m ^ n

m = k ^ n = (m ^ n ) ^ n    

```java
    int num1 = 10;
		int num2 = 20;
		System.out.println("num1 = " + num1 + ",num2 = " + num2);

		//方式一：定义临时变量的方式
		//推荐的方式
		int temp = num1;
		num1 = num2;
		num2 = temp;

		//方式二：好处：不用定义临时变量  
		//弊端：① 相加操作可能超出存储范围 ② 有局限性：只能适用于数值类型
		//num1 = num1 + num2;
		//num2 = num1 - num2;
		//num1 = num1 - num2;

		//方式三：使用位运算符
		//有局限性：只能适用于数值类型
		//num1 = num1 ^ num2;
		//num2 = num1 ^ num2;
		//num1 = num1 ^ num2;

		System.out.println("num1 = " + num1 + ",num2 = " + num2);
```

### 如何求一个0~255范围内的整数的十六进制值，例如60的十六进制表示形式3C

```java
//方式一：自动实现
String str1 = Integer.toBinaryString(60);
String str2 = Integer.toHexString(60);

//方式二：手动实现
int i1 = 60;
int i2 = i1&15;
String j = (i2 > 9)? (char)(i2-10 + 'A')+"" : i2+"";
int temp = i1 >>> 4;
i2 = temp & 15;
String k = (i2 > 9)? (char)(i2-10 + 'A')+"" : i2+"";
System.out.println(k+""+j);
```

### 运算符之四：三元运算符

1. 结构：**(条件表达式)? 表达式1 : 表达式2**
2. 说明
   ① 条件表达式的结果为boolean类型
   ② 根据条件表达式真或假，决定执行表达式1，还是表达式2.
     如果表达式为true，则执行表达式1。
     如果表达式为false，则执行表达式2。
   ③ 表达式1 和表达式2要求是一致的。
   ④ 三元运算符可以嵌套使用

3. 凡是可以使用三元运算符的地方，都可以改写为if-else
反之，不成立。
4. 如果程序既可以使用三元运算符，又可以使用if-else结构，那么**优先选择三元运算符**。原因：简洁、执行效率高。

## 流程控制

### 分支结构中的if-else（条件判断结构）

三种结构：

第一种：
if(条件表达式){
	执行表达式
}

第二种：二选一
if(条件表达式){
	执行表达式1
}else{
	执行表达式2
}

第三种：n选一
if(条件表达式){
	执行表达式1
}else if(条件表达式){
	执行表达式2
}else if(条件表达式){
	执行表达式3
}
...
else{
	执行表达式n
}

### switch-case结构

### 循环结构

#### for 

#### while

**While 循环的使用**

一、循环结构的4个要素
① 初始化条件
② 循环条件  --->是boolean类型
③ 循环体
④ 迭代条件

二、while循环的结构

①
while(②){
	③;
	④;
}

执行过程：① - ② - ③ - ④ - ② - ③ - ④ - ... - ②

说明：
1.写while循环千万小心不要丢了迭代条件。一旦丢了，就可能导致死循环！
2.我们写程序，要避免出现死循环。
3.for循环和while循环是可以相互转换的！ 
  区别：for循环和while循环的初始化条件部分的作用范围不同。


算法：有限性。

#### do-while

**do-while循环的使用**

一、循环结构的4个要素
① 初始化条件
② 循环条件  --->是boolean类型
③ 循环体
④ 迭代条件

二、do-while循环结构：

①
do{
	③;
	④;

}while(②);

执行过程：① - ③ - ④ - ② - ③ - ④ - ... - ②

说明：
1.do-while循环至少会执行一次循环体！
2.开发中，使用for和while更多一些。较少使用do-while

### 关键字：beak 和 continue

```java
/*
break和continue关键字的使用
				使用范围			循环中使用的作用(不同点)		相同点
break:			switch-case			
				循环结构中			结束当前循环					关键字后面不能声明执行语句	

continue:		循环结构中			结束当次循环					关键字后面不能声明执行语句

补充：带标签的break和continue的使用

*/
class BreakContinueTest {
*****************************
		label:for(int i = 1;i <= 4;i++){
			for(int j = 1;j <= 10;j++){
				if(j % 4 == 0){
					//break;//默认跳出包裹此关键字最近的一层循环。
					//continue;
					//break label;//结束指定标识的一层循环结构    123
					continue label;//结束指定标识的一层循环结构当次循环//输出   123123123123
				}
				System.out.print(j);
			}
			System.out.println();
		}
	}
}
```

### 质数的输出

#### 优化方式一

定义flag来判断是否为质数

```java
*/
class PrimeNumberTest1 {
	public static void main(String[] args) {
		
		boolean isFlag = true;//标识i是否被j除尽，一旦除尽，修改其值
		int count = 0;//记录质数的个数

		//获取当前时间距离1970-01-01 00:00:00 的毫秒数
		long start = System.currentTimeMillis();

		for(int i = 2;i <= 100000;i++){//遍历100000以内的自然数
			
			//优化二：对本身是质数的自然数是有效的。
			//for(int j = 2;j < i;j++){
			for(int j = 2;j <= Math.sqrt(i);j++){//j:被i去除
				
				if(i % j == 0){ //i被j除尽
					isFlag = false;
					break;//优化一：只对本身非质数的自然数是有效的。
				}
				
			}
			//
			if(isFlag == true){
				//System.out.println(i);
				count++;
			}
			//重置isFlag
			isFlag = true;
		
		}

		//获取当前时间距离1970-01-01 00:00:00 的毫秒数
		long end = System.currentTimeMillis();
		System.out.println("质数的个数为：" + count);
		System.out.println("所花费的时间为：" + (end - start));//17110 - 优化一：break:1546 - 优化二：13

	}
}
```



#### 优化方式二

利用 continue label

```java
class PrimeNumberTest2 {
	public static void main(String[] args) {
		
		
		int count = 0;//记录质数的个数

		//获取当前时间距离1970-01-01 00:00:00 的毫秒数
		long start = System.currentTimeMillis();

		label:for(int i = 2;i <= 100000;i++){//遍历100000以内的自然数
			
			for(int j = 2;j <= Math.sqrt(i);j++){//j:被i去除
				
				if(i % j == 0){ //i被j除尽
					continue label;
				}
				
			}
			//能执行到此步骤的，都是质数
			count++;
		
		}

		//获取当前时间距离1970-01-01 00:00:00 的毫秒数
		long end = System.currentTimeMillis();
		System.out.println("质数的个数为：" + count);
		System.out.println("所花费的时间为：" + (end - start));//17110 - 优化一：break:1546 - 优化二：13

	}
}
```

### 最大公因数与最小公倍数

```java
/*
题目：输入两个正整数m和n，求其最大公约数和最小公倍数。
比如：12和20的最大公约数是4，最小公倍数是60。

说明：break关键字的使用：一旦在循环中执行到break，就跳出循环

*/

import java.util.Scanner;
class ForTest{

	public static void main(String[] args){
	
		Scanner scan = new Scanner(System.in);

		System.out.println("请输入第一个正整数：");
		int m = scan.nextInt();
		
		System.out.println("请输入第二个正整数：");
		int n = scan.nextInt();
		
		//获取最大公约数
		//1.获取两个数中的较小值
		int min = (m <= n)? m : n;
		//2.遍历
		for(int i = min;i >= 1 ;i--){
			if(m % i == 0 && n % i == 0){
				System.out.println("最大公约数为：" + i);
				break;//一旦在循环中执行到break，就跳出循环
			}
		}
		
		//获取最小公倍数
		//1.获取两个数中的较大值
		int max = (m >= n)? m : n;
		//2.遍历
		for(int i = max;i <= m * n;i++){
			if(i % m == 0 && i % n == 0){
				
				System.out.println("最小公倍数：" + i);
				break;
			
			}
		}
		
	}

}

```



##  附加:特殊流程控制语句3

*   **return**:并非专门用于结束循环的，它的功能是**结束一个方法**。 当一个方法执行到一个return语句时，这个方法将被结束。
*   与break和continue不同的是，return直接结束整个方法，不管这个return处于多少层循环之内

##  Scanner 中next() 与 nextLine() 区别

next():

- 1、一定要读取到有效字符后才可以结束输入。
- 2、对输入有效字符之前遇到的空白，next() 方法会自动将其去掉。
- 3、只有输入有效字符后才将其后面输入的空白作为分隔符或者结束符。 
- **next() 不能得到带有空格的字符串**。

nextLine()： 

- 1、**nextLine() 以Enter为结束符,也就是说 nextLine()方法返回的是输入回车之前的所有字符。** 
- 2、**可以获得空白**。

如果要输入 int 或 float 类型的数据，在 Scanner 类中也有支持，但是在输入之前最好先使用 hasNextXxx() 方法进行验证，再使用 nextXxx() 来读取:

```java
private static String readKeyBoard(int limit) {
        String line = "";
        while (scanner.hasNext()) {
            line = scanner.nextLine();
            if (line.length() < 1 || line.length() > limit) {
                System.out.print("输入长度（不大于" + limit + "）错误，请重新输入：");
                continue;
            }
            break;
        }

        return line;
    }//记录并且判断输入字符的长度是否符合要求
```

```java

import java.util.Scanner;
 
public class ScannerDemo {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        // 从键盘接收数据
        int i = 0;
        float f = 0.0f;
        System.out.print("输入整数：");
        if (scan.hasNextInt()) {
            // 判断输入的是否是整数
            i = scan.nextInt();
            // 接收整数
            System.out.println("整数数据：" + i);
        } else {
            // 输入错误的信息
            System.out.println("输入的不是整数！");
        }
        System.out.print("输入小数：");
        if (scan.hasNextFloat()) {
            // 判断输入的是否是小数
            f = scan.nextFloat();
            // 接收小数
            System.out.println("小数数据：" + f);
        } else {
            // 输入错误的信息
            System.out.println("输入的不是小数！");
        }
        scan.close();
    }
}
/*
输出结果为：
$ javac ScannerDemo.java
$ java ScannerDemo
输入整数：12
整数数据：12
输入小数：1.2
小数数据：1.2
*/
```

## 衡量一个功能代码的优劣

1. 正确性
2. 可读性
3. 健壮性
4. 高效率与低存储：**时间复杂度**、空间复杂度（衡量算法的好坏）

## 数组

1. 数组是多个相同类型数据按一定顺序排列的集合，并使用一个名字命名，并通过编号的方式对这些数据进行统一的管理
2. 数组相关的概念：
   1. 数组名
   2. 元素
   3. 角标、下标、索引
   4. 数组的长度：元素个数
3. 数组的特点：
   1. 数组是序排序的
   2. 数组属于引用数据类型的变量。数组的元素，既可以是基本数据类型，也可以是引用数据类型
   3. 创建数组对象会在内存中开辟一整块连续的空间
   4. 数组的长度一旦确定，就不能修改
4. 数组的分类：
   1. 按照维数：一维数组、二维数组、、、、、、
   2. 按照数组元素的类型：基本数据类型元素的数组、引用数据元素的数组

* 写出一维数组初始化的两种方式

  ```java
  int[] arr = new int[5]; //动态初始化
  String[] arr1 = new String[]{"Tom","Jerry","Jim"};//静态初始化
  数组一初始化，其长度就是确定的。arr.length
  数组长度一旦确定，就不可以修改
  ```
  
* 写出二维数组初始化的两种方式

```java
int[][] arr = new int[4][3];//动态初始化1
int[][] arr1 = new int[4][];//动态初始化2

int[][] arr2 = new int[][]{{1,2},{3,4,5}};
```

* 如何遍历如下数组

```java
int[] arr  = new int [][]{{1,2,3},{4,5},{6,7,8}};
for(int i = 0;i < arr.length;i++){
  for(int j = 0;j < arr[i].length;j++){
    System.out.print(arr[i][j] + "\t");
  }
  System.out.println();
}
```

* 不同类型的一维数组的默认初始化值各是多少

```java
整型: 0
浮点型：0.0
char：0
boolean:false
引用类型：null
```

* 一维数组的内存解析

```java
String[] strs = new String[5];
strs[2] = "Tom";
strs = new String[3];
```

String[] strs = new String[5];

![image-20200216234054034](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200216234054034.png)

strs[2] = "Tom";

![image-20200216234155075](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200216234155075.png)

strs = new String[3];

![image-20200216234427490](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200216234427490.png)

sysout[strs[2]];//null

sysout[strs[4]];//报错

真实情况下，String中的数据放在常量池中，数组都是地址值

![image-20200216234738387](/Users/yangshucheng/Library/Application Support/typora-user-images/image-20200216234738387.png)

### 一维数组的声明和初始化

```java
    //1. 一维数组的声明和初始化
		int num;//声明
		num = 10;//初始化
		int id = 1001;//声明 + 初始化
		
		int[] ids;//声明
		//1.1 静态初始化:数组的初始化和数组元素的赋值操作同时进行
		ids = new int[]{1001,1002,1003,1004};
		//1.2动态初始化:数组的初始化和数组元素的赋值操作分开进行
		String[] names = new String[5];

    //也是正确的写法：
		int[] arr4 = {1,2,3,4,5};//类型推断
		
		//总结：数组一旦初始化完成，其长度就确定了。
```

### 如何调用数组的指定位置的元素

通过角标的方式调用。

数组的角标（或索引）从0开始的，到数组的长度-1结束。

### 如何获取数组的长度。

属性:length

```java
System.out.println(names.length);
System.out.println(ids.length);
```

### 如何遍历数组

```java
for(int i = 0;i < names.length;i++){
			System.out.println(names[i]);
		}
```

### 数组元素的默认初始化值

* 数组元素是整型：0

* 数组元素是浮点型：0.0

* 数组元素是char型：0或'\u0000'，而非'0'

* 数组元素是boolean型：false

*  数组元素是引用数据类型：null

## 二维数组的使用

#### 理解

* 对于二维数组的理解，我们可以看成是一维数组array1又作为另一个一维数组array2的元素而存在。其实，从数组底层的运行机制来看，其实没有多维数组

#### 使用:

 \*  ① 二维数组的声明和初始化

```java
		//二维数组的声明和初始化
		int[] arr = new int[]{1,2,3};//一维数组
		//静态初始化
		int[][] arr1 = new int[][]{{1,2,3},{4,5},{6,7,8}};
		//动态初始化1
		String[][] arr2 = new String[3][2];
		//动态初始化2
		String[][] arr3 = new String[3][];
		//也是正确的写法：
		int[] arr4[] = new int[][]{{1,2,3},{4,5,9,10},{6,7,8}};
		int[] arr5[] = {{1,2,3},{4,5},{6,7,8}};
```



 \*  ② 如何调用数组的指定位置的元素

```java
		System.out.println(arr1[0][1]);//2
		System.out.println(arr2[1][1]);//null
		
		arr3[1] = new String[4];
		System.out.println(arr3[1][0]);
```



 \*  ③ 如何获取数组的长度

```java
		System.out.println(arr4.length);//3
		System.out.println(arr4[0].length);//3
		System.out.println(arr4[1].length);//4
```

 \*  ④ 如何遍历数组

```java
		for(int i = 0;i < arr4.length;i++){
			
			for(int j = 0;j < arr4[i].length;j++){
				System.out.print(arr4[i][j] + "  ");
			}
			System.out.println();
		}
```



 \*  ⑤ 数组元素的默认初始化值 

```java
规定：二维数组分为外层数组的元素，内层数组的元素
 * 		int[][] arr = new int[4][3];
 * 		外层元素：arr[0],arr[1]等
 * 		内层元素：arr[0][0],arr[1][2]等
 * 
 *   ⑤ 数组元素的默认初始化值 
 *   针对于初始化方式一：比如：int[][] arr = new int[4][3];
 *      外层元素的初始化值为：地址值
 *      内层元素的初始化值为：与一维数组初始化情况相同
 *      
 *   针对于初始化方式二：比如：int[][] arr = new int[4][];
 *   	外层元素的初始化值为：null
 *      内层元素的初始化值为：不能调用，否则报错。
```



 \*  ⑥ 数组的内存解析 

```java
		System.out.println("*****************");
		double[][] arr3 = new double[4][];
		System.out.println(arr3[1]);//null
//		System.out.println(arr3[1][0]);//报错
```

