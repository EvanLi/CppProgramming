Table of Contents
=================

* [第4章　循环程序设计　56](#%E7%AC%AC4%E7%AB%A0%E5%BE%AA%E7%8E%AF%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A156)
  * [4\.1　计数循环　56](#41%E8%AE%A1%E6%95%B0%E5%BE%AA%E7%8E%AF56)
    * [4\.1\.1　for语句　56](#411for%E8%AF%AD%E5%8F%A556)
    * [4\.1\.2　for语句的进一步讨论　61](#412for%E8%AF%AD%E5%8F%A5%E7%9A%84%E8%BF%9B%E4%B8%80%E6%AD%A5%E8%AE%A8%E8%AE%BA61)
    * [4\.1\.3　for循环的嵌套　61](#413for%E5%BE%AA%E7%8E%AF%E7%9A%84%E5%B5%8C%E5%A5%9761)
    * [\*4\.1\.4　C\+\+11的扩展　62](#414c11%E7%9A%84%E6%89%A9%E5%B1%9562)
  * [4\.2　break和continue语句　62](#42break%E5%92%8Ccontinue%E8%AF%AD%E5%8F%A562)
  * [4\.3　基于哨兵的循环　64](#43%E5%9F%BA%E4%BA%8E%E5%93%A8%E5%85%B5%E7%9A%84%E5%BE%AA%E7%8E%AF64)
    * [4\.3\.1　while语句　64](#431while%E8%AF%AD%E5%8F%A564)
    * [4\.3\.2　do\-while语句　68](#432do-while%E8%AF%AD%E5%8F%A568)
  * [4\.4　循环的中途退出　69](#44%E5%BE%AA%E7%8E%AF%E7%9A%84%E4%B8%AD%E9%80%94%E9%80%80%E5%87%BA69)
  * [\*4\.5　枚举法　70](#45%E6%9E%9A%E4%B8%BE%E6%B3%9570)
  * [\*4\.6　贪婪法　73](#46%E8%B4%AA%E5%A9%AA%E6%B3%9573)
  * [4\.7　编程规范及常见错误　75](#47%E7%BC%96%E7%A8%8B%E8%A7%84%E8%8C%83%E5%8F%8A%E5%B8%B8%E8%A7%81%E9%94%99%E8%AF%AF75)
  * [4\.8　小结　75](#48%E5%B0%8F%E7%BB%9375)
  * [4\.9　习题　75](#49%E4%B9%A0%E9%A2%9875)

---

# 第4章　循环程序设计　56
## 4.1　计数循环　56
### 4.1.1　for语句　56

**代码清单4-1　计算10个账户利息的程序**

```cpp
//文件名：4-1.cpp
//计算10个账户利息的程序
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
	const double rate1Year = 0.025, rate2Year = 0.028, currentRate = 0.012;
	double balance, interest;
	int startDate, endDate, type, i;

	for (i = 0; i < 10; ++i) {
		cout << "请输入存款类型（1：一年期， 2：两年期， 0：活期）：";
		cin >> type;
		cout << "请输入存款金额：";
		cin >> balance;
		cout << "请输入起始日期：";
		cin >> startDate;
		cout << "请输入终止日期：";
		cin >> endDate;

		switch (type) {
			case 0: interest = pow( 1 + currentRate, endDate - startDate) * balance - balance;
				break;
			case 1: interest = pow( 1 + rate1Year, endDate - startDate) * balance - balance; break;
			case 2: interest = pow( 1 + rate2Year, endDate - startDate) * balance - balance; break;
		}

		cout << balance << " 元存 " << endDate - startDate << " 年共得利息 "
			 << interest << "元" << endl;
	}

	return 0;
}
```

**代码清单4-2　统计考试分数的程序**

```cpp
//文件名：4-2.cpp
//统计考试分数中的最高分，最低分和平均分
#include<iostream>
using namespace std;

int main()
{
	int value, total, max, min, numOfStudent;//value存放当前输入数据

	//变量的初始化
	total = 0;
	max = 0;
	min = 100;

	cout << "请输入学生人数：";
	cin >> numOfStudent;

	for (int i = 1; i <= numOfStudent; ++i) {      // 控制处理n个学生的信息
		cout << "\n请输入第" << i << "个人的成绩：";
		cin >> value;
		total += value;
		if (value > max) max = value;
		if (value < min) min = value;
	}

	cout << "\n最高分：" << max << endl;
	cout << "最低分：" << min << endl;
	cout << "平均分：" << total / numOfStudent << endl;

	return 0;
}
```

**代码清单4-3　输出字母A- Z的内码**

```cpp
//文件名：4-3.cpp
//输出字母A- Z的内码
#include<iostream>
using namespace std;

int main()
{
	char ch;

	for (ch = 'A' ; ch <= 'Z'; ++ch)
		cout << ch << '(' << int(ch) << ')' << "  ";

	return 0;
}
```

**代码清单4-4　计算1到100之间的素数和**

```cpp
//文件名：4-4.cpp
//计算1到100之间的素数和
#include<iostream>
using namespace std;

int main()
{
	int num, k, count, sum = 2;              // 2肯定是素数，所以sum初值为2

	for (num = 3; num <= 100; num += 2) {    //检查3到100 之间的每个奇数是否为素数
		count = 0;
		for ( k = 1; k <= num; k += 2 )        //检查小于num的所有奇数
			if (num % k == 0) ++count;
		if (count == 2) sum += num;
	}

	cout << "1到100的素数和是：" << sum << endl;

	return 0;
}
```

**代码清单4-5　求输入整数的最大因子**

```cpp
//文件名：4-5.cpp
//求输入整数的最大因子
#include<iostream>
using namespace std;

int main()
{
	int num, fac;

	cout << "请输入一个整数：";
	cin >> num;

	for (fac = num / 2; num % fac != 0; --fac);

	cout << num << "的最大因子是：" << fac << endl;

	return 0;
}
```
### 4.1.2　for语句的进一步讨论　61
### 4.1.3　for循环的嵌套　61

**代码清单4-6　打印九九乘法表的程序**

```cpp
//文件名：4-6.cpp
//打印九九乘法表
#include<iostream>
using namespace std;

int main()
{
	int i, j;

	for (i = 1; i <= 9; ++i) {
		for (j = 1; j <= 9; ++j)
			cout << i *j << '\t';
		cout << endl;
	}

	return 0;
}
```
### *4.1.4　C++11的扩展　62
## 4.2　break和continue语句　62

**代码清单4-7　检查输入是否为素数的程序**

```cpp
//文件名：4-7.cpp
//检查输入是否为素数的程序
#include <iostream>
using namespace std;

int main()
{
	int num, k;

	cout << "请输入要检测的数：";
	cin >> num;

	if (num == 2) {                     // 2是素数
		cout << num << "是素数\n";
		return 0;
	}
	if(num % 2 == 0) {                   // 2以外的偶数不是素数
		cout << num << "不是素数\n";
		return 0;
	}

	for (k = 3; k < num; k += 2)
		if (num  % k == 0) break;

	if (k < num) cout << num << "不是素数\n";     // 由break跳出循环
	else cout << num << "是素数\n";               // 正常结束循环

	return 0;
}
```

**代码清单4-8　输出A、B、C的全排列**

```cpp
//文件名：4-8.cpp
//输出A、B、C的全排列
#include <iostream>
using namespace std;

int main()
{
	char ch1, ch2, ch3;

	for (ch1 = 'A'; ch1 <= 'C'; ++ch1)              //  第一个位置的值
		for (ch2 = 'A'; ch2 <= 'C'; ++ch2)          // 第二个位置的值
			if (ch2 == ch1) continue;               // 第一个位置的值和第二个位置的值不能相同
			else for (ch3 = 'A'; ch3 <= 'C'; ++ch3) // 第三个位置的值
					if (ch3 == ch1 || ch3 == ch2)
						continue;     // 第三个位置的值和第一、二个位置的值不能相同
					else cout << ch1 << ch2 << ch3 << '\t'; // 输出一个合法的排列

	return 0;
}
```
## 4.3　基于哨兵的循环　64
### 4.3.1　while语句　64

**代码清单4-9　统计分数的程序**

```cpp
//文件名：4-9.cpp
//统计考试成绩中的最高分，最低分和平均分
#include<iostream>
using namespace std;

int main()
{
	int value, total, max, min, noOfInput;

	total = 0;                 //总分
	max = 0;
	min = 100;
	noOfInput = 0;             //人数

	cout << "请输入第1位学生的成绩：";
	cin >> value;
	while (value != -1) {
		++noOfInput;
		total += value;
		if (value > max) max = value;
		if (value < min) min = value;
		cout << "\n请输入第" << noOfInput + 1 << "位学生的成绩：";
		cin >> value;
	}

	cout << "\n最高分：" << max << endl;
	cout << "最低分：" << min << endl;
	cout << "平均分：" << total / noOfInput << endl;

	return 0;
}
```

**代码清单4-10　计算exp(x)的程序**

```cpp
//文件名：4-10.cpp
//计算ex
#include <iostream>
using namespace std;

int main()
{
	double ex, x, item;//ex存储ex的值，item保存当前项的值
	int i;

	cout << "请输入x：";
	cin >> x;

	ex = 0;
	item = 1;
	i = 0;

	while (item > 1e-6) {
		ex += item;
		++i;
		item = item * x / i;
	}

	cout << "e的" << x << "次方等于：" << ex << endl;

	return 0;
}
```

**代码清单  4-11  统计句子中各种字符的出现次数**

```cpp
//文件名：4-11.cpp
//统计句子中各种字符出现的次数
#include <iostream>
using namespace std;

int main()
{
	char ch;
	int numVowel = 0, numCons = 0, numSpace = 0, numDigit = 0, numOther = 0;

	cout << "请输入句子：";
	cin.get(ch);                               // 读入一个字符
	while (ch != '.') {                        //  处理每个字符
		if (ch >= 'A' && ch <= 'Z' ) ch = ch - 'A' + 'a';   // 大写字母转成小写字母
		if (ch >= 'a' && ch <= 'z')
			if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') ++numVowel;
			else ++numCons;
		else if (ch == ' ') ++numSpace;
		else if (ch >= '0' && ch <= '9') ++numDigit;
		else ++numOther;
		cin.get(ch);                   // 读入一个字符
	}

	cout << "元音字母数：" << numVowel << endl;
	cout << "辅音字母数：" << numCons << endl;
	cout << "空格数：" << numSpace << endl;
	cout << "数字字符数：" << numDigit << endl;
	cout << "其他字符数：" << numOther << endl;

	return 0;
}
```

### 4.3.2　do-while语句　68

**代码清单4-12　求方程的根**

```cpp
//文件名：4-12.cpp
//求方程的根
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
	double x, x1 = -1, x2 = 1, f2, f1, f, epsilon;

	cout << "请输入精度： ";
	cin >> epsilon;

	do {
		f1 = x1 * x1 * x1 + 2 * x1 * x1 + 5 * x1 - 1;     // 计算f(x1)
		f2 = x2 * x2 * x2 + 2 * x2 * x2 + 5 * x2 - 1;     // 计算f(x2)
		x = (x1 * f2 - x2 * f1) / (f2 - f1);  // 计算(x1, f(x1))和(x2, f(x2))的弦交与x轴的交点
		f = x * x * x + 2 * x * x + 5 * x - 1;
		if (f * f1 > 0) x1 = x;  else x2 = x;             // 修正区间
	} while (fabs(f) > epsilon);

	cout << "方程的根是：" << x << endl;

	return 0;
}
```
## 4.4　循环的中途退出　69
## *4.5　枚举法　70

**代码清单  4-13  求A、B、C、D、E的值（解1）**

```cpp
//文件名：4-13.cpp
//求解ABCD×E=DCBA
#include <iostream>
using namespace std;

int main()
{
	int A, B, C, D, E, num1, num2;

	for (A = 1; A <= 9; ++A)
		for (B = 0; B <= 9; ++B) {
			if (A == B) continue;                                 // A、B不能相等
			for (C = 0; C <= 9; ++C) {
				if (C == A || C == B) continue;                   // C不能等于A，也不能等于B
				for (D = 1; D <= 9; ++D) {
					if (D == A || D == B || D == C) continue;     // D不能等于A、B、C
					for (E = 2; E <= 9; ++E) {
						if (E == A || E == B || E == C || E == D) continue;//E不能等于A、B、C、D
						num1 = A * 1000 + B * 100 + C * 10 + D ;  // 构成数字ABCD
						num2 = D * 1000 + C * 100 + B * 10 + A;   // 构成数字DCBA
						if (num1 * E == num2 )
							cout << num1 << '*' << E << '=' << num2 << endl;
					}
				}
			}
		}

	return 0;
}

```

**代码清单  4-14  求A、B、C、D、E的值（解2）**

```cpp
//文件名：4-14.cpp
//求解ABCD×E=DCBA
#include <iostream>
using namespace std;

int main()
{
	int num1, num2, A, B, C, D, E;

	for (num1 = 1023; num1 <= 9876; ++num1) {     // 枚举每个可能的4位数
		A = num1 / 1000;                          // 取出每一位数字A、B、C、D
		B = num1 % 1000 / 100;
		C = num1 % 100 / 10;
		D = num1 % 10;
		if (D == 0 || A == B || A == C || A == D || B == C || B == D || C == D) continue;
		num2 = D * 1000 + C * 100 + B * 10 + A;   //  构造num2
		for (E = 2; E <= 9; ++E) {                //  检查每个可能的E
			if (E == A || E == B || E == C || E == D) continue; // E不能等于A、B、C、D
			if (num1 * E == num2 )
				cout << num1 << '*' << E << '=' << num2 << endl;
		}
	}

	return 0;
}
```

**代码清单4-15　阶梯问题的程序**

```cpp
//文件名：4-15.cpp
//阶梯问题

#include <iostream>
using namespace std;

int main()
{
	int n;

	for (n = 7; ; n += 7)
		if (n % 2 == 1 && n	% 3 == 2 && n % 5 == 4 && n % 6 == 5) break;

	cout << "满足条件的最短的阶梯长度是：" << n << endl;

	return 0;
}
```

**代码清单4-16　水果问题的程序**

```cpp
//文件名：4-16.cpp
//水果问题求解
#include <iostream>
using namespace std;

int main()
{
	int  mellon, apple, orange; 	                   //分别表示西瓜数、苹果数和橘子数

	for (mellon = 1; mellon < 15; ++mellon) {          //对每种可能的西瓜数
		for (apple = 1; apple < (150 - 10 * mellon); ++apple) {  //当西瓜数给定后可能的苹果数
			orange = 150 - 10 * mellon - 3 * apple; //剩下的钱全买了橘子
			if (mellon + apple + orange == 100) { 	   //3种水果数之和是否为100
				cout << "mellon:" << mellon << ' ';
				cout << "apple:" << apple << ' ';
				cout << "orange:" << orange << endl;
			}
		}
	}

	return 0;
}
```
## *4.6　贪婪法　73

**代码清单4-17　贪婪法解硬币找零问题的程序**

```cpp
//文件名：4-17.cpp
//贪婪法解硬币找零问题
#include<iostream>
using namespace std;

#define ONEFEN  1
#define TWOFEN  2
#define FIVEFEN  5
#define ONEJIAO  10

int main()
{
	int money;
	int onefen = 0, twofen = 0, fivefen = 0, onejiao = 0;

	cout << "输入要找零的钱（以分为单位）：";  cin >> money;

	//不断尝试每一种硬币
	if (money >= ONEJIAO) {
		onejiao = money / ONEJIAO;
		money %= ONEJIAO;
	}
	if (money >= FIVEFEN) {
		fivefen = 1;
		money -= FIVEFEN;
	}
	if (money >= TWOFEN) {
		twofen = money / TWOFEN;
		money %= TWOFEN;
	}
	if (money >= ONEFEN) onefen = 1;

	//输出结果
	cout << "1角硬币数：" << onejiao << endl;
	cout << "5分硬币数：" << fivefen << endl;
	cout << "2分硬币数：" << twofen << endl;
	cout << "1分硬币数：" << onefen << endl;

	return 0;
}
```

**代码清单4-18　找出由5、6、2、9、4、1的3个数字组成的最大的3位数的程序**

```cpp
//文件名：4-18.cpp
//找出由5、6、2、9、4、1的3个数字组成的最大的3位数的程序
#include <iostream>
using namespace std;

int main()
{
	int num = 0, max = 10, current;

	for (int digit = 100; digit > 0; digit /= 10) {
		current = 0;
		for (int n : {5, 6, 2, 4, 9, 1})
			if (n > current && n < max) current = n;
		num += digit * current;
		max = current;
	}

	cout << num << '\t';

	return 0;
}
```
## 4.7　编程规范及常见错误　75
## 4.8　小结　75
## 4.9　习题　75
