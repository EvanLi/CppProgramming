Table of Contents
=================

* [第3章　分支程序设计　37](#%E7%AC%AC3%E7%AB%A0%E5%88%86%E6%94%AF%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A137)
  * [3\.1　关系表达式　37](#31%E5%85%B3%E7%B3%BB%E8%A1%A8%E8%BE%BE%E5%BC%8F37)
  * [3\.2　逻辑表达式　38](#32%E9%80%BB%E8%BE%91%E8%A1%A8%E8%BE%BE%E5%BC%8F38)
  * [3\.3　if语句　39](#33if%E8%AF%AD%E5%8F%A539)
    * [3\.3\.1　if语句的格式　39](#331if%E8%AF%AD%E5%8F%A5%E7%9A%84%E6%A0%BC%E5%BC%8F39)
    * [3\.3\.2　if语句的嵌套　43](#332if%E8%AF%AD%E5%8F%A5%E7%9A%84%E5%B5%8C%E5%A5%9743)
    * [3\.3\.3　条件表达式　44](#333%E6%9D%A1%E4%BB%B6%E8%A1%A8%E8%BE%BE%E5%BC%8F44)
  * [3\.4　switch语句及其应用　46](#34switch%E8%AF%AD%E5%8F%A5%E5%8F%8A%E5%85%B6%E5%BA%94%E7%94%A846)
  * [3\.5　编程规范及常见错误　52](#35%E7%BC%96%E7%A8%8B%E8%A7%84%E8%8C%83%E5%8F%8A%E5%B8%B8%E8%A7%81%E9%94%99%E8%AF%AF52)
  * [3\.6　小结　52](#36%E5%B0%8F%E7%BB%9352)
  * [3\.7　习题　53](#37%E4%B9%A0%E9%A2%9853)

---

# 第3章　分支程序设计　37
## 3.1　关系表达式　37
## 3.2　逻辑表达式　38
## 3.3　if语句　39
### 3.3.1　if语句的格式　39

**代码清单3-1　计算利息的程序（版本1）**

```
//文件名：3-1.cpp
//计算利息

#include <iostream>
#include <cmath>
using namespace std;

int main()
{
	const double oneYearRate = 0.025, twoYearRate = 0.028;
	double balance, interest;
	int type, startDate, endDate;;

	cout << "请输入存款类型（1：一年期， 2：两年期）：";
	cin >> type;
	cout << "请输入存款金额：";
	cin >> balance;
	cout << "请输入起始日期：";
	cin >> startDate;
	cout << "请输入终止日期：";
	cin >> endDate;

	if (type == 1)
		interest = pow( 1 + oneYearRate, endDate - startDate) * balance - balance;
	else
		interest = pow( 1 + twoYearRate, endDate - startDate) * balance - balance;

	cout << balance << " 元存 " << endDate - startDate << " 年共得利息 "
		 << interest << "元" << endl;

	return 0;
}
```

**代码清单3-2　计算利息的程序（版本2）**

```
//文件名：3-2.cpp
//计算利息

#include <iostream>
#include <cmath>
using namespace std;

int main()
{
	const double oneYearRate = 0.025, twoYearRate = 0.028;
	double balance, interest, rate;
	int startDate, endDate;;
	char type;

	cout << "请输入存款类型（O：一年期， T：两年期）：";
	cin >> type;
	cout << "请输入存款金额：";
	cin >> balance;
	cout << "请输入起始日期：";
	cin >> startDate;
	cout << "请输入终止日期：";
	cin >> endDate;

	if (type == 'O')
		rate = oneYearRate;
	else
		rate = twoYearRate;
	interest = pow( 1 + rate, endDate - startDate) * balance - balance;

	cout << balance << " 元存 " << endDate - startDate << " 年共得利息 "
		 << interest << "元" << endl;

	return 0;
}
```

**代码清单3-3　判断闰年的程序**

```
//文件名：3-3.cpp
//判断闰年
#include <iostream>
using namespace std;

int main()
{
	int year;
	bool result;

	cout << "请输入所要验证的年份：";
	cin >> year;

	result = (year % 4 == 0 && year % 100 != 0) || year % 400 == 0;

	if (result)  cout << year << "是闰年" << endl;
	else  cout << year << "不是闰年" << endl;

	return 0;
}
```
### 3.3.2　if语句的嵌套　43

**代码清单3-4　求一元二次方程解的程序**

```
//文件名：3-4.cpp
//求一元二次方程解
#include <iostream>
#include <cmath>           //sqrt所属的库
using namespace std;
int main()
{
	double a, b, c, x1, x2, dlt;

	cout << "请输入3个参数：" << endl;
	cout << "输入 a:";   cin >> a ;
	cout << "输入 b:";   cin >> b ;
	cout << "输入 c:";   cin >> c ;

	if (a == 0)
		if (b == 0) cout << "非法方程" << endl;
		else  cout << "是一元一次方程，x = " << -c / b << endl;
	else {
		dlt = b * b - 4 * a * c;
		if (dlt > 0) {                               //有两个实根
			x1 = (-b + sqrt(dlt)) / 2 / a;
			x2 = (-b - sqrt(dlt)) / 2 / a;
			cout << "x1 = " << x1 << "   x2 = " << x2 << endl;
		} else if (dlt == 0)                           //  有两个等根
			cout << "x1 = x2 = " << -b / a / 2 << endl;
		else cout << "无根" << endl;                    //无实根
	}

	return 0;
}
```
### 3.3.3　条件表达式　44

**代码清单3-5　判断点(x, y)是否落在以原点为圆心，r为半径的圆内的程序**

```
//文件名：3-5.cpp
//判断点(x, y)是否落在以原点为圆心，r为半径的圆内
#include <iostream>
using namespace std;

int main()
{
	double radius, x, y;

	cout << "请输入圆的半径：";
	cin >> radius;
	cout << "请输入点的坐标：";
	cin >> x >> y;

	cout << "点(" << x << ", " << y << ")" << (x * x + y * y <= radius * radius ? "" : "没有")
		 << "落在圆内" << endl;

	return 0;
}
```
## 3.4　switch语句及其应用　46

**代码清单3-6　利息计算程序**

```
//文件名：3-6.cpp
//计算利息

#include <iostream>
#include <cmath>
using namespace std;

int main()
{
	const double rate1Year = 0.025, rate2Year = 0.028, currentRate = 0.012;
	double balance, interest;
	int startDate, endDate, type;

	cout << "请输入存款类型（1：一年期， 2：两年期， 0：活期）：";
	cin >> type;
	cout << "请输入存款金额：";
	cin >> balance;
	cout << "请输入起始日期：";
	cin >> startDate;
	cout << "请输入终止日期：";
	cin >> endDate;

	switch (type) {
		case 0: interest = pow( 1 + currentRate, endDate - startDate) * balance - balance;; break;
		case 1: interest = pow( 1 + rate1Year, endDate - startDate) * balance - balance; break;
		case 2: interest = pow( 1 + rate2Year, endDate - startDate) * balance - balance; break;
	}

	cout << balance << " 元存 " << endDate - startDate << " 年共得利息 "
		 << interest << "元" << endl;

	return 0;
}
```

**代码清单3-7　分数转换程序**

```
//文件名：3-7.cpp
//将百分制转换成5个等级(A、B、C、D、E)
#include <iostream>
using namespace std;

int main()
{
	int score;

	cout << "请输入分数:";
	cin >> score;

	switch(score / 10) {
		case 10:
		case 9: cout << "A";   break;
		case 8: cout << "B";   break;
		case 7: cout << "C";   break;
		case 6: cout << "D";   break;
		default: cout << "E";
	}
	cout << endl;

	return 0;
}
```

**代码清单3-8　自动出题程序**

```
//文件名：3-8.cpp
//自动出题程序
#include <cstdlib>
#include <iostream>
using namespace std;

int main()
{
	int num1, num2, op, result1, result2;            //num1,num2:操作数，op:运算符，
	                                                 //result1,result2:结果

	num1 = rand() * 10 / (RAND_MAX + 1);             //生成运算数
	num2 = rand() * 10 / (RAND_MAX + 1);             //生成运算数
	op = rand() * 4 / (RAND_MAX + 1);                //生成运算符 0--+，1-- -，2--*，3-- /

	switch (op) {
		case 0:
			cout << num1 << " + " << num2 << " =? " ;
			cin >> result1;
			if (num1 + num2 == result1)  cout << "you are right\n";
			else  cout << "you are wrong\n";
			break;
		case 1:
			cout << num1 << " - " << num2 << " =? " ;
			cin >> result1;
			if (num1 - num2 == result1) cout << "you are right\n";
			else  cout << "you are wrong\n";
			break;
		case 2:
			cout << num1 << " * " << num2 << " =? " ;
			cin >> result1;
			if (num1 * num2 == result1) cout << "you are right\n";
			else  cout << "you are wrong\n";
			break;
		case 3:
			cout << num1 << " / " << num2 << " =? " ;
			cin >> result1;
			cout << "余数为=? ";
			cin >> result2;
			if ((num1 / num2 == result1) && (num1 % num2 == result2))
				cout << "you are right\n";
			else  cout << "you are wrong\n";
			break;
	}

	return 0;
}
```

**代码清单3-9　修改后的自动出题程序**

```
//文件名：3-9.cpp
//自动出题程序
#include <cstdlib>
#include <ctime>
#include <iostream>
using namespace std;

int main()
{
	int num1, num2, op, result1, result2;            //num1,num2:操作数，op:运算符，
	                                                 //result1,result2:结果

	srand(time(NULL));                               //随机数种子初始化

	num1 = rand() * 10 / (RAND_MAX + 1);             //生成运算数
	num2 = rand() * 10 / (RAND_MAX + 1);             //生成运算数
	op = rand() * 4 / (RAND_MAX + 1);                //生成运算符 0--+，1-- -，2--*，3-- /

	switch (op) {
		case 0:
			cout << num1 << " + " << num2 << " =? " ;
			cin >> result1;
			if (num1 + num2 == result1)  cout << "you are right\n";
			else  cout << "you are wrong\n";
			break;
		case 1:
			cout << num1 << " - " << num2 << " =? " ;
			cin >> result1;
			if (num1 - num2 == result1) cout << "you are right\n";
			else  cout << "you are wrong\n";
			break;
		case 2:
			cout << num1 << " * " << num2 << " =? " ;
			cin >> result1;
			if (num1 * num2 == result1) cout << "you are right\n";
			else  cout << "you are wrong\n";
			break;
		case 3:
			cout << num1 << " / " << num2 << " =? " ;
			cin >> result1;
			cout << "余数为=? ";
			cin >> result2;
			if ((num1 / num2 == result1) && (num1 % num2 == result2))
				cout << "you are right\n";
			else  cout << "you are wrong\n";
			break;
	}

	return 0;
}
```
## 3.5　编程规范及常见错误　52
## 3.6　小结　52
## 3.7　习题　53
