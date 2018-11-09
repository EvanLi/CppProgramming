# 第5章　批量数据处理——数组　79
## 5.1　一维数组　79
### 5.1.1　一维数组的定义　79
### 5.1.2　一维数组元素的引用　80

**代码清单5-1　数组的输入/输出**

```
//文件名：5-1.cpp
//数组输入/输出示例
#include <iostream>
using namespace std;

int main()
{
    int a[10], i;

    cout << "请输入10个整型数：\n";
    for (i = 0; i < 10; ++i)
        cin >> a[i];

    cout << "\n数组的内容为：\n";
    for (i = 0; i < 10; ++i)
        cout << a[i] << '\t';

    return 0;
}
```
### 5.1.3　一维数组的内存映像　81
### 5.1.4　一维数组的应用　81

**代码清单5-2　统计某次考试的平均成绩和均方差**

```
//文件名：5-2.cpp
//统计某次考试的平均成绩和均方差
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
    const int MAX = 100;        //定义一个班级中最多的学生数
    int score[MAX], num = 0;    // num：某次考试的真实人数
    double average = 0, variance = 0;

    cout << "请输入成绩（-1表示结束）：\n";
    for (num = 0; num < MAX; ++num) {     // 输入并统计成绩总和
        cin >> score[num];
        if (score[num] == -1) break;
        average += score[num];
    }

    average = average / num;             //计算平均成绩

    for (int i = 0; i < num ; ++i)      //计算均方差
        variance += (average - score[i]) * (average - score[i]);
    variance = sqrt(variance / num);

    cout << "平均分是：" << average << "\n均方差是：" <<  variance <<  endl;

    return 0;
}

```

**代码清单5-3　计算两个十维向量的数量积**

```
//文件名：5-3.cpp
//计算两个十维向量的数量积
#include <iostream>
using namespace std;

int main()
{
    const int MAX = 10;
    double a[MAX], b[MAX], result = 0;
    int i;

    // 输入向量a
    cout << "请输入向量a的十个分量：";
    for (i = 0; i < MAX; ++i)
        cin >> a[i];

    // 输入向量b
    cout << "请输入向量b的十个分量：";
    for (i = 0; i < MAX; ++i)
        cin >> b[i];

    // 计算a，b的数量积
    for (i = 0; i < MAX; ++i)
        result += a[i] * b[i];

    cout << "a，b的数量积是：" << result << endl;

    return 0;
}
```
### *5.1.5　C++11的扩展　83
## 5.2　查找　84
### 5.2.1　顺序查找　84

**代码清单5-4　顺序查找**

```
//文件名：5-4.cpp
//顺序查找
#include <iostream>
using namespace std;

int main()
{
    int  k, x;
    int array[ ] = { 2, 3, 1, 7, 5, 8, 9, 0, 4, 6};

    cout << "请输入要查找的数据：";
    cin >> x;

    for (k = 0; k < 10; ++k)
        if (x == array[k])  break;

    if (k == 10) cout << "没有找到";
    else cout << x << "的存储位置为：" << k;
    return 0;
}
```

### 5.2.2　二分查找　85

**代码清单5-5　二分查找程序**

```
//文件名：5-5.cpp
//二分查找
#include <iostream>
using namespace std;

int main()
{
    int low, high, mid, x;
    int array[ ] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};

    cout << "请输入要查找的数据：";  cin >> x;

    low = 0;  high = 9;
    while ( low <= high ) {           // 查找区间存在
        mid = ( low + high ) / 2;       // 计算中间位置
        if ( x == array[mid] )  break;   // 找到
        if ( x < array[mid]) high = mid - 1; else low = mid + 1; // 修改查找区间
    }

    if (low > high) cout << "没有找到" << endl;
    else cout << x << "的位置是：" << mid << endl;

    return 0;
}
```
## 5.3　排序　87
### 5.3.1　直接选择排序法　87

**代码清单5-6　直接选择排序的程序**

