# Cplusplus_OO
Lecture Notes for Learning the Julia language

<p align="center">
    <a href="https://github.com/elegantcoin/Cplusplus_OO"><img src="https://img.shields.io/badge/status-updating-brightgreen.svg"></a>
    <a href="https://github.com/python/cpython"><img src="https://img.shields.io/badge/Python-3.7-FF1493.svg"></a>
    <a href="https://github.com/elegantcoin/Cplusplus_OO"><img src="https://img.shields.io/badge/platform-Windows%7CLinux%7CmacOS-660066.svg"></a>
    <a href="https://opensource.org/licenses/mit-license.php"><img src="https://badges.frapsoft.com/os/mit/mit.svg"></a>
    <a href="https://github.com/elegantcoin/Cplusplus_OO/stargazers"><img src="https://img.shields.io/github/stars/elegantcoin/Cplusplus_OO.svg?logo=github"></a>
    <a href="https://github.com/elegantcoin/Cplusplus_OO/network/members"><img src="https://img.shields.io/github/forks/elegantcoin/Cplusplus_OO.svg?color=blue&logo=github"></a>
    <a href="https://www.python.org/"><img src="https://upload.wikimedia.org/wikipedia/commons/c/c3/Python-logo-notext.svg" align="right" height="48" width="48" ></a>
</p>
<br />


```

## :fire: OOP

```

## :fire 1.

```C++
// #include "stdafx.h"
#include <iostream> // cout cin
using namespace std;

int main(void)
{
    char a = 'A';
    char *p1 = &a;
    wchar_t b = L'B';
    wchar_t c = L'龙';
    wchar_t str[] = L"一条龙";
    int d = 10;
    int *p2 = &d;
    float e = 10.0;
    double f = 10.0;
    short g = 10.0;
    long h = 10.0;
    cout << a << " char a -> " << sizeof(a) << endl; // 1B
    cout << *p1 << " char * p1 -> " << sizeof(p1) << endl; // 8B
    cout << d << " int d -> " << sizeof(d) << endl; // 4B
    cout << *p2 << " int * p2 -> " << sizeof(p2) << endl; // 8B
    cout << e << " float e -> " << sizeof(e) << endl; // 4B
    cout << f << " double f -> " << sizeof(f) << endl; // 8B
    cout << g << " short g -> " << sizeof(g) << endl; // 2B
    cout << h << " long h -> " << sizeof(h) << endl; // 8B
    // 宽字符输出用 wcout
    wcout << b << " -> " << sizeof(b) << endl; // 4B
    // C++中默认为 EN_US，中文需转换
    // wcout.imbue(locale("chs"));
    wcout << c << " -> " << sizeof(c) << endl; // 2B 龙
    wcout << str << endl;                      // 一条龙
    return 0;
}
```

## :fire 2.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main()
{
    vector<string> msg {"Hello", "C++", "World", "from", "VS Code", "and the C++ extension!"};

    for (const string& word : msg)
    {
        cout << word << " ";
    }
    cout << endl;
}


```

## :fire 3.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

// 强制类型转换
int main()
{
    long int ageL=123;
    // short ageS=int (ageL);
    short ageS=(int) ageL;
    cout <<"ageL "<<ageL<<" "<<sizeof(ageL)<<endl;
    cout <<"ageS "<< ageS<<" "<<sizeof(ageS)<<endl;
    cout << endl;
}


```


## :fire 4.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;


// error: too few arguments to function 'int fun(int, int)'
// int fun(int x, int y)
int fun(int x, int y)
{
    return x * 2;
}

// 函数内不能再定义函数 error: a function-definition is not allowed here before '{' token
int main()
{
    int x = 10;
    int b;
    b = fun(x);
    cout << b << endl;
    cout << endl;
}


```

## :fire 5.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

void show(int = 1, float = 2.3, long = 6);

/*
 默认值不能有间隔，否则就无法判断哪个值对应哪个参数名了。例：
void show(int a=1,float b,long c=6);
我调用时：show(2);谁能分得清，现在是 a=2 还是b=2？
这样可以
void show(int a,float b=2.3,long c=6); show(2); // a=2,b=2.3,c=6
*/
int main()
{
    show();
    show(2);
    show(4, 5.6);
    show(8, 12.34, 50L);
    return 0;
}

void show(int first, float second, long third)
{
    cout << "first=" << first
         << " second=" << second
         << " third=" << third << endl;
}


```

