# Java常用数据结构与函数

## StringBuffer和 StringBuilder 类

StringBuffer ans = new StringBuffer();

当对字符串进行修改的时候，需要使用 StringBuffer 和 StringBuilder 类。

和 String 类不同的是，StringBuffer 和 StringBuilder 类的对象能够被多次的修改，并且不产生新的未使用对象。

StringBuilder 类在 Java 5 中被提出，它和 StringBuffer 之间的最大不同在于 StringBuilder 的方法不是线程安全的（不能同步访问）。

由于 StringBuilder 相较于 StringBuffer 有速度优势，所以多数情况下建议使用 StringBuilder 类。然而在应用程序要求线程安全的情况下，则必须使用 StringBuffer 类。

```java
public class Test{
  public static void main(String args[]){
    StringBuffer sBuffer = new StringBuffer("菜鸟教程官网：");
    sBuffer.append("www");
    sBuffer.append(".runoob");
    sBuffer.append(".com");
    System.out.println(sBuffer);  
  }
}
```

>   ```
>   菜鸟教程官网：www.runoob.com
>   ```

### ans.append()

添加字符串

### ans.reverse()

翻转字符串

## StringBuffer 方法

以下是 StringBuffer 类支持的主要方法：

| 序号                                    | 方法描述                                                 |
| --------------------------------------- | -------------------------------------------------------- |
| public StringBuffer append(String s)    | 将指定的字符串追加到此字符序列。                         |
| public StringBuffer reverse()           | 将此字符序列用其反转形式取代。                           |
| public delete(int start, int end)       | 移除此序列的子字符串中的字符。                           |
| public insert(int offset, int i)        | 将 `int` 参数的字符串表示形式插入此序列中。              |
| replace(int start, int end, String str) | 使用给定 `String` 中的字符替换此序列的子字符串中的字符。 |

下面的列表里的方法和 String 类的方法类似：

| 序号                                                         | 方法描述                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| int capacity()                                               | 返回当前容量。                                               |
| char charAt(int index)                                       | 返回此序列中指定索引处的 `char` 值。                         |
| void ensureCapacity(int minimumCapacity)                     | 确保容量至少等于指定的最小值。                               |
| void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin) | 将字符从此序列复制到目标字符数组 `dst`。                     |
| int indexOf(String str)                                      | 返回第一次出现的指定子字符串在该字符串中的索引。             |
| int indexOf(String str, int fromIndex)                       | 从指定的索引处开始，返回第一次出现的指定子字符串在该字符串中的索引。 |
| int lastIndexOf(String str)                                  | 返回最右边出现的指定子字符串在此字符串中的索引。             |
| int lastIndexOf(String str, int fromIndex)                   | 返回 String 对象中子字符串最后出现的位置。                   |
| int length()                                                 | 返回长度（字符数）。                                         |
| void setCharAt(int index, char ch)                           | 将给定索引处的字符设置为 `ch`。                              |
| void setLength(int newLength)                                | 设置字符序列的长度。                                         |
| CharSequence subSequence(int start, int end)                 | 返回一个新的字符序列，该字符序列是此序列的子序列。           |
| String substring(int start)                                  | 返回一个新的 `String`，它包含此字符序列当前所包含的字符子序列。 |
| String substring(int start, int end)                         | 返回一个新的 `String`，它包含此序列当前所包含的字符子序列。  |
| String toString()                                            | 返回此序列中数据的字符串表示形式。                           |

## String

**注意:**String 类是不可改变的，所以你一旦创建了 String 对象，那它的值就无法改变了