```
//文件名：5-6.cpp
//直接选择排序
#include <iostream>
using namespace std;

int main( )
{
    int lh, rh, k, tmp;
    int array[ ] = {2, 5, 1, 9, 10, 0, 4, 8, 7, 6};

    for (lh = 0; lh < 10; ++lh)   {         // 依次将正确的元素放入array[lh]
        rh = lh;
        for (k = lh; k < 10; ++k)           // 找出从lh到最后一个元素中的最小元素的下标rh
            if ( array[k] < array[rh] )   rh = k;
        tmp = array[lh];                    //交换lh和rh的值
        array[lh] = array[rh];
        array[rh] = tmp;
    }

    for (lh = 0; lh < 10; ++lh)  cout << array[lh] << ' ';

    return 0;
}
```

### 5.3.2　冒泡排序法　89

**代码清单5-7　整型数的冒泡排序的程序**

```
//文件名：5-7.cpp
//冒泡排序
#include <iostream>
using namespace std;

int main()
{
    int a[ ] = { 0, 3, 5, 1, 8, 7, 9, 4, 2, 10, 6};
    int i, j, tmp;
    bool flag; //记录一趟起泡中有没有发生过交换

    for (i = 1; i < 11; ++i) { // 控制10次起泡
        flag = false;
        for (j = 0; j < 11 - i; ++j) // 一次起泡过程
            if (a[j + 1] < a[j]) {
                tmp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = tmp;
                flag = true;
            }
        if (!flag) break; //一趟起泡中没有发生交换，排序提前结束
    }

    cout << endl;
    for (i = 0; i < 11; ++i)  cout << a[i] << ' ';

    return 0;
}
```

## 5.4　二维数组　90
### 5.4.1　二维数组的定义　91
### 5.4.2　二维数组元素的引用　91
### 5.4.3　二维数组的内存映像　92
### 5.4.4　二维数组的应用　92

**代码清单5-8　矩阵乘法的程序**

```
//文件名：5-8.cpp
//矩阵乘法
#include <iostream>
using namespace std;
#define MAX_SIZE 10  //矩阵的最大规模

int main()
{
    int a[MAX_SIZE][MAX_SIZE], b[MAX_SIZE][MAX_SIZE], c[MAX_SIZE][MAX_SIZE];
    int i, j, k, NumOfRowA, NumOfColA, NumOfColB;

    //输入A和B的大小
    cout << "\n输入A的行数、列数和B的列数：";
    cin >> NumOfRowA  >> NumOfColA >> NumOfColB;

    //输入A
    cout << "\n输入A:\n";
    for (i = 0; i < NumOfRowA; ++i)
        for (j = 0; j < NumOfColA; ++j)  {
            cout << "a[" << i << "][" << j << "] = ";
            cin >> a[i][j];
        }

    //输入B
    cout << "\n输入B:\n";
    for (i = 0; i < NumOfColA; ++i)
        for (j = 0; j < NumOfColB; ++j)    {
            cout << "b[" << i << "][" << j << "] = ";
            cin >> b[i][j];
        }

    //计算A×B
    for (i = 0; i < NumOfRowA; ++i)
        for (j = 0; j < NumOfColB; ++j) {
            c[i][j] = 0;
            for (k = 0; k < NumOfColA; ++k)   c[i][j] += a[i][k] * b[k][j];
        }

    //输出C
    cout << "\n输出C:";
    for (i = 0; i < NumOfRowA; ++i) {
        cout << endl;
        for (j = 0; j < NumOfColB; ++j)  cout << c[i][j] << '\t';
    }

    return 0;
}
```

**代码清单5-9　打印N阶魔阵的程序**

```
//文件名：5-9.cpp
//打印N阶魔阵
#include <iostream>
using namespace std;

#define MAX 15 //最高为打印15阶魔阵

int main()
{
    int magic[MAX][MAX] = {0}; //将magic每个元素设为0
    int row, col, count, scale;

    //输入阶数scale
    cout << "input scale\n";
    cin >> scale;

    //生成魔阵
    row = 0; col = (scale - 1) / 2; magic[row][col] = 1;
    for (count = 2; count <= scale * scale; count++) {
        if (magic[(row - 1 + scale) % scale][(col + 1) % scale] == 0) {
            row = ( row - 1 + scale ) % scale;
            col = ( col + 1 ) % scale;
        } else  row = ( row + 1 ) % scale;
        magic[row][col] = count;
    }

    //输出
    for (row = 0; row < scale; row++) {
        for (col = 0; col < scale; col++)
            cout << magic[row][col] << '\t';
        cout << endl;
    }

    return 0;
}
```