## :fire 6.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

void a(int, int);
void a(int);
void a(float);

// 静态多态，重载，名字一样，参数个数不一样，类型不一样
// Overload 也被称为“静态多态”，“静”是指在编译时就能确定哪个函数是哪个函数。
int main()
{
    a(5);
    // float b = 5.53;
    // a(b);
    a(5.53f);
    a(6, 7);
    return 0;
}

void a(int i)
{
    cout << i << endl; //输出 5
}

void a(float i)
{
    cout << i << endl; //输出 5.53
}

void a(int i, int j)
{
    cout << i << j << endl; //输出 67
}


```

## :fire 7.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class Parent
{
public:
    int Add(int x, int y)
    {
        return x + y;
    }
    // 成员函数的重载
    //重载(overload)Add 函数
    float Add(float x, float y)
    {
        return x + y;
    }
};

int main()
{
    Parent *p = new Parent();
    // 重 载 (overload) 
    printf("%d\n",p->Add(1, 2));
    printf("%f\n", p->Add(3.4f, 4.5f));

    delete p;
    return 0;
}


```

## :fire 8.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

inline int dbtest(int i) //将函数定义为内联函数
{
    return (i % 2 > 0) ? 1 : 0;
}

int main()
{
    int i = 0;
    for (i = 1; i < 100; i++)
    {
        // windows /n 和的linux mac 的 \n
        printf("i:%d 奇偶性:%d \n", i, dbtest(i));
    }
    cout << endl;
}


```

## :fire 9.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main(int argc, char *argv[])
{

    int a = 1;
    int &b = a;
    cout << "b " << b << " " << sizeof(b) << endl; // 1 b=3;
    cout << "a " << a << " " << sizeof(a) << endl; // 3

    int c = a;
    c = 100;
    int &d = c;
    cout << "c " << c << " " << sizeof(c) << endl; // 5
    cout << "d " << d << " " << sizeof(d) << endl; // 2 c=4;
    cout << endl;
}

// 在函数参数和返回值中使用引用，是个提高效率的方法。
// int &fun(int &a)
// {
//     return a + 6;
// }

```

## :fire 10.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main()
{
    int *birthday = new int[3];
    birthday[0] = 6;
    birthday[1] = 24;
    birthday[2] = 1940;
    cout << "I was born on "
         << birthday[0] << '/' << birthday[1] << '/' << birthday[2] << endl;
    delete[] birthday; //在删除数组时，delete 运算符后要有一对方括号。
    return 0;
}


```

## :fire 11.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class MyCls
{
public:
    void fun3()
    {
        cout << "fun3" << endl;
    };

protected:
    void fun2(){};

private:
    void fun1(){};
};

int main(int argc, char *argv[])
{
    MyCls mc;
    // mc.fun1(); //不让访问
    // mc.fun2(); //不让访问
    mc.fun3(); //让访问

    return 0;
}


```

## :fire 12.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class Box
{
// 编译器会自动生成一个 Box()构造函数
};

int main()
{
Box a; // 默认构造函数，那么实例化对象时，直接写 Box obj;即可也不需要括号

return 0;
}


```

## :fire 13.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class Box
{
private:
    int height, width, depth; // 3 个私有数据成员

public:
    //带参数构造函数
    Box(int, int, int);

    // copy 构造函数
    Box(Box &);

    void volume(); //成员函数
};

Box::Box(int ht = 2, int wd = 3, int dp = 4)
{
    height = ht;
    width = wd;
    depth = dp;
    cout << "constructor" << endl;
}

Box::Box(Box &b)
{
    height = b.height;
    width = b.width;
    depth = b.depth;
    cout << "copy constructor" << endl;
}

void Box::volume()
{
    cout << height * width * depth << endl;
}

int main()
{
    /* 各种实例化对象的写法 */ 
    Box a(3, 4, 5); // constructor 
    a.volume(); // 60

    //函数的参数是以传值方式传递进来的对象
    Box b = a; //隐式调用拷贝构造函数 copy constructor 
    b.volume(); // 60

    Box c(b); //显式调用拷贝构造函数 copy constructor 
    c.volume(); // 60

    // 比Box a多 一步，生成再赋值给d
    Box d = Box(5, 6, 7);      // constructor 
    d.volume();	// 210

    // 指针的只能这么写
    Box *p = new Box(4, 5, 6); // constructor 
    p->volume();	// 120

     return 0;
}


```

