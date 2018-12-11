# 第5章 批量数据处理——数组

## 7.计算5阶行列式

**测试数据：**
```
5 3 -1 2 0
1 7 2 5 2
0 -2 3 1 0
0 -4 -1 4 0
0 2 3 5 0

行列式的值为： -1080
```

**程序：**

```cpp
// 计算5阶行列式
// 逆序数方法
#include <iostream>
using namespace std;

int main()
{
	//输入行列式A
	double A[5][5], detA = 0; //detA为行列式的值
	int row, col; //row为行，col为列
	cout << "请输入行列式A：" << '\n' << endl;
	for (row = 0; row < 5; ++row) {
		for(col = 0; col < 5; ++col) {
			cin >> A[row][col];
		}
	}
	cout << endl;
	//计算行列式
	int c1, c2, c3, c4, c5, sgn; //sgn计算逆序数
	for(c1 = 0; c1 < 5; ++c1)
		for(c2 = 0; c2 < 5; ++c2)
			if(c2 == c1) continue;
			else for(c3 = 0; c3 < 5; ++c3)
					if((c3 - c2 ) * ( c3 - c1) == 0) continue;
					else for(c4 = 0; c4 < 5; ++c4)
							if((c4 - c3 ) * ( c4 - c2 ) * ( c4 - c1) == 0)continue;
							else {
								c5 = 10 - c1 - c2 - c3 - c4; //0+1+2+3+4=10
								if((c1 - c4) * (c1 - c3) * (c1 - c2) * (c1 - c5) * (c2 - c3) * (c2 - c4) * (c2 - c5) * (c3 - c4) * (c3 - c5) * (c4 - c5) > 0) sgn = 1;
								else sgn = -1;
								detA += sgn * (A[0][c1] * A[1][c2] * A[2][c3] * A[3][c4] * A[4][c5]);
							}
	cout << "行列式的值 |A| = " << detA << endl;
	return 0;
}
```


## 9.统计文章的字符数

**测试数据：**

```
ACC9:B0F0:A0F5:3ABA:2002:2DD1:9827:F046
ca0e29c5-3d89-45f1-9d16-9c33bb603f48
2013-10-28T05:45:57+08:00
219.58.229.12
16:58:36
#122c15
2024-04-19
VMKzYsqlH
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua.

英文字母数:138
数字字符数:87
空格数:17
其他字符数:28
```

**程序：**

```cpp
#include <iostream>
using namespace std;

int main()
{
	const int ROW = 10, LEN = 80;
	char article[ROW][LEN + 1];
	int i, j, alph = 0, digit = 0, space = 0, other = 0;

	cout << "请输入" << ROW << "行文字，每行以回车结束，每行最多" << LEN << "个字符,空行用回车代替，每输入一行之后回车\n" << endl;


	for(i = 0; i < ROW; ++i) {
		cout << "请输入第" << i + 1 << "行：";
		cin.getline(article[i], LEN + 1);
	}

	cout << "\n你输入的是：\n" << endl;
	for(i = 0; i < ROW; ++i) {         //回显输入的文章
		for(j = 0; article[i][j] != '\0'; ++j) {
			cout << article[i][j];
		}
		cout << endl;
	}

	for(i = 0; i < ROW; ++i) {         //统计过程
		for(j = 0; article[i][j] != '\0'; ++j) {
			if(article[i][j] == ' ') ++space;
			else if(article[i][j] >= '0' && article[i][j] <= '9') ++digit;
			else if((article[i][j] >= 'a' && article[i][j] <= 'z') || (article[i][j] >= 'A' && article[i][j] <= 'Z')) ++alph;
			else ++other;
		}
	}
	cout << "\n字符统计如下：\n\n英文字母数:" << alph << "\n数字字符数:" << digit << "\n空格数:" << space << "\n其他字符数:" << other << endl;
}
```

## 11.井字游戏

