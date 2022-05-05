# C++面试辅导课程笔记

## 预处理与宏

### 预处理

```cpp
...
#define DEBUG
    ... 
#ifdef DEBUG//判断DEBUG是否被定义
    ...
#endif
    ...
```

### 宏定义的使用

考点：使用#define宏定义需要注意的地方

```cpp
#define SQR(x) (x * x)
int a,b = 3;
a = SQR(b + 2);//原本： a = (b + 2) * (b + 2)   #define SQR(x) (x * x)
// 实际上 ：  a = b + 2 * b + 2
//解决方法：#define SQR(x) ((x) * (x)
```

## 动态分配内存

### 使用new动态分配内存，使用delete释放动态申请的内存

类型名 *指针变量 = new 类型名

eg: int *pNum = new int;

类型名 *指针变量 = new 类型名[元素个数]

int i = 5;

int *p = new int[i];

避免野指针：delete后指针指向NULL

### 使用malloc和free动态分配内存

void* malloc(unsigned int size);

void free(void *p);

eg:

short *p = (short\*)malloc(len \* sizeof(short));

free(p);

## String类具体实现

```cpp
class String{
    public:
    	String(const char *str = NULL);//通用构造函数
    	String(const String &another);//复制构造函数
    	~String();//析构函数
    	String & operator = (const String &rhs);//赋值函数
    	char *m_data;//用于保存字符串
};

//需要注意：1、判断参数str是否为NULL；2、赋值前需要给成员变量m_data申请内存
String::String(const char *str){
    if(str == NULL){
        m_data = new char[1];
        m_data[0] = '\0';
    }else{
        m_data = new char[strlen(str) + 1];
        strcpy(m_data,str);
    }
}


//1、参数another的成员变量m_data赋值给另一个m_data
String::String(const String &another){
    m_data = new char[strlen(another.m_data) + 1];
    strcpy(m_data,another.m_data);
}



String &String::operator = (const String &rhs){//赋值函数
    //String A;
    //String B = A
    if(this == &rhs){
        return *this;
    }
    //删除原来的数据
    delete []m_data;
    //新开一块内存
    m_data = new char[strlen(rhs.m_data) + 1];
    strcpy(m_data,rhs.m_data);
    return *this;
}


String::~String(){
    delete []m_data;
    m_data = NULL;
}

```

## 链表

```cpp
struct Node{
    int data;
    Node *next;
}
```

### 逆置链表

```cpp
Node *ReverseList(Node *head){
    if(head == NULL || head->next == NULL){
        return head;
    }
    Node *p1 = head;
    Node *p2 = p1->next;
    Node *p3 = p2->next;
    
    p1->next = NULL;//让链表头变为尾
    while(p3 != NULL){
        p2->next = p1;
        p1 = p2;
        p2 = p3;
        p3 = p3->next;
    }
    p2->next = p1;
    head = p2;//让链表尾变为头
    return head;
}
```

### 合并两个有序链表

```cpp
Node *Merge(Node *head1,Node *p2){
    if(head1 == NULL){
        return head2;
    }
    if(head2 == NULL){
        return head1;
    }
    Node *head = NULL;
    Node *p1 = NULL;
    Node *p2 = NULL;
    if(head1->data < head2->data){
        head = head1;
        p1 = head1->next;
        p2 = head2;
    }else{
        head = head2;
        p2 = head2->next;
        p1 = head1;
    }
    Node *pcurrent = head;
    while(p1 != NULL && p2 != NULL){
        if(p1->data <= p2->data){
			pcurrent->next = p1;
             pcurrent = p1;
             p1 = p1->next;
        }else{
            pcurrent->next = p2;
            pcurrent = p2;
            p2 = p2->next;
        }
    }
    if(p1 != NULL){
	    pucurrent->next = p1; 
    }
    if(p2 != NULL){
        pcurrent->next = p2;
    }
    return head;
}
```

## 字符串

逆序输出字符串

```cpp
void print(char *a){
    int i = 0;
    int j;
    char t;
    for(int i = 0,j = strlen(a) - 1;i < strlen(a) / 2;i++,j--){
    	t = a[i];
        a[i] = a[j];
        a[j] = t;
    }
    cout<<a<<endl;
}


int _tmain(int argc,_TCHAR* agev[]){
    char a[10];
    //初始化
    memset(a,0,sizeof(a));
    cin.getline(a,10,'\n');
    print(a);
    return 0; 
}
```

## 数组降序排列