## :fire 14.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
public:
    A(int); // 类型转换构造函数
    A(A &); // 拷贝构造函数，建议写成引用
};

A::A(int a)
{
    cout << "typecast constructor" << endl;
}

A::A(A &a)
{
    cout << "copy constructor" << endl;
}

int main()
{
    A a = 10; //隐式转换：typecast constructor
    A b(10);  //显式转换：typecast constructor

    //函数的参数是以传值方式传递进来的对象
    A c = b; // 隐式调用copy constructor
    A d(b);  // 显式调用 copy constructor

    return 0;
}


```

## :fire 15.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
public:
    explicit A(int); // 类型转换构造函数
    explicit A(A &); // 拷贝构造函数
};

A::A(int a)
{
    cout << "typecast constructor" << endl;
}

A::A(A &a)
{
    cout << "copy constructor" << endl;
}

int main()
{
    // explicit 显式调用

    // error: conversion from 'int' to non-scalar type 'A' requested
    // A a = 10; //隐式转换：typecast constructor
    A b(10); //显式转换：typecast constructor

    // error: no matching function for call to 'A::A(A&)'
    // A c = b; // 隐式调用copy constructor
    A d(b); // 显式调用 copy constructor

    return 0;
}


```

## :fire 16.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
public:
    operator int(); // 禁止有返回值
};

class B
{
public:
    explicit B(int); // 类型转换构造函数
    explicit B(B &); // 拷贝构造函数
};


A::operator int()
{
    cout << "operator int" << endl;
    return 18;
}


B::B(int b)
{
    cout << "typecast constructor" << endl;
}

B::B(B &b)
{
    cout << "copy constructor" << endl;
}

// 基本类型和其他类类型相互转换

int main()
{
    // int转换为其它类
    B b(10); //显式转换：typecast constructor

    // 本类转换为其它类
    A a;
    int i = a;         //隐式调用 operator int
    int j(a);          //显式调用 operator int
    cout << i << endl; // 18

    return 0;
}


```

## :fire 17.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

// class A
// {
//     int a, b;

// public:
//     A(int x, int y)
//     {
//         a = x;
//         b = y;

//         cout << a << "," << b << endl;
//     }
// };

// =========================================================================

// class A
// {
//     int a, b;

// public:
//     A(int x, int y) : a(x), b(y)
//     { // 内联函数
//         cout << a << "," << b << endl;
//     }
// };

// =========================================================================

class A
{
    int a, b;

public:
    A(int, int); // 这里不要使用参数初始化列表
};

A::A(int x, int y) : a(x), b(y) //在函数实现这里使用参数初始化列表
{
    cout << a << "," << b << endl;
}

// =========================================================================

// 参数函数参数化列表

// 若类中的数据成员是引用类型的，则只能在参数初始化表中为其赋值
// 参数初始化表速度快于赋值运算符
// operator= ， 因为后者会产生临时对象（ 匿名对象）

int main()
{
    A a(1, 2);

    return 0;
}


```

## :fire 18.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
public:
    A()
    {
        cout << "A" << endl;
    }

    // error: ISO C++ forbids declaration of 'operator=' with no type [-fpermissive]
    // 没有指定返回类型A时的报错
    A operator=(A &)
    {
        cout << "A operator=" << endl;
        return *this;
    }
};

class B
{
private:
    A a; //会调用A 类的构造函数
public:
    B(A &para) : a(para)
    {
        cout << "B" << endl;
    }
};

// =========================================================================

// class A
// {
// public:
//     A()
//     {
//         cout << "A" << endl;
//     }

//     A operator=(A &)
//     {
//         cout << "A operator=" << endl;
//         return *this;
//     }
// };

// class B
// {
// private:
//     A a; //会调用A 类的构造函数
// public:
//     B(A &para)
//     {
//         a = para; // A 这个 A 就是匿名对象
//         /*
//         上面这行
//         a=para;是隐式调用A()和A::operator=(A&)
//         等价于
//         a=A(para);显式调用 A()和A::operator=(A&)

//         调用了类型转换函数，自然就会产生 2 个A 类的匿名对象
//         */
//         cout << "B" << endl;
//     }
// };

int main()
{
    A a;    // A
    B b(a); //显式调用类型转换函数 B

    return 0;
}


