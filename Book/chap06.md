Table of Contents
=================

* [第6章　过程封装——函数　104](#%E7%AC%AC6%E7%AB%A0%E8%BF%87%E7%A8%8B%E5%B0%81%E8%A3%85%E5%87%BD%E6%95%B0104)
  * [6\.1　函数定义　105](#61%E5%87%BD%E6%95%B0%E5%AE%9A%E4%B9%89105)
    * [6\.1\.1　函数的基本结构　105](#611%E5%87%BD%E6%95%B0%E7%9A%84%E5%9F%BA%E6%9C%AC%E7%BB%93%E6%9E%84105)
    * [6\.1\.2　return语句　105](#612return%E8%AF%AD%E5%8F%A5105)
    * [6\.1\.3　函数示例　105](#613%E5%87%BD%E6%95%B0%E7%A4%BA%E4%BE%8B105)
  * [6\.2　函数的使用　108](#62%E5%87%BD%E6%95%B0%E7%9A%84%E4%BD%BF%E7%94%A8108)
    * [6\.2\.1　函数原型的声明　108](#621%E5%87%BD%E6%95%B0%E5%8E%9F%E5%9E%8B%E7%9A%84%E5%A3%B0%E6%98%8E108)
    * [6\.2\.2　函数调用　109](#622%E5%87%BD%E6%95%B0%E8%B0%83%E7%94%A8109)
    * [6\.2\.3　将函数与主程序放在一起　109](#623%E5%B0%86%E5%87%BD%E6%95%B0%E4%B8%8E%E4%B8%BB%E7%A8%8B%E5%BA%8F%E6%94%BE%E5%9C%A8%E4%B8%80%E8%B5%B7109)
    * [6\.2\.4　函数调用过程　110](#624%E5%87%BD%E6%95%B0%E8%B0%83%E7%94%A8%E8%BF%87%E7%A8%8B110)
  * [6\.3　变量的作用域　113](#63%E5%8F%98%E9%87%8F%E7%9A%84%E4%BD%9C%E7%94%A8%E5%9F%9F113)
  * [6\.4　变量的存储类别　115](#64%E5%8F%98%E9%87%8F%E7%9A%84%E5%AD%98%E5%82%A8%E7%B1%BB%E5%88%AB115)
    * [6\.4\.1　自动变量　115](#641%E8%87%AA%E5%8A%A8%E5%8F%98%E9%87%8F115)
    * [6\.4\.2　静态变量　115](#642%E9%9D%99%E6%80%81%E5%8F%98%E9%87%8F115)
    * [6\.4\.3　寄存器变量　117](#643%E5%AF%84%E5%AD%98%E5%99%A8%E5%8F%98%E9%87%8F117)
    * [6\.4\.4　外部变量　117](#644%E5%A4%96%E9%83%A8%E5%8F%98%E9%87%8F117)
  * [6\.5　数组作为函数参数　119](#65%E6%95%B0%E7%BB%84%E4%BD%9C%E4%B8%BA%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0119)
  * [6\.6　带默认值的函数　124](#66%E5%B8%A6%E9%BB%98%E8%AE%A4%E5%80%BC%E7%9A%84%E5%87%BD%E6%95%B0124)
  * [6\.7　内联函数　125](#67%E5%86%85%E8%81%94%E5%87%BD%E6%95%B0125)
  * [6\.8　重载函数　126](#68%E9%87%8D%E8%BD%BD%E5%87%BD%E6%95%B0126)
  * [6\.9　函数模板　128](#69%E5%87%BD%E6%95%B0%E6%A8%A1%E6%9D%BF128)
  * [6\.10　递归函数　129](#610%E9%80%92%E5%BD%92%E5%87%BD%E6%95%B0129)
    * [6\.10\.1　递归函数的基本概念　129](#6101%E9%80%92%E5%BD%92%E5%87%BD%E6%95%B0%E7%9A%84%E5%9F%BA%E6%9C%AC%E6%A6%82%E5%BF%B5129)
    * [6\.10\.2　递归函数的应用　131](#6102%E9%80%92%E5%BD%92%E5%87%BD%E6%95%B0%E7%9A%84%E5%BA%94%E7%94%A8131)
  * [\*6\.11　基于递归的算法　136](#611%E5%9F%BA%E4%BA%8E%E9%80%92%E5%BD%92%E7%9A%84%E7%AE%97%E6%B3%95136)
    * [6\.11\.1　回溯法　136](#6111%E5%9B%9E%E6%BA%AF%E6%B3%95136)
    * [6\.11\.2　分治法　140](#6112%E5%88%86%E6%B2%BB%E6%B3%95140)
    * [6\.11\.3　动态规划　143](#6113%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92143)
  * [\*6\.12　C\+\+11的扩展　146](#612c11%E7%9A%84%E6%89%A9%E5%B1%95146)
    * [6\.12\.1　constexpr函数　146](#6121constexpr%E5%87%BD%E6%95%B0146)
    * [6\.12\.2　尾置返回类型　146](#6122%E5%B0%BE%E7%BD%AE%E8%BF%94%E5%9B%9E%E7%B1%BB%E5%9E%8B146)
  * [6\.13　编程规范及常见错误　147](#613%E7%BC%96%E7%A8%8B%E8%A7%84%E8%8C%83%E5%8F%8A%E5%B8%B8%E8%A7%81%E9%94%99%E8%AF%AF147)
  * [6\.14　小结　147](#614%E5%B0%8F%E7%BB%93147)
  * [6\.15　习题　148](#615%E4%B9%A0%E9%A2%98148)

---

# 第6章　过程封装——函数　104
## 6.1　函数定义　105
### 6.1.1　函数的基本结构　105
### 6.1.2　return语句　105
### 6.1.3　函数示例　105
**代码清单6-1 无参数、无返回值的函数实例**

```cpp
// 输出一个由5行组成的三角形
// 用法：PrintStar()
void  PrintStar()
{
    cout << "    *\n";
    cout << "   ***\n";
    cout << "  *****\n";
    cout << " ********\n";
    cout << "**********\n";
}
```

**代码清单6-2 有参数、无返回值的函数实例**

```cpp
// 输出一个由numOfLine行组成的三角形
// 用法：PrintStarN(10);
void PrintStarN(int numOfLine)
{
    int i, j;

    for (i = 1; i <= numOfLine; ++i)  {           // 打印第i行
        cout << endl;
        for (j = 1; j <= numOfLine - i; ++j)     // 打印前置空格
            cout << ' ';
        for (j = 1; j <= 2 * i - 1; ++j)         // 打印连续的*号
            cout << "*";
    }
    cout << endl;
}
```

**代码清单6-3 有参数、有返回值的函数实例**

```cpp
// 计算n！
// 用法：fact = p(n);
int p(int n)
{
    int s = 1;

    if ( n < 0)  return (0);
    for (int i = 1; i <=  n;  ++i)  s *=  i;

    return(s);
}
```

**代码清单6-4 无参数、有返回值的函数实例**

```cpp
// 从键盘获取一个1 – 10之间的整数
// 用法：num = getInput();
int getInput()
{
    int num;

    while (true) {
        cin >> num;
        if (num >= 1 && num <= 10) return num;
    }
}
```

**代码清单6-5 返回布尔值的函数实例**

```cpp
// 判断某个年份是否闰年
// 用法：if (isLeapYear(2016))……
bool isLeapYear(int year)
{
    bool leapyear;

    leapyear = (((year % 4 == 0) && (year  % 100 != 0)) || (year % 400 == 0));

    return (leapyear);
}
```

## 6.2　函数的使用　108
### 6.2.1　函数原型的声明　108
### 6.2.2　函数调用　109
### 6.2.3　将函数与主程序放在一起　109
**代码清单6-6　函数的使用**

```cpp
//文件名：6-6.cpp
//多函数程序的组成及函数的使用
#include <iostream>
using namespace std;

void PrintStar(int);                  //函数原型声明

//主程序
int main()
{
    int n;

    cout << "请输入要打印的行数：";
    cin >> n;

    PrintStar(n); //函数调用，n为实际参数

    return 0;
}

//函数：PrintStar
//用法：PrintStar(numOfLine)
//作用：在屏幕上显示一个由numOfLine行组成的三角形
void PrintStar(int numOfLine)
{
    int i, j;

    for (i = 1; i <= numOfLine; ++i) {
        cout << endl;
        for (j = 1; j <= numOfLine - i; ++j)  cout << ' ';
        for (j = 1; j <= 2 * i - 1; ++j)  cout << "*";
    }
    cout << endl;
}
```

### 6.2.4　函数调用过程　110

**代码清单6-7　函数调用实例**

```cpp
//文件名：6-7.cpp
//函数调用示例
#include <iostream>
using namespace std;
int p( int );
int max( int a, int b );

int main()
{
    int x, y;

    cin >> x >> y;
    cout << max(x, y);

    return 0 ;
}

int p( int n )
{
    int s = 1;

    if (n < 0) return(0);
    for (int i = 1; i <= n; ++i)   s *= i;

    return(s);
}

int max( int a, int b )
{
    int n1, n2;

    n1 = p(a);
    n2 = p(b);

    return (n1 > n2 ? n1 : n2);
}

```

## 6.3　变量的作用域　113

**代码清单6-8　全局变量实例**

```cpp
//文件名：6-8.cpp
//全局变量示例
#include <iostream>
using namespace std;

void f1();
void f2();
int g = 15;

int main()
{
    cout << g <<endl;
    f1();
    f2();

    return 0;
}

void f1()
{
    g = 20;
}

void f2()
{
    cout << g << endl;
}
```
## 6.4　变量的存储类别　115
### 6.4.1　自动变量　115
### 6.4.2　静态变量　115

**代码清单6-9　静态局部变量的应用**

```cpp
//文件名：6-9.cpp
//静态局部变量的使用
#include<iostream>
using namespace std;

int f(int a);

int main()
{
    int a = 2;

    for (int i = 0; i < 3; ++i)  cout << f(a);

    return 0;
}

int f(int a)
{
    int b = 0;
    static int c = 3;

    b = b + 1;   c = c + 1;

    return(a + b + c);
}
```
### 6.4.3　寄存器变量　117
### 6.4.4　外部变量　117

**代码清单6-10　全局变量的错误用法**

```cpp
//文件名：6-10.cpp
//全局变量的错误用法
#include <iostream>
using namespace std;
void f();

int main()
{
    // 加外部变量声明
    // extern int x;

    f();
    cout << "in main(): x= " << x << endl;
    return 0;
}

int x;

void f()
{
    cout << "in f(): x= " << x << endl;
}
```

**代码清单6-11　外部变量应用实例**

```cpp
// file1.cpp
// 外部变量的应用
#include <iostream>
using namespace std;

void f();
extern x;   //外部变量的声明

int main()
{
    f();
    cout << "in main(): x= " << x << endl;
    return 0;
}
```

```cpp
//file2.cpp

#include <iostream>
using namespace std;

int x;  //全局变量的定义

void f()
{
    cout << "in f(): x= " << x << endl;
}
```

## 6.5　数组作为函数参数　119

**代码清单6-12　计算10位学生的平均成绩的函数及使用**

```cpp
//文件名：6-12.cpp
//计算10位学生的平均成绩的函数及使用
#include <iostream>
using namespace std;

int average(int array[10]); //函数原型声明

int main()
{
    int i, score[10];

    cout << "请输入10个成绩：" << endl;
    for ( i = 0; i < 10; i++)  cin >> score[i];

    cout << "平均成绩是：" << average(score) << endl;

    return 0;
}

int average(int array[10])
{
    int i, sum = 0;

    for (i = 0; i < 10; ++i)  sum += array[i];

    return sum / 10;
}
```

**代码清单6-13　整型数据逆序输出的程序**

```cpp
//文件名：6-13.cpp
//读入一串整型数据，将其逆序排列并输出排列后的数据。最多允许处理10个数据
#include <iostream>
using namespace std;

#define MAX 10

int ReadIntegerArray(int array[ ], int max, int flag );
void ReverseIntegerArray(int array[ ], int size);
void PrintIntegerArray(int array[ ], int size);

int main()
{
    int IntegerArray[MAX], flag, CurrentSize;

    cout << "请输入结束标记：";
    cin >> flag;

    CurrentSize = ReadIntegerArray(IntegerArray, MAX, flag );
    ReverseIntegerArray(IntegerArray, CurrentSize);
    PrintIntegerArray(IntegerArray, CurrentSize);

    return 0;
}

//函数：ReadIntegerArray
//作用：接收用户的输入，存入数组array，max是array的大小，flag是输入结束标记。
//当输入数据个数达到最大长度或输入了flag时结束
int ReadIntegerArray(int array[ ], int max, int flag )
{
    int size = 0;

    cout << "请输入数组元素，以" << flag << "结束：:" ;
    while (size < max) {
        cin >> array[size];
        if (array[size] == flag) break; else ++size;
    }

    return size;
}

//函数：ReverseIntegerArray
//作用：将array中的元素按逆序存放，size为元素个数
void ReverseIntegerArray(int array[ ], int size)
{
    int i, tmp;

    for (i = 0; i < size / 2; i++) {
        tmp = array[i];
        array[i] = array[size - i - 1];
        array[size - i - 1] = tmp;
    }
}

//函数：PrintIntegerArray
//作用：将array中的元素显示在屏幕上。size是array中元素的个数
void PrintIntegerArray(int array[ ], int size)
{
    int i;

    if (size == 0) return;
    cout << "逆序是：" << endl;
    for (i = 0; i < size; ++i)  cout << array[i] << '\t';
    cout << endl;
}
```

**代码清单6-14　函数的使用**

```cpp
//文件名：6-14.cpp
//例5.12的另一实现方法
#include <iostream>
using namespace std;

int convertToInt(char s[], int start, int base);
void convertToUpper(char s[]);

int main()
{
    char str[81];
    int sum = 0, i = 0;

    cin.getline(str, 81);
    convertToUpper(str);
    while (str[i] != ' ' && str[i] != '\0') ++i;   // 跳过刚才处理的整数

    while (str[i] != '\0') {
        if (str[i] != '0') sum += convertToInt(str, i, 10);
        else {
            if (str[i + 1] == 'X') sum += convertToInt(str, i + 2, 16);
            else sum += convertToInt(str, i + 1, 8);
        }

        while (str[i] != ' ' && str[i] != '\0') ++i;   // 跳过刚才处理的整数
        while (str[i] == ' ' && str[i] != '\0') ++i;    // 跳过整数之间的空格
    }

    cout << sum << endl;

    return 0;
}

void convertToUpper(char s[])
{
    for (int i = 0; s[i] != '\0'; ++i)
        if (s[i] >= 'a' && s[i] <= 'z')
            s[i] = s[i] - 'a' + 'A';
}

int convertToInt(char s[], int start, int base)
{
    int data = 0;
    switch (base) {
        case 10: while (s[start] != ' ' && s[start] != '\0')
                data = data * 10 + s[start++] - '0';
            break;
        case 8: while (s[start] != ' ' && s[start] != '\0')
                data = data * 8 + s[start++] - '0';
            break;
        case 16: while (s[start] != ' ' && s[start] != '\0') {
                data = data * 16;
                if (s[start] >= 'A' && s[start] <= 'F') data += s[start++] - 'A' + 10;
                else data += s[start++] - '0';
            }
    }
    return data;
}
```

## 6.6　带默认值的函数　124
## 6.7　内联函数　125

**代码清单6-15　用内联函数打印平方表和立方表的程序**

```cpp
//文件名：6-15.cpp
//用内联函数打印平方表和立方表
#include <iostream>
using namespace std;

inline int square(int x) {return x*x;}
inline int cube(int x) {return x*x*x;}

int main()
{
    int i;

    cout << "x" << '\t' << "x*x" << '\t' << "x*x*x" << endl;
    for (i = 1; i <= 100; ++i)
        cout << i << '\t' << square(i) << '\t' << cube(i) << endl;

    return 0;
}
```

## 6.8　重载函数　126

**代码清单6-16　重载函数实例**

```cpp
//文件名：6-16.cpp
//重载函数示例
#include <iostream>
using namespace std;

int max(int a1, int a2);
int max(int a1, int a2, int a3);
int max(int a1, int a2, int a3, int a4);
int max(int a1, int a2, int a3, int a4, int a5);

int main()
{
    cout << "max(3,5) is " << max( 3, 5) << endl;
    cout << "max(3,5,4) is " << max( 3, 5, 4) << endl;
    cout << "max(3,5,7,9) is " << max( 3, 5, 7, 9) << endl;
    cout << "max(3,5,2,4,6) is " << max( 3, 5, 2, 4, 6) << endl;

    return 0;
}

int max(int a1, int a2)
{
    return a1 > a2 ? a1 : a2;
}

int max(int a1, int a2, int a3)
{
    int tmp;

    if (a1 > a2) tmp = a1; else tmp = a2;
    if (a3 > tmp) tmp = a3;

    return tmp;
}

int max(int a1, int a2, int a3, int a4)
{
    int tmp;

    if (a1 > a2) tmp = a1; else tmp = a2;
    if (a3 > tmp) tmp = a3;
    if (a4 > tmp) tmp = a4;

    return tmp;
}

int max(int a1, int a2, int a3, int a4, int a5)
{
    int tmp;

    if (a1 > a2) tmp = a1; else tmp = a2;
    if (a3 > tmp) tmp = a3;
    if (a4 > tmp) tmp = a4;
    if (a5 > tmp) tmp = a5;

    return tmp;
}
```

## 6.9　函数模板　128

**代码清单6-17　函数模板的定义及使用**

```cpp
//文件名：6-17.cpp
//函数模板的定义及使用
#include <iostream>

using namespace std;

template <class T>
T mymax(T a, T b)
{
    return  a > b ? a : b;
}

int main()
{
    cout << "mymax(3,5) = " << mymax(3, 5) << endl;
    cout << "mymax(3.3, 2.5) = " << mymax(3.3, 2.5) << endl;
    cout << "mymax('d', 'r') = " << mymax('d', 'r') << endl;

    return 0;
}

```

## 6.10　递归函数　129
### 6.10.1　递归函数的基本概念　129
### 6.10.2　递归函数的应用　131

**代码清单6-18  解决汉诺塔问题的函数**

```cpp
//文件名：6-18.cpp
//汉诺塔问题
#include <iostream>
using namespace std;

void Hanoi(int n, char start, char finish, char temp);

int main()
{
    Hanoi(3, 'A', 'B', 'C'); // 将3个盘子从A柱子借助于C柱子移动到B柱子
    return 0;
}

// 汉诺塔问题：将n个盘子从start借助于temp移动到finish
// 用法：Hanoi(64, ’A’, ‘B’, ‘C’);
void Hanoi(int n, char start, char finish, char temp)
{
    if (n == 1)  cout << start << "->" << finish << '\t';
    else {
        Hanoi(n - 1, start, temp, finish);
        cout << start << "->" << finish << '\t';
        Hanoi(n - 1, temp, finish, start);
    }
}
```

**代码清单6-19　打印一个十进制整数的函数定义及使用**

```cpp
//文件名：6-19.cpp
//打印一个十进制整数
#include <iostream>
using namespace std;

void printInt(int);  //输出一个非负整型数

int main()
{
    int num;

    cout << "请输入一个整型数：" << endl;
    cin >> num;

    printInt(num);
    cout << endl;

    return 0;
}

//作用：以十进制打印非负整数num
//用法：printInt(1234)
void printInt(int num)
{
    if (num < 10)     //递归终止条件
        cout << static_cast<char>(num + '0');
    else {
        printInt(num / 10);
        cout << static_cast<char>(num % 10 + '0');
    }
}
```

**代码清单6-20　打印二进制、八进制、十进制或十六进制整数的函数定义及使用**

```cpp
//文件名：6-20.cpp
//打印二进制、八进制、十进制和十六进制整数
#include <iostream>
using namespace std;

const char DIGIT[17] = "0123456789abcdef";
void printInt(int, int);
int main()
{
    int num, base;

    cout << "请输入一个整型数：" << endl;
    cin >> num;
    cout << "请输入要打印的数制：" << endl;
    cin >> base;

    printInt(num, base);
    cout << endl;

    return 0;
}

//作用：以数制base打印非负整数num
//用法：printInt(1234, 8)
void printInt(int num, int base)
{
    if  (num < base) cout << DIGIT[num];
    else {
        printInt(num / base, base);
        cout << DIGIT[num % base];
    }
}
```


**代码清单6-21  固定前k个字母的全排列**

**代码清单6-22  交换数组中的两个元素**

```cpp
// 文件名：6-21.cpp
// 打印n个字符的全排列
#include <iostream>
#include <cstring>
using namespace std;

void PermuteWithFixedPrefix(char str[ ], int k);
void swap(char str[], int k, int i);
void ListPermutations(char str[]);

int main()
{
    char str[11];
    cout << "请输入字符：" << endl;
    cin.getline(str,11);
    cout << "全排列为：" << endl;
    ListPermutations(str);
    return 0;
}


// 输出字符串str的从第k个字符到最后一个字符的全排列
// 用法：PermuteWithFixedPrefix(str, k)；
void PermuteWithFixedPrefix(char str[ ], int k)
{
    int i;

    if ( k == (int)strlen(str) )  cout << str << endl;
    else  for (i = k; i < (int)strlen(str); ++i) {
            swap(str, k, i);
            PermuteWithFixedPrefix(str, k + 1);
            swap(str, k, i);
        }
}

// 交换数组str中的第k和第i个元素
// 用法：swap(string, 3, 7);
void swap(char str[], int k, int i)
{
    int tmp;

    tmp = str[k];
    str[k] = str[i];
    str[i] = tmp;
}

//包装函数
void ListPermutations(char str[])
{
    PermuteWithFixedPrefix(str, 0);
}
```
## *6.11　基于递归的算法　136
### 6.11.1　回溯法　136
### 6.11.2　分治法　140
### 6.11.3　动态规划　143
## *6.12　C++11的扩展　146
### 6.12.1　constexpr函数　146
### 6.12.2　尾置返回类型　146
## 6.13　编程规范及常见错误　147
## 6.14　小结　147
## 6.15　习题　148