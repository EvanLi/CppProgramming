# 第7章 间接访问——指针

## 1.日期字符串传给三个整型参数

**测试数据：**

```
12-Feb-18

日期：12 月份：2 年份：18

5-Oct-12
日期：5  月份：10  年份：12
```

**程序：**

```cpp
#include <iostream>
#include <cstring>

using namespace std;

void getDate(int &dd, int &mm, int &yy);

int main()
{
    int day, month, year;
    getDate(day, month, year);
    cout << "日期：" << day << "  月份：" << month << "  年份：" << year;
    return 0;
}

void getDate(int &dd, int &mm, int &yy)
{
    char str[9];
    char month[12][4] = {"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"};
    cout << "输入日期" << endl;
    cin >> str;
    if(str[1] == '-') {
        //字符串前加'0'
        for(int i = 8; i > 0; --i) {
            str[i] = str[i - 1]; //后移一位
        }
        str[0] = '0';
    }
    dd = 10 * (str[0] - '0') + str[1] - '0'; 
    for(mm = 1; mm <= 12; ++mm) {
        if(!strncmp(month[mm - 1], &str[3], 3)) break;
    }
    yy = 10 * (str[7] - '0') + str[8] - '0';
}
```
## 2.str1中删除str2中出现的字符

**测试数据：**

```
输入str1:
aabbcdehi
输入str2:
abh
在str1中删除str2中出现的字符后，str1为：
cdei
```

```cpp
#include <iostream>
using namespace std;

void deletechar1(char *str1, const char *str2);
void deletechar2(char *str1, const char *str2);

int main()
{
    char str1[40], str2[40];
    cout << "输入str1:" << endl;
    cin >> str1;
    cout << "输入str2:" << endl;
    cin >> str2;

    //    deletechar1(str1, str2); // 非递归
    deletechar2(str1, str2); // 递归
    cout << "在str1中删除str2中出现的字符后，str1为：" << endl;
    cout << str1 << endl;
    return 0;
}

void deletechar1(char *str1, const char *str2)
{
    int i = 0, j = 0;
    char *q;
    while(*(str2 + j) != 0) {
        while(*(str1 + i) != 0) {
            if(*(str1 + i) == *(str2 + j)) {
                q = str1 + i;
                while(*q != 0) {
                    *q = *(q + 1);
                    q++;
                }
            }
            if(*(str1 + i) != *(str2 + j))++i;
        }
        ++j;
        i = 0;
    }
}

void deletechar2(char *str1, const char *str2)
{
    int i = 0;
    char *q;
    if (*str2 == '\0')return ;
    while(*(str1 + i) != '\0') {
        if(*(str1 + i) == *(str2)) {
            q = str1 + i;
            while(*q != '\0') {
                *q = *(q + 1); //左移一位
                q++;
            }
        }
        if(*(str1 + i) != *(str2)) ++i;
    }
    i = 0;
    deletechar2( str1, str2 + 1);
}
```

## 3.整型数转换为字符串

**测试数据：**

```
-100

-100
```

```cpp
#include <iostream>

using namespace std;
char *itos(int n);

int main()//测试函数部分
{
    int n;
    cout << "输入整型数n:" << endl;
    cin >> n;
    cout << itos(n);
}

char *itos(int n)//考虑了负数的情况
{
    int i = 9, scale = 1e8;
    char *s = new char[10];
    if (n < 0) {
        s[0] = '-';
        n = -n;
    }
    if (n == 0) {
        s[0] = '0';
        s[1] = '\0';
        return s;
    }
    for (; n / scale < 1; i -= 1, scale = scale / 10);
    for (int m = 0; m <= i; m++) {
        if (s[0] == '-' && m == 0) {
            i = i + 1;
            continue;
        }
        if (m == i) {
            s[m] = '\0';
            break;
        }
        s[m] = n / scale + '0';
        n = n % scale;
        scale = scale / 10;
    }
    return s;

}
```

## 4.用带参数的main函数实现一个完成整数运算的计算器

**测试数据：**

```
calc 5 x 3

15

```