```cpp
//冒泡排序
void sort(int *arr,int n){
    int temp;
    for(int i = 1;i < n;i++){
        for(int k = 0;k < n - i;k++){
            if(arr[k] < arr[k + 1]){
			 temp = arr[k];
              arr[k] = arr[k + 1];
              arr[k + 1] = arr[k];
            }
        }
    }
}
//快速排序
void QuickSort(vector<int>& arr, int begin, int end)
{
    if (begin >= end) return;
    int first = begin;
    int last = end;
    int key = arr[first];
    while (first < last)
    {
        while (first < last && key <= arr[last])
            last--;
        arr[first] = arr[last];
        while (first < last && key >= arr[first])
            first++;
        arr[last] = arr[first];
    }
    arr[first] = key;
    QuickSort(arr, first + 1, end);
    QuickSort(arr, begin, first - 1);
}
```

## 容器和迭代器的使用

### 序列式容器和关联式容器

vector,list,deque

```cpp
//创建一个double型的数组
double sz[5] = {1,2,3,4,5};
//创建deque型容器obd,用sz的首地址和（末地址 + 1）进行初始化
deque<double> obD(sz,sz + 5);
//对obD的元素进行随机访问
for(unsigned int i = 0;i < obD.sizae();++i){
    cout<<obD[i]<<" ";
}

//创建一个大小为3的List型容器obL，其中每个元素都初始化为5
list<float> obL(3,5);
//创建list<float>型迭代器，类似指针的概念
list<float>::iterator iter = obL.begin();
while(iter != obL.end()){
    cout << (*iter)<<" ";
    iter++;
}





```

## const成员函数

const成员函数的基本定义格式

1、类内定义时

类型 函数名（参数列表）const{

​	函数体

}

2、在类定义之外定义时，共分两步

类内声明

类型 函数名（参数列表）const;



类外定义



类型 类名::函数名（参数列表）const{

​	函数体

}

```cpp
class point{
    int x;
    int y;
public:
    point(int xp = 0,int yp = 0){
        x = xp;
        y = yp;
    }
    //const成员函数内无法修改数据成员，否则编译报错，不能调用其他非const函数
    void print() const{
        x = 5;//试图修改x，将引发编译器报错
    }
    
    
};
```



## static数据成员

static（静态存储）数据成员：编译时就会被创建和初始化



```cpp
class computer{
private:
    float price;
    static float total_price;//static数据成员 想编译器描述：如何为static数据成员分配内存 
public:
    computer(const float p){
        price = p;
        total_price += p;
    }
    ~computer(){
        total_price -= price;
    }
    void print(){
        cout <<"总价 ： "<<total_price<<endl;
    }  
};
//必须先把static的变量初始化，真正的内存分配
float computer::total_price = 0;
int main(){
    computer comp1(7000);
    comp1.print();
    computer comp2(4999);
    comp2.print();
    computer comp3(2999);
    comp3.print();
    comp2.~computer();
}



```

## 派生类的构造函数

派生类名（派生类构造函数参数表）：基类构造函数（基类构造函数参数表）{

​	函数体；

}；

1、完成对象所占整块内存的开辟，由系统在调用构造函数时自动完成

2、调用基类的构造函数完成基类成员的初始化

3、如果派生类中含有对象成员、const成员或引用成员，则必须在初始化表中完成其初始化

4、派生类构造函数体执行:先调用基类构造函数    派生类对象成员构造函数   派生类构造函数函数体

```cpp
class A{
private:
    int x;
public:
    A(int xp = 0){
        x = xp;
        cout <<"A的构造函数执行"<<endl;
    }
};
//类B的定义
class B{
public:
    B(){
        cout<<"B的构造函数被执行"<<endl;
    }
};
class C:public A{
private:
    int y;
    B b;
public:
    C(int xp,int yp):A(xp),b(){
        y = yp;
        cout<<"C的构造函数被执行"<endl;
    }
};
int mian(){
    
    C expC(1,2);
    //A -> B -> C
    return 0;
    
}
```









## 派生类的析构函数

构造函数、析构函数都不可被继承

执行顺序：先执行派生类的析构函数，再执行基类的析构函数



```cpp
class A{
private:
    int x;
public:
    A(int xp = 0){
        x = xp;
        cout<<"A的构造函数被执行"<<endl;
    }
    ~A(){
        cout<<"A的析构函数被执行"<<endl;
    }
};

//类B的定义
class B{
public:
    B(){
        cout<<"B的构造函数被执行"<<endl;
    }
    ~B(){
        cout<<"B的析构函数被执行"<<endl;
    }
};

class C:public A{
private:
    int y;
    B b;
public:
    C(int xp,int yp):A(xp),b(){
        y = yp;
        cout<<"C的构造函数被执行"<<endl;
    }
    ~C(){
        cout<<"C的析构函数被执行"<<endl;
    }
};

int mian(){
    
    C expC(1,2);
    //构造函数A -> B -> C
    //析构函数C -> B -> A
    return 0;
    
}
```