```

## :fire 19.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
    int i;

public:
    A operator=(int n)
    {
        i = n;
        return *this;
    }

    void showI()
    {
        cout << " 1 " << this->i << endl; // 当前对象的 i，this=当前对象，所以写不写一样
        cout << " 2 " << i << endl;       // 当前对象的 i
    }

    void f(int i) // 那写不写一样，我何时要写？

    {
        cout << " 3 " << this->i << endl; // 当前对象的 i，this=当前对象
        cout << " 4 " << i << endl;       // 传进来的实参 i
    }

    A operator+(int n)
    {
        this->i = n;
        return *this;
    }
};

int main()
{
    A a;
    a = 3;
    a.showI();
    a.f(8);
    return 0;
}

```



## :fire 20.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class Base
{
public: //公有的
    int a1;
    virtual void test() = 0;

protected: //受保护的
    int a2;

private: //私有的
    int a3;
};

class PublicClass : public Base //共有继承有区别与其它方式的继承，继承后的各成员不会其改变控制方式
{
public:
    void test()
    {
        a1 = 1; // a1 仍然保持 public
        a2 = 2; // a2 仍然保持 protected
        // a3=3;//错误，派生类不能操作基类的私有成员
    }
};

class ProtectedClass : protected Base //保护继承
{

public:
    void test()
    {
        a1 = 1; // a1 在这里被转变为 protected
        a2 = 2; // a2 仍然保持 protected
        // a3=3; //错误，派生类不能访问基类的私有成员
    }
};

class PrivateClass : private Base //私有继承
{
public:
    void test()
    {
        a1 = 1; // a1 在这里被转变为 private
        a2 = 2; // a2 在这里被转变为 private
        // a3=3; //错误，基类私有成员对文件区域与派生类区域都是不可访问的
    }
};

class PrivateClassSun : private PrivateClass //私有继承
{
public:
    void test()
    {
    }
};

int main()
{

    // a1 = 1; //错误，因为 a1 在PrivateClass 是private 的，不能够被子类继承
    // a2 = 2; //错误，因为 a2 在PrivateClass 是private 的，不能够被子类继承
    // a3=3; //错误，基类私有成员对文件区域与派生类区域都是不可访问的

    return 0;
}


```

## :fire 21.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
};

class B : public A
{
};

class C : public A
{
};

class D : public B, public C // 多继承
{
};

int main(int argc, char *argv[])
{
    return 0;
}


```

## :fire 22.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class Names
{
public:
    void *operator new(size_t) throw(bad_alloc); // 运算符函数
    void operator delete(void *) throw();
};

void *Names::operator new(size_t) throw(bad_alloc)
{
    throw bad_alloc();
}

void Names::operator delete(void *p) throw()
{
    if (p != 0)
        inuse[((char *)p - pool) / sizeof(Names)] = false;
}

int main()
{
    Names *np = new Names(name);
    delete np;
    return 0;
}


```

## :fire 23.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
public:
    void fun()
    {
        cout << "A::fun" << endl;
    }
};

class B : public A
{
public:
    void fun()
    {
        cout << "B::fun" << endl;
    }
};

class C : public A
{
public:
    void fun()
    {
        cout << "C::fun" << endl;
    }
};

int main(int argc, char *argv[])
{
    B b;
    A *p = &b; //看这里p的类型是A，后面p掉的都是A的fun
    p->fun();  // A::fun()
    b.fun();   // B::fun()

    C c;
    p = &c;
    p->fun(); // A::fun()
    c.fun();  // C::fun()

    return 0;
}


```

## :fire 24.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
public:
    virtual void fun() // 就加这里
    {
        cout << "A::fun" << endl;
    }
};

class B : public A
{
public:
    void fun()
    {
        cout << "B::fun" << endl;
    }
};

class C : public A
{
public:
    void fun()
    {
        cout << "C::fun" << endl;
    }
};

int main(int argc, char *argv[])
{
    B b;
    A *p = &b;
    p->fun(); // B::fun()
    b.fun();  // B::fun()

    C c;
    p = &c;
    p->fun(); // C::fun()
    c.fun();  // C::fun()

    return 0;
}