```cpp
#include <iostream>

using namespace std;
int chartoint(char *s);

int main(int argc, char *argv[])
{
    int num1, num2;
    num1 = chartoint(argv[1]);
    num2 = chartoint(argv[3]);
    switch (*argv[2]) {
        case '+': cout << num1 + num2; break;
        case '-': cout << num1 - num2; break;
        case 'x': cout << num1 * num2; break; //用x代替*，直接用*字符无法匹配到
        case '/': cout << num1 / num2; break;
    }
}

int chartoint(char *s)
{
    int num = 0;
    while(*s) {
        num = num * 10 + *s - '0';
        s++;
    }
    return num;
}

```

## 6.将Julian历法（用年及这一年中第几天表示日期）转换成月和日

**测试数据：**

```
2012 356

Dec 21
```

```cpp
#include <iostream>
#include <cstring>

using namespace std;
char *Julian(int year, int day);

int main()
{
    int year, day;
    cout << "输入年份和天数(用空格分隔)：" << endl;
    cin >> year >> day;
    if (Julian(year, day) != NULL)
        cout << Julian(year, day);
    else
        cout << "输入有误！" << endl;
    return 0;
}

char *Julian(int year, int day)
{
    const char *Month[12] = {"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dce"};
    int monthday[12] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    int i;
    bool flag = ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0);

    if(day <= 0 || day > 366 || year < 0) return NULL;
    if(!flag && day > 365) return NULL;

    monthday[1] += flag; //闰年2月29天

    for (i = 0; i < 12; ++i) {
        if(day <= monthday[i]) break;
        else day -= monthday[i];
    }
    char *date = new char[7];
    strcpy(date, Month[i]);
    date[3] = ' ';
    if(day < 10) {
        date[4] = day + '0';
        date[5] = '\0';
    } else {
        date[4] = day / 10 + '0';
        date[5] = day % 10 + '0';
        date[6] = '\0';
    }
    return date;
}
```

## 8.计算均值与方差

```cpp
#include <iostream>
using namespace std;
double *VarianceAndAverage(double *arr, int size);

int main()
{
    int n;
    cout << "输入数组规模：";
    cin >> n;
    cout << "输入" << n << "个数：";
    double *arr = new double[n];
    for(int i = 0; i < n; ++i) cin >> arr[i];
    double *result = VarianceAndAverage(arr, n);
    cout << "均值为：" << result[0] << endl;
    cout << "方差为：" << result[1] << endl;
    delete[] result;
    return 0;
}

double *VarianceAndAverage(double *arr, int size)
{
    double *result = new double[2];
    result[0] = 0;
    for(int i = 0; i < size; ++i) result[0] += arr[i];
    result[0] /= size;
    result[1] = 0;
    for(int i = 0; i < size; ++i) result[1] += (arr[i] - result[0]) * (arr[i] - result[0]);
    result[1] /= size;
    return result;
}
```

## 9.弦截法求方程的根

```cpp
#include <iostream>
#include <cmath>

using namespace std;

double root(double (*f)(double x), double x1, double x2);
double testfunc(double x);

int main()
{
    double a, b;
    cout << "输入区间左端点：";
    cin >> a;
    cout << "输入区间右端点：";
    cin >> b;
    cout << "方程的根为：" << root(testfunc, a, b);
    return 0;
}
//方法1：递归方法
//double root(double (*f)(double x), double x1, double x2)
//{
//  double f1 = f(x1), f2 = f(x2);
//  if(f1 == 0) return x1;
//  if(f2 == 0) return x2;
//  double x = (x1 * f2 - x2 * f1) / (f(x2) - f(x1));
//  double fx = f(x);
//  if(fx < 1e-6 && fx > -1e-6) return x;
//  return (fx * f1 >= 0) ? root(f, x, x2) : root(f, x1, x); 
//}

//方法2：循环方法
double root(double (*f)(double x), double x1, double x2)
{
    double f1, f2, x, fx;
    do {
        f1 = f(x1);
        f2 = f(x2);
        x = (x1 * f2 - x2 * f1) / (f2 - f1);
        fx = f(x);
        if (fx * f1 > 0) x1 = x; //取右半区间
        else x2 = x; //取左半区间
    } while (fabs(fx) > 1e-10);
    return x;
}

double testfunc(double x)
{
    return x * x - 2 * x - 3; //-1,3
}

```