## 重载、覆盖与隐藏

### 重载

1.  相同的范围（在同一个类中）
2.  函数名相同
3.  参数不同
4.  virtual关键字可有可无

### 覆盖：指的是派生类的成员函数覆盖基类中的同名函数

要求：两个函数的参数个数和类型都相同，基类函数必须是虚函数

特征：

1.  不同的范围（分别位于派生类和基类）
2.  函数名字相同
3.  参数相同
4.  基类函数必须有virtual关键字

```cpp
class A{
    //重载关系的3个函数
    virtual int fun();
    void fun(int);
    void(double,double);
    
    
};
//覆盖
class A{
    virtual void fun1(int,int);
    virtual int fun2(char *);
};
class B:public A{
    
    void fun1(int,int);
    
}
class C:public B{
    
    int fun2(char *);
    
}
int main(){
    A *pA = new C;
    pA->fun1();
    pA->fun2();
    
}



```

## 隐藏

派生类中的函数与基类中的函数参数相同，但是基类函数不是虚函数

派生类中的函数与基类中的函数参数不同时，不管基类函数是否是虚函数，基类函数都会被屏蔽

特征：

1.  如果派生类的函数与基类的函数同名，但是参数不同。此时，不论有无virtual关键字，基类函数都将被隐藏
2.  派生类中的函数与基类中的函数参数相同时，但是基类函数不是虚函数（没有virtual关键字）。基类函数将被隐藏

```cpp
//隐藏
class A{
public:
    void fun(int xp){
        cout << xp << endl;
    }
};
class B:public A{
public:
    void fun(char *s){
        cout << s << endl; 
    }
    void fun(int xp){
        A::fun(xp);//主函数中调用obB.fun(2);成功
    }
}
int main(){
    B obB;
    obB.fun("hello");
    obB.fun(2);//错误，基类函数被屏蔽了
    
}
```



## 虚函数

```cpp
//基类base定义
class base{
public:
    void disp(){
        cout <<"Hello,base"<<endl;
    }
};
class child1:public base{
public:
    void disp(){//派生类child1中定义的disp()函数将base中的disp()屏蔽了
        cout<<"hello,child1"<<endl;
    }
};
class child1:public base{
public:
    void disp(){
        cout<<"hello,child2"<<endl;
    }
};
void display(base *pb){
    pb->disp();
}
int main(){
    base *pBase = NULL,obj_base;
    obj_base.disp();//Hello,base
    pBase = &obj_base;
    pBase->disp();//Hello,base
    
    child *pchild1 = NULL,obj_child1;
    obj_child1.disp();//Hello,child1
    pchild1 = &obj_child1;
    pchild1->disp();//Hello,child1
    
    child *pchild2 = NULL,obj_child2;
    obj_child2.disp();//Hello,child2
    pchild2 = &obj_child1;
    pchild2->disp();//Hello,child2
    
    //使用obj_child1的地址为pBase赋值
    pBase = &obj_child1;
    pBase->disp();//Hello,base
    
    display(&obj_base);//Hello,base
    display(&obj_child1);//Hello,base
    display(&obj_child2);//Hello,base
    
    return 0;
}


```



基类加了virtual后：

```cpp
//基类base定义
class base{
public:
    virtual void disp(){
        cout <<"Hello,base"<<endl;
    }
};
class child1:public base{
public:
    void disp(){//派生类child1中定义的disp()函数将base中的disp()屏蔽了
        cout<<"hello,child1"<<endl;
    }
};
class child1:public base{
public:
    void disp(){
        cout<<"hello,child2"<<endl;
    }
};
void display(base *pb){
    pb->disp();
}
int main(){
    base *pBase = NULL,obj_base;
    obj_base.disp();//Hello,base
    pBase = &obj_base;
    pBase->disp();//Hello,base
    
    child *pchild1 = NULL,obj_child1;
    obj_child1.disp();//Hello,child1
    pchild1 = &obj_child1;
    pchild1->disp();//Hello,child1
    
    child *pchild2 = NULL,obj_child2;
    obj_child2.disp();//Hello,child2
    pchild2 = &obj_child1;
    pchild2->disp();//Hello,child2
    
    //使用obj_child1的地址为pBase赋值
    pBase = &obj_child1;
    pBase->disp();//Hello,child1
    
    display(&obj_base);//Hello,base
    display(&obj_child1);//Hello,child1
    display(&obj_child2);//Hello,child2
    
    return 0;
}



```