```

## :fire 25.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A // A 是接口，不干活儿。只下命令 fun
{
public:
    virtual void fun() = 0; // 不需要A 的 fun()干活
};

class B : public A
{
public:
    void fun() // 干活！
    {
        cout << "B::fun" << endl;
    }
};

class C : public A
{
public:
    void fun() // 干活！
    {
        cout << "C::fun" << endl;
    }
};

int main(int argc, char *argv[])
{
    B b;
    A *p = &b;
    p->fun(); // B::fun()
    b.fun();  // B::fun()

    C c;
    p = &c;
    p->fun(); // C::fun()
    c.fun();  // C::fun()

    return 0;
}


```

## :fire 26.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
protected:
    int n;
};

// class B : public A
// {
// };

// class C : public A
// {
// };

// class D : public B, public C
// {
// public:
//     void fun()
//     {
//         // n = 5; // 报错，因为现在有 B::n,C::n 两个 n
//         B::n = 5; // 只能用这种方法来处理歧义性
//     }
// };

class B : virtual public A
{
};

class C : virtual public A
{
};

class D : virtual public B, virtual public C
{
public:
    void fun()
    {
        n = 5; // 不报错
        B::n = 5; //此时 A::n == B::n == C::n == D::n，都是 1 个n 了！
    }
};

// 虚继承 解决菱形问题，多爷爷
int main()
{
    return 0;
}


```

## :fire 27.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

namespace N1
{
    int a;
    int add(int left, int right)
    {
        return left + right;
    }
}

namespace N2
{
    int a;
    int add(int left, int right)
    {
        return left - right;
    }
}

int main()
{
    int c,d;
    c = N1::add(10, 20); //命名空间的调用
    cout << c << endl;
    d = N2::add(100, 200); //命名空间的调用
    cout << d << endl;
    return 0;
}


```

## :fire 28.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
    int i;

public:
    A(int a) : i(a){};
    friend void f(A &a); // 我是A 类的朋友，哪种朋友呢？连private 都能访问的朋友，
    // 亲密无间
};

void f(A &a)
{
    cout << a.i << endl;
}

// 友元函数：友元普通函数
int main()
{
    A a(1);
    f(a);
    return 0;
}


```

## :fire 29.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A;
class B
{
public:
    void f(A &a);
};

class A
{
    int i;

public:
    A(int a) : i(a){};
    friend void B::f(A &a);
};

void B::f(A &a)
{
    cout << a.i << endl;
}

int main()
{
    A a(1);
    B b;
    b.f(a);

    return 0;
}


```


## :fire 30.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A;
class B
{
public:
    void f(A &a);
};

class A
{
    int i;

public:
    A(int a) : i(a){};
    friend B;
};

void B::f(A &a)
{
    cout << a.i << endl;
}

int main()
{
    A a(1);
    B b;
    b.f(a);

    return 0;
}


```

## :fire 31.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int g = 100;
class A
{
public:
    A() : j(0){};      //构造函数
    void pop(){};      // 非const 成员函数
    void f(int) const; // const 成员函数
    void f2() const;   // const 成员函数

private:
    int i;       // 非const 成员
    const int j; // const 成员==常量
};

void A::f2() const
{
}

void A::f(int n) const
{
    /*读写普通变量*/
    n = 1; // 可以
    g++;   // 可以

    /*const 成员函数不能写非 const 数据成员，但是能读它*/
    int a = i;
    //++i; // 错误，不能写非 const 成员

    /*谁都不能写 const 成员：因为 const 就是常量、禁止修改之意*/
    int b = j;
    //++j; // 错误，常量不能被修改

    /*const 成员函数不能调用非 const 成员函数*/
    // pop(); // 错误，访问非 const 成员

    /*const 成员函数能调用 const 成员函数*/
    f2();
}

int main()
{
    A a;
    a.f(1);
    a.f2();
    return 0;
}


```

## :fire 32.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
public:
    mutable int i; // mutable 成员可被 const 成员、非 const 成员共同访问
    void f() const
    {
        i++; // const 成员不能写非 const 数据成员，但是能读它
    }
    void f2()
    {
        i++; // 
    }
};

class B
{
public:
    void pop(){};
    int f(int) const; // const成员函数
private:
    mutable int m_num;
};

int B::f(int n) const
{
    n = 1;                 //可以
    m_num += 100;          // m_num
    cout << m_num << endl; // m_num
    return m_num;
}

// mutable 成员可被 const 成员、非 const 成员共同访问
int main()
{
    B b;
    b.f(2);

    return 0;
}