**代码清单5-10　求解三元一次方程组的程序**

```
//文件名：5-10.cpp
//求解三元一次方程组的程序
#include<iostream>
using namespace std;

int main()
{
    double a[3][3], b[3], result[3], detA, detB, tmp[3]; // a系数矩阵，b常数项，result存放根
    int i, j;

    for (i = 0; i < 3; ++i) {
        cout << "请输入第" << i + 1 << "个方程的3个系数和常数项：";
        cin >> a[i][0] >> a[i][1] >> a[i][2] >> b[i];
    }

    detA = a[0][0] * a[1][1] * a[2][2] + a[0][1] * a[1][2] * a[2][0] + a[0][2] * a[1][0] * a[2][1]
           - a[0][2] * a[1][1] * a[2][0] - a[0][1] * a[1][0] * a[2][2] - a[0][0] * a[1][2] * a[2][1];

    for (i = 0; i < 3; ++i) {    // 求解3个根
        for (j = 0; j < 3; ++j) {  // 用b替换a矩阵的第i列
            tmp[j] = a[j][i];
            a[j][i] = b[j];
        }
        detB = a[0][0] * a[1][1] * a[2][2] + a[0][1] * a[1][2] * a[2][0] + a[0][2] * a[1][0] * a[2][1]
               - a[0][2] * a[1][1] * a[2][0] - a[0][1] * a[1][0] * a[2][2] - a[0][0] * a[1][2] * a[2][1];
        for (j = 0; j < 3; ++j) a[j][i] = tmp[j];  // 还原a矩阵
        result[i] = detB / detA;                   // 计算第i个根
    }

    cout << "x=" << result[0] << ",y=" << result[1] << ",z=" << result[2] << endl;

    return 0;
}
```
## 5.5　字符串　96
### 5.5.1　字符串的存储及初始化　96
### 5.5.2　字符串的输入/输出　97
### 5.5.3　字符串处理函数　97
### 5.5.4　字符串的应用　98

**代码清单5-11　统计单词数的程序**

```
//文件名：5-11.cpp
//统计一段文字中的单词个数
#include <iostream>
using namespace std;

int main()
{
    const int LEN = 80;
    char sentence[LEN + 1], prev = ' ';   //prev 表示当前字符的前一字符
    int i, num = 0;

    cin.getline(sentence, LEN + 1);

    for (i = 0; sentence[i] != '\0'; ++i) {
        if (prev == ' ' && sentence[i] != ' ') ++num;
        prev = sentence[i];
    }

    cout << "单词个数为：" << num << endl;

    return 0;
}
```

**代码清单5-12　计算输入数据之和**

```
//文件名：5-12.cpp
//计算输入数据之和
#include <iostream>
using namespace std;

int main()
{
    char str[81];
    int sum = 0, data, i = 0, flag;   // flag记录当前正在处理的整数的基数

    cin.getline(str, 81);
    while (str[i] == ' ') ++i;          // 跳过前置的空格

    while (str[i] != '\0') {              // 取出一个整数加入总和
        // 区分基数
        if (str[i] != '0') flag = 10;       // 十进制
        else {
            if (str[i + 1] == 'x' || str[i + 1] == 'X') { // 十六进制
                flag = 16;
                i += 2;
            } else {
                flag = 8;    // 八进制
                ++i;
            }
        }

        // 将字符串表示的整数转换成整型数
        data = 0;
        switch (flag) {
            case 10: while (str[i] != ' ' && str[i] != '\0')
                    data = data * 10 + str[i++] - '0';
                break;
            case 8: while (str[i] != ' ' && str[i] != '\0')
                    data = data * 8 + str[i++] - '0';
                break;
            case 16: while (str[i] != ' ' && str[i] != '\0') {
                    data = data * 16;
                    if (str[i] >= 'A' && str[i] <= 'F') data += str[i++] - 'A' + 10;
                    else if (str[i] >= 'a' && str[i] <= 'f') data += str[i++] - 'a' + 10;
                    else data += str[i++] - '0';
                }
        }
        sum += data;
        while (str[i] == ' ') ++i;           // 跳过空格
    }

    cout << sum << endl;

    return 0;
}
```
## 5.6　编程规范及常见错误　100
## 5.7　小结　101
## 5.8　习题　101