## 结构体和共用体sizeof

1、结构体变量的sizeof

```cpp
struct ExS1{
    char c1;//char的偏移量必须是1的倍数
    short s1;//short的偏移量必须是2的倍数
    int i1;//int型必须是4的倍数
};

sizeof(ExS1);//8 = 2 + 2 + 4字节对齐
/*
1. 结构体变量的首地址能够被其最大宽度基本类型成员的大小所整除
2. 结构体每个成员相对于结构体首地址的偏移量都是成员大小的整数倍，
如果有需要，编译器会在成员之间加上填充字节
3. 结构体的总大小为结构体最宽基本类型成员大小的整数倍


*/
```

2、 共用体的sizeof，看最宽的类型所占字节

```cpp
union Ex{
    double x;
    char y[13];  
};

sizeof(Ex);//char y 字节为 8   char[13]时为 16
```

## C++如何使用内存

三种管理内存的方式：

自动存储

静态存储

动态存储

### 自动存储（栈存储）

函数的形参、函数内部声明的变量及结构体变量

```cpp
int add(int m,int n){
    //z的生命周期包括整个函数
    int z = m + n;
    return z;
}
int add(int m,int n){
    //z的生命周期包括在这个代码块中
    if(m != 0){
        int z = m + n;
    }
    
    return z;//错误，未定义z
}
```

### 静态存储（编译器预分配）：永久存储

关键字：

1.  extern关键字：全局变量或外部变量（定义性声明和引用性声明）

    1.  定义性声明：

        extern 类型 变量名 = 初始化表达式；

        eg: extern double total =10；

2.  引用性声明

    1.  extern 类型 变量名;



```cpp
int main(){
    //引用性声明
    extern int num1;
    cout <<"num1: " <<num1 <<endl;
    //函数声明
    void change();
    //函数使用
    change();
    cout <<"num1: " <<num1 <<endl;
}


int num1;
int change(){
    num1 += 3; 
}
```





## 函数参数的值传递、指针传递和引用传递

```cpp
int main(){
    //值传递
    //函数声明
    void change(int,int);
    int x = 2,y = 3;
    cout<<"交换前：x = "<<x<<",y = "<<y<<endl;
    change(x,y);//值传递
    cout<<"交换后：x = "<<x<<",y = "<<y<<endl;
    return 0;
}


int main(){
    //指针传递
    //函数声明
    void change(int*,int*);
    int x = 2,y = 3;
    cout<<"交换前：x = "<<x<<",y = "<<y<<endl;
    change(&x,&y);//值传递
    cout<<"交换后：x = "<<x<<",y = "<<y<<endl;
    return 0;
}
void change(int *n,int *m){
    int temp;
    temp = *n;
    *n = *m;
    *m = temp;
}



int main(){
    //引用传递
    //函数声明
    void change(int&,int&);
    int x = 2,y = 3;
    cout<<"交换前：x = "<<x<<",y = "<<y<<endl;
    change(x,y);//值传递
    cout<<"交换后：x = "<<x<<",y = "<<y<<endl;
    return 0;
}
void change(int &n,int &m){
    int temp;
    temp = n;
    n = m;
    m = temp;
}





```



## 函数模板的使用

1.  隐式实例化
2.  显式实例化

```cpp
//函数模板的声明
template<class Ex>
Ex Great(Ex x,Ex y);
int main(){
    int intX = 1,intY = 2;
    double dblX = 3.0,dblY = 2.9;
    //实参为int型，生成int型模板函数，并对第二个参数进行检查
    cout<<Greater(intX,intY)<<endl;
     cout<<Greater(dblX,dblY)<<endl;
    return 0;
}
template<class Ex>
Ex Great(Ex x,Ex y){
    return x > y ? x : y;
}
    
```

显示实例化

```cpp
//函数模板的声明
template<class Ex>
Ex Great(Ex x,Ex y);
//显示实例化Greater函数模板
template int Greater<int> (int,int)
int main(){
    int intX = 1,intY = 2;
    double dblX = 3.0,dblY = 2.9;
    //实参为int型，生成int型模板函数，并对第二个参数进行检查
    cout<<Greater(intX,intY)<<endl;//显示实例化
     cout<<Greater(dblX,dblY)<<endl;
    return 0;
}
template<class Ex>
Ex Great(Ex x,Ex y){
    return x > y ? x : y;
}
    
```



## 类模板



```cpp
//类型参数表
template <class T,int num>
class Stack{
private:
    T sz[num];
    int point;
public:
    Stack();
    bool isEmpty();//判断栈是否为空
    bool push(const T&);
}
```



















































