```

## :fire 33.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
private:
    const int i;

public:
    A() : i(1) {} // OK
    // A(){i=1;} // 报错
};

// const 成员只能在构造函数中通过初始化列表来赋值
int main()
{

    return 0;
}


```

## :fire 34.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
    static int i;
    // 不允许在这里赋值 i=5
};

int A::i = 0; //外部初始化

int main()
{
    return 0;
}


```

## :fire 35.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class A
{
public:
    static int i; // 不允许在这里赋值 i=5
};

int A::i = 0; //外部初始化

// static 变量的使用：全员共享！我管它叫小全局变量
// C 语言中我说过，静态变量的特点：
// 生命周期：静态变量和全局变量的生命周期一样
// 作用域：看定义静态变量的位置的位置，和局部变量、全局变量一样。

int main()
{
    A a, b;

    cout << a.i << endl;
    cout << b.i << endl;

    cout << A::i << endl;

    a.i = 8;
    cout << a.i << endl;
    cout << b.i << endl;
    // 静态成员所在类，不需要初例化或new 该类，
    //  就可以通过“类名::static 成员”的访问访问静态成员
    cout << A::i << endl;

    return 0;
}


```

## :fire 36.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

double division(int a, int b)
{
    if (b == 0) // 除数为 0，是一种错误
    {
        // 抛出异常（错误），程序在这里会中断， 抛出异常给上层调用者来处理
        throw "Division by zero condition!";
    }
    return (a / b); // 没错，正常进行
}

int main()
{
    int x = 50;
    int y = 0;
    double z = 0;

    try
    {
        // 用于捕捉异常
        z = division(x, y); // 发生了异常（错误）
        cout << z << endl;  // 发生异常后，这句就不会被执行
    }
    catch (const char *msg)
    { // 处理异常
        cerr << msg << endl;
    }

    return 0;
}


```

## :fire 37.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename PARAM>
PARAM add(PARAM a, PARAM b) //注意形参和返回类型
{
    return a + b;
}

// 泛型
int main()
{
    int num1, num2, sum;
    // cin >> num1 >> num2;
    num1 = 1;
    num2 = 1;
    sum = add(num1, num2);
    // 用 int 匹配模版参数 T，产生函数原型 add(int,int) 。若
    // sum, num1, num2 //类型不一致则无法匹配。
    cout << sum << endl;

    float num12, num22, sum2;
    // cin >> num12 >> num22;
    num12 = 1.2;
    num22 = 1.3;
    sum2 = add(num12, num22);
    //用 int 匹配模版参数T，产生函数原型add(int,int)。若
    // sum, num1, num2 类型不一致则无法匹配。
    cout << sum2 << endl;
    return 0;
}


```

## :fire 38.

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T>
class A
{
public:
    A()
    {
        cout << "constructor()" << endl;
    }

    A(T a) //类型转换构造函数，如之前的例子：A(int& a)
    {
        this->a = a; // 这里必须写 this，否则我不知道你是哪个 a（歧义性）
        cout << "constructor(" << a << ")" << endl;
    }

    /*
    operator+的返回值是 A 类的对象
    要生成“模板类的对象”就得这么写<T>。即：A<int> = A 类（类型实参为 int）的对象
    */
    // A<T> operator+(A &b) //运算符重载
    // {
    //     A<T> tmp(a + b.a); // 产生一个新的 A 类对象，所以输出 constructor(a)
    //     cout << "operator+" << endl;
    //     return tmp;
    // }

    A<T> &operator+(A &b) //运算符重载
    {
        A<T> tmp(a + b.a); // 产生一个新的 A 类对象，所以输出 constructor(a)
        cout << "operator+" << endl;
        return *this;
    }

private:
    T a;
};

int main()
{
    //对象的定义，必须声明模板类型，因为要分配内存
    A<int> a(1);  // 编译时就会“生成”模板类 A<int>
    A<int> b(2);  // 显式类型转换构造函数
    A<int> e = 4; // 隐式类型转换构造函数

    a + b;            // a+b 返回的 A 类对象，没人接受 operator+
    A<int> c = a + b; // a+b 返回的A 类对象给了c	operator+ 隐式类型转换构造函数
    A<int> d(a + b);  // operator + 显式类型转换构造函数

     return 0;
}


#
#test39.cpp|       8

#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main()
{
}


```