```cpp
#include <iostream>
using namespace std;

int main()
{
	int board[3][3] = {0};    //初始化棋盘
	int i, j, k, judgeRow, judgeCol, judgeDig1, judgeDig2, player = 1, row, col, won = 0;
	cout << "player1使用[O]显示，player2使用[X]显示，" << '\n' << "输入的行列之间用空格分隔。" << endl;
	for(k = 0; k < 9; ++k) {
		//输入player的选择
		do {
			for(i = 0; i < 3; ++i) {  //显示当前的状态
				for(j = 0; j < 3; ++j) {
					switch(board[i][j]) {
						case 1: cout << "[O]"; break; //选手1使用[O]，对应1
						case -1: cout << "[X]"; break; //选手2使用[X]，对应-1
						default: cout << "[ ]";
					}
				}
				cout << endl;
			}
			cout << "请输入player" << player << "的选择：";
			cin >> row >> col;
			if(row < 1 || row > 3 || col < 1 || col > 3 || board[row - 1][col - 1])
				cout << "输入有误，请重新输入" << endl;
			else break;
		} while(true);

		//根据选择修改棋盘的状态
		board[row - 1][col - 1] = (player == 1 ? 1 : -1);
		for(i = 0; i < 3; ++i) {  //判断是否有玩家赢了
			judgeRow = board[i][0] + board[i][1] + board[i][2];
			judgeCol = board[0][i] + board[1][i] + board[2][i];
			if(judgeRow == 3 || judgeCol == 3) {
				won = 1; break;
			}
			if(judgeRow == -3 || judgeCol == -3) {
				won = 2; break;
			}
		}
		if(won != 0) break;   //如果有玩家赢了，则不再判断两个斜线部分
		judgeDig1 = board[0][0] + board[1][1] + board[2][2];
		judgeDig2 = board[0][2] + board[1][1] + board[2][0];
		if(judgeDig1 == 3 || judgeDig2 == 3) {
			won = 1; break;
		}
		if(judgeDig1 == -3 || judgeDig2 == -3) {
			won = 2; break;
		}
		player = player % 2 + 1;     //交换玩家
	}
	//显示玩家获胜时的棋盘状态
	for(i = 0; i < 3; ++i) {
		for(j = 0; j < 3; ++j) {
			switch(board[i][j]) {
				case 1: cout << "[O]"; break;
				case -1: cout << "[X]"; break;
				default : cout << "[ ]";
			}
		}
		cout << endl;
	}
	switch(won) {
		case 1: cout << "玩家1赢了，游戏结束！" << endl; break;
		case 2: cout << "玩家2赢了，游戏结束！" << endl; break;
		default: cout << "平局！" << endl;
	}
	return 0;
}
```

## 12.检验输入ISBN号是否合法

**测试数据：**
```
合法：
0078818095
9787115183095
非法：
1234567890
13abc46789
```

**程序：**

```cpp
//12.ISBN号的鉴定
#include <iostream>
#include <cstring>
using namespace std;

int main()
{
	char isbn[14];
	int i, sum = 0;
	int check[13] = {1, 3, 1, 3, 1, 3, 1, 3, 1, 3, 1, 3, 1};

	cout << "请输入ISBN号：";
	cin >> isbn;

	if(strlen(isbn) != 10 && strlen(isbn) != 13) { //检查长度，排除非法的ISBN号
		cout << "非法的ISBN！" << endl;
		return 0;
	}
	if(strlen(isbn) == 10) {
		for(i = 0; i < 10; ++i) {
			if(isbn[i] < '0' || isbn[i] > '9') { //检查ISBN号中是否包含非数字
				cout << "非法的ISBN！" << endl;
				return 0;
			}
			sum += (10 - i) * (isbn[i] - '0');
		}
		if(sum % 11 == 0)
			cout << "合法的ISBN" << endl;
		else cout << "非法的ISBN！" << endl;
	} else {                                    //13位的ISBN号的检验
		for(i = 0; i < 13; ++i) {
			if(isbn[i] < '0' || isbn[i] > '9') { //检查ISBN号中是否包含非数字
				cout << "非法的ISBN！" << endl;
				return 0;
			}
			sum += check[i] * (isbn[i] - '0');
		}
		if(sum % 10 == 0)
			cout << "合法的ISBN" << endl;
		else cout << "非法的ISBN！" << endl;
	}
	return 0;
}
```