如果需要对字符串做很多修改，那么应该选择使用 [StringBuffer & StringBuilder 类](https://www.runoob.com/java/java-stringbuffer.html)。

### length()

用于获取有关对象的信息的方法称为访问器方法。

String 类的一个访问器方法是 length() 方法，它返回字符串对象包含的字符数

```java
public class StringDemo {
    public static void main(String args[]) {
        String site = "www.runoob.com";
        int len = site.length();
        System.out.println( "菜鸟教程网址长度 : " + len );
   }
}

```

### 连接字符串

String 类提供了连接两个字符串的方法：

string1**.concat**(string2);

返回 string2 连接 string1 的新字符串。也可以对字符串常量使用 concat() 方法，如：

```java
"我的名字是 ".concat("Runoob");
```

更常用的是使用**'+'操作符**来连接字符串，如：

```java
"Hello," + " runoob" + "!"
```

结果如下:

```java
"Hello, runoob!"
```

### 创建格式化字符串

我们知道输出格式化数字可以使用 printf() 和 format() 方法。

String 类使用静态方法 format() 返回一个String 对象而不是 PrintStream 对象。

String 类的静态方法 format() 能用来创建可复用的格式化字符串，而不仅仅是用于一次打印输出。

如下所示：

```java
System.out.printf("浮点型变量的值为 " +
                  "%f, 整型变量的值为 " +
                  " %d, 字符串变量的值为 " +
                  "is %s", floatVar, intVar, stringVar);
```

你也可以这样写

```java
String fs;
fs = String.format("浮点型变量的值为 " +
                   "%f, 整型变量的值为 " +
                   " %d, 字符串变量的值为 " +
                   " %s", floatVar, intVar, stringVar);
```



### num1.charAt(字符串索引)

##  LinkedList

链表（Linked list）是一种常见的基础数据结构，是一种线性表，但是并不会按线性的顺序存储数据，而是在每一个节点里存到下一个节点的地址。

Java LinkedList（链表） 类似于 ArrayList，是一种常用的数据容器。

与 ArrayList 相比，LinkedList 的增加和删除对操作效率更高，而查找和修改的操作效率较低。

**以下情况使用 ArrayList :**

-   频繁访问列表中的某一个元素。
-   只需要在列表末尾进行添加和删除元素操作。

**以下情况使用 LinkedList :**

-   你需要通过循环迭代来访问列表中的某些元素。
-   需要频繁的在列表开头、中间、末尾等位置进行添加和删除元素操作。

LinkedList 继承了 AbstractSequentialList 类。

LinkedList 实现了 Queue 接口，可作为队列使用。

LinkedList 实现了 List 接口，可进行列表的相关操作。

LinkedList 实现了 Deque 接口，可作为队列使用。

LinkedList 实现了 Cloneable 接口，可实现克隆。

LinkedList 实现了 java.io.Serializable 接口，即可支持序列化，能通过序列化去传输。

![LinkedList关系结构图](https://gitee.com/yangshucheng2020/blogimage/raw/master/uPic/20190328164737.png)

LinkedList 类位于 java.util 包中，使用前需要引入它，语法格式如下：

```java
// 引入 LinkedList 类
import java.util.LinkedList; 
LinkedList<E> list = new LinkedList<E>();   
// 普通创建方法     或者
LinkedList<E> list = new LinkedList(Collection<? extends E> c); 
// 使用集合创建链表
```

LinkedList常用方法

```java
LinkedList<String> sites = new LinkedList<String>();
sites.add("Google");//尾部添加元素
sites.add("Runoob");
sites.add("Taobao");
// 使用 addFirst() 在头部添加元素
sites.addFirst("Wiki");
// 使用 addLast() 在尾部添加元素
sites.addLast("Wiki");
// 使用 removeFirst() 移除头部元素
sites.removeFirst();
// 使用 removeLast() 移除尾部元素
sites.removeLast();
// 使用 getFirst() 获取头部元素
System.out.println(sites.getFirst());
// 使用 getLast() 获取尾部元素
System.out.println(sites.getLast());
//可以使用 for 配合 size() 方法来迭代列表中的元素：
for (int size = sites.size(), i = 0; i < size; i++) {
     System.out.println(sites.get(i));//get(i)获取第i+1个元素
}
//可以使用 for-each 来迭代元素：
for (String i : sites) {
     System.out.println(i);
}
```

### 常用方法

| 方法                                           | 描述                                                         |
| ---------------------------------------------- | ------------------------------------------------------------ |
| public boolean add(E e)                        | 链表末尾添加元素，返回是否成功，成功为 true，失败为 false。  |
| public void add(int index, E element)          | 向指定位置插入元素。                                         |
| public boolean addAll(Collection c)            | 将一个集合的所有元素添加到链表后面，返回是否成功，成功为 true，失败为 false。 |
| public boolean addAll(int index, Collection c) | 将一个集合的所有元素添加到链表的指定位置后面，返回是否成功，成功为 true，失败为 false。 |
| public void addFirst(E e)                      | 元素添加到头部。                                             |
| public void addLast(E e)                       | 元素添加到尾部。                                             |
| public boolean offer(E e)                      | 向链表末尾添加元素，返回是否成功，成功为 true，失败为 false。 |
| public boolean offerFirst(E e)                 | 头部插入元素，返回是否成功，成功为 true，失败为 false。      |
| public boolean offerLast(E e)                  | 尾部插入元素，返回是否成功，成功为 true，失败为 false。      |
| public void clear()                            | 清空链表。                                                   |
| public E removeFirst()                         | 删除并返回第一个元素。                                       |
| public E removeLast()                          | 删除并返回最后一个元素。                                     |
| public boolean remove(Object o)                | 删除某一元素，返回是否成功，成功为 true，失败为 false。      |
| public E remove(int index)                     | 删除指定位置的元素。                                         |
| public E poll()                                | 删除并返回第一个元素。                                       |
| public E remove()                              | 删除并返回第一个元素。                                       |
| public boolean contains(Object o)              | 判断是否含有某一元素。                                       |
| public E get(int index)                        | 返回指定位置的元素。                                         |
| public E getFirst()                            | 返回第一个元素。                                             |
| public E getLast()                             | 返回最后一个元素。                                           |
| public int indexOf(Object o)                   | 查找指定元素从前往后第一次出现的索引。                       |
| public int lastIndexOf(Object o)               | 查找指定元素最后一次出现的索引。                             |
| public E peek()                                | 返回第一个元素。                                             |
| public E element()                             | 返回第一个元素。                                             |
| public E peekFirst()                           | 返回头部元素。                                               |
| public E peekLast()                            | 返回尾部元素。                                               |
| public E set(int index, E element)             | 设置指定位置的元素。                                         |
| public Object clone()                          | 克隆该列表。                                                 |
| public Iterator descendingIterator()           | 返回倒序迭代器。                                             |
| public int size()                              | 返回链表元素个数。                                           |
| public ListIterator listIterator(int index)    | 返回从指定位置开始到末尾的迭代器。                           |
| public Object[] toArray()                      | 返回一个由链表元素组成的数组。                               |
| public  T[] toArray(T[] a)                     | 返回一个由链表元素转换类型而成的数组。                       |

## HashMap

HashMap 是一个散列表，它存储的内容是键值对(key-value)映射。

HashMap 实现了 Map 接口，根据键的 HashCode 值存储数据，具有很快的访问速度，最多允许一条记录的键为 null，不支持线程同步。

HashMap 是无序的，即不会记录插入的顺序。

HashMap 继承于AbstractMap，实现了 Map、Cloneable、java.io.Serializable 接口。

HashMap<Node,Node> hash = new HashMap<>();

![HashMap关系图](https://gitee.com/yangshucheng2020/blogimage/raw/master/uPic/WV9wXLl.png)

HashMap 的 key 与 value 类型可以相同也可以不同，可以是字符串（String）类型的 key 和 value，也可以是整型（Integer）的 key 和字符串（String）类型的 value。

![Map内部结构图](https://gitee.com/yangshucheng2020/blogimage/raw/master/uPic/java-initialize-hashmap.png)

HashMap 中的元素实际上是对象，一些常见的基本类型可以使用它的包装类。

基本类型对应的包装类表如下：

| 基本类型 | 引用类型  |
| -------- | --------- |
| boolean  | Boolean   |
| byte     | Byte      |
| short    | Short     |
| int      | Integer   |
| long     | Long      |
| float    | Float     |
| double   | Double    |
| char     | Character |

HashMap 类位于 java.util 包中，使用前需要引入它，语法格式如下：

```java
import java.util.HashMap; // 引入 HashMap 类
```

以下实例我们创建一个 HashMap 对象 Sites， 整型（Integer）的 key 和字符串（String）类型的 value：

```java
HashMap<Integer, String> Sites = new HashMap<Integer, String>();
```

```java
// 引入 HashMap 类      
import java.util.HashMap;

public class RunoobTest {
    public static void main(String[] args) {
        // 创建 HashMap 对象 Sites
        HashMap<Integer, String> Sites = new HashMap<Integer, String>();
        //HashMap 类提供类很多有用的方法，添加键值对(key-value)可以使用 put()方法:
        // 添加键值对
        Sites.put(1, "Google");
        Sites.put(2, "Runoob");
        Sites.put(3, "Taobao");
        Sites.put(4, "Zhihu");
        System.out.println(Sites);
/***************************************************************************/
        /*访问元素
	    我们可以使用 get(key) 方法来获取 key 对应的 value:
        */
        // 创建 HashMap 对象 Sites
        HashMap<Integer, String> Sites = new HashMap<Integer, String>();
        // 添加键值对
        Sites.put(1, "Google");
        Sites.put(2, "Runoob");
        Sites.put(3, "Taobao");
        Sites.put(4, "Zhihu");
        System.out.println(Sites.get(3));
/**************************************************************************/        
        /*删除元素
	    我们可以使用 remove(key) 方法来删除 key 对应的键值对(key-value):
        */
        // 创建 HashMap 对象 Sites
        HashMap<Integer, String> Sites = new HashMap<Integer, String>();
        // 添加键值对
        Sites.put(1, "Google");
        Sites.put(2, "Runoob");
        Sites.put(3, "Taobao");
        Sites.put(4, "Zhihu");
        Sites.remove(4);
        System.out.println(Sites);
//删除所有键值对(key-value)可以使用 clear 方法：
        Sites.clear();
// 如果要计算 HashMap 中的元素数量可以使用 size() 方法：
        System.out.println(Sites.size());
 		/*迭代 HashMap
 		可以使用 for-each 来迭代 HashMap 中的元素。
 		如果只想获取 key，可以使用 keySet() 方法，
 		如果只想获取 value，可以使用 values() 方法。
		*/       
        for (Integer i : Sites.keySet()) {
            System.out.println("key: " + i + " value: " + Sites.get(i));    
        }
  }
}
```

### hash.containsKey(node)

### hash.put(node,cloneNode);

##  Deque

Deque接口是“double ended queue”的缩写(通常读作“deck”)，即双端队列，支持在队列的两端插入和删除元素，继承Queue接口。大多数的实现对元素的数量没有限制，但这个接口既支持有容量限制的deque，也支持没有固定大小限制的。

Deque堆栈操作方法：push()、pop()、peek()。

提供插入、移除和检查元素的方法。每种方法都存在两种形式：一种形式在操作失败时抛出异常，另一种形式返回一个特殊值（null 或 false，具体取决于操作）。插入操作的后一种形式是专为使用有容量限制的 Deque 实现设计的；在大多数实现中，插入操作不能失败。

下表总结了上述 12 种方法：

|          | **第一个元素 (头部)** | **最后一个元素 (尾部)** |              |              |
| -------- | --------------------- | ----------------------- | ------------ | ------------ |
|          | *抛出异常*            | *特殊值*                | *抛出异常*   | *特殊值*     |
| **插入** | addFirst(e)           | offerFirst(e)           | addLast(e)   | offerLast(e) |
| **删除** | removeFirst()         | pollFirst()             | removeLast() | pollLast()   |
| **检查** | getFirst()            | peekFirst()             | getLast()    | peekLast()   |

Deque接口扩展了 Queue 接口。在将双端队列用作队列时，将得到 FIFO（先进先出）行为。将元素添加到双端队列的末尾，从双端队列的开头移除元素。从 Queue 接口继承的方法完全等效于 Deque 方法，如下表所示：

| **Queue方法** | **等效Deque方法** |
| ------------- | ----------------- |
| add(e)        | addLast(e)        |
| offer(e)      | offerLast(e)      |
| remove()      | removeFirst()     |
| poll()        | pollFirst()       |
| element()     | getFirst()        |
| peek()        | peekFirst()       |

双端队列也可用作 LIFO（后进先出）堆栈。应优先使用此接口而不是遗留 Stack 类。在将双端队列用作堆栈时，元素被推入双端队列的开头并从双端队列开头弹出。堆栈方法完全等效于 Deque 方法，如下表所示：


| **堆栈方法** | **等效Deque方法**                       |
| ------------ | --------------------------------------- |
| push(e)      | addFirst(e)【抛出异常】栈中加入一个元素 |
| pop()        | removeFirst()【抛出异常】弹出栈顶元素   |
| peek()       | peekFirst()【特殊值】取出栈顶元素       |

总结：

| Deque方法     | 作用             |
| ------------- | ---------------- |
| addFirst(e)   | 队首前面添加元素 |
| removeFirst() | 删除队首元素     |
| peekFirst()   | 取队首元素       |
| addLast()     | 队尾后面添加元素 |
| removeLast()  | 删除队尾元素     |

==Deque==<Character> stack = ==**new LinkedList**==<Character>();

## Map

Map 接口中键和值一一映射. 可以通过键来获取值。

-   给定一个键和一个值，你可以将该值存储在一个 Map 对象。之后，你可以通过键来访问对应的值。
-   当访问的值不存在的时候，方法就会抛出一个 NoSuchElementException 异常。
-   当对象的类型和 Map 里元素类型不兼容的时候，就会抛出一个 ClassCastException 异常。
-   当在不允许使用 Null 对象的 Map 中使用 Null 对象，会抛出一个 NullPointerException 异常。
-   当尝试修改一个只读的 Map 时，会抛出一个 UnsupportedOperationException 异常。

| 方法名                              | 方法描述                                                     |
| ----------------------------------- | ------------------------------------------------------------ |
| void clear( )                       | 从此映射中移除所有映射关系（可选操作）。                     |
| boolean contain**s**Key(Object k)   | 如果此映射包含指定键的映射关系，则返回 true。                |
| boolean contain**s**Value(Object v) | 如果此映射将一个或多个键映射到指定值，则返回 true。          |
| Set entrySet( )                     | 返回此映射中包含的映射关系的 Set 视图。                      |
| boolean equals(Object obj)          | 比较指定的对象与此映射是否相等。                             |
| Object get(Object k)                | 返回指定键所映射的值；如果此映射不包含该键的映射关系，则返回 null。 |
| int hashCode( )                     | 返回此映射的哈希码值。                                       |
| boolean isEmpty( )                  | 如果此映射未包含键-值映射关系，则返回 true。                 |
| Set keySet( )                       | 返回此映射中包含的键的 Set 视图。                            |
| Object put(Object k, Object v)      | 将指定的值与此映射中的指定键关联（可选操作）。               |
| void putAll(Map m)                  | 从指定映射中将所有映射关系复制到此映射中（可选操作）。       |
| Object remove(Object k)             | 如果存在一个键的映射关系，则将其从此映射中移除（可选操作）。 |
| int size( )                         | 返回此映射中的键-值映射关系数。                              |
| Collection values( )                | 返回此映射中包含的值的 Collection 视图。                     |

```java
Map<Character,Character> pairs = new HashMap<Character,Character>(){
            {
                put(')','(');
                put('}','{');
                put(']','[');
            }
        };
```



## Java Character 类

Character 类用于对单个字符进行操作。

Character 类在对象中包装一个基本类型 **char** 的值

### 实例

```java
char ch = 'a';  
// Unicode 字符表示形式 char uniChar = '\u039A';  
// 字符数组 
char[] charArray ={ 'a', 'b', 'c', 'd', 'e' };
```

然而，在实际开发过程中，我们经常会遇到需要使用对象，而不是内置数据类型的情况。为了解决这个问题，Java语言为内置数据类型char提供了包装类Character类。

Character类提供了一系列方法来操纵字符。你可以使用Character的构造方法创建一个Character类对象，例如：

```java
Character ch = new Character('a');
```

在某些情况下，Java编译器会自动创建一个Character对象。

例如，将一个char类型的参数传递给需要一个Character类型参数的方法时，那么编译器会自动地将char类型参数转换为Character对象。 这种特征称为装箱，反过来称为拆箱。

### 实例

```java
// 原始字符 'a' 装箱到 Character 对象 ch 中
Character ch = 'a';
 
// 原始字符 'x' 用 test 方法装箱
// 返回拆箱的值到 'c'
char c = test('x');
```



------

### 转义序列

前面有反斜杠（\）的字符代表转义字符，它对编译器来说是有特殊含义的。

下面列表展示了Java的转义序列：

| 转义序列 | 描述                     |
| -------- | ------------------------ |
| \t       | 在文中该处插入一个tab键  |
| \b       | 在文中该处插入一个后退键 |
| \n       | 在文中该处换行           |
| \r       | 在文中该处插入回车       |
| \f       | 在文中该处插入换页符     |
| \'       | 在文中该处插入单引号     |
| \"       | 在文中该处插入双引号     |
| \\       | 在文中该处插入反斜杠     |

#### 实例

当打印语句遇到一个转义序列时，编译器可以正确地对其进行解释。

以下实例转义双引号并输出：

```java
public class Test {    
    public static void main(String args[]) {      
        System.out.println("访问\"菜鸟教程!\"");   
    } 
}
```

以上实例编译运行结果如下：

```
访问"菜鸟教程!"
```

------

### Character 方法

下面是Character类的方法：

| 序号               | 方法与描述                              |
| ------------------ | --------------------------------------- |
| isLetter()         | 是否是一个字母                          |
| isDigit()          | 是否是一个数字字符                      |