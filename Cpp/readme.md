- [Environment set up](#environment-set-up)
- [Basic](#basic)
  * [hello world](#hello-world)
  * [Variables and constants](#variables-and-constants)
  * [Data types](#data-types)
  * [Operator](#operator)
  * [Program flow structure](#program-flow-structure)
    + [Sequential structure](#sequential-structure)
      - [if](#if)
      - [ternary operator](#ternary-operator)
      - [switch](#switch)
    + [cycle structure](#cycle-structure)
      - [while](#while)
      - [do...while](#dowhile)
      - [for](#for)
      - [nest-loop](#nest-loop)
    + [jump statement](#jump-statement)
      - [break](#break)
      - [continue](#continue)
      - [goto](#goto)
  * [array](#array)
    + [1-D array](#1-d-array)
    + [2-D array](#2-d-array)
  * [function](#function)
  * [Pointer](#pointer)
  * [struct](#struct)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>




# Environment set up

 1. 下载软件： 百度`visual studio`,下载**community**版本
 2. 安装软件：选`使用c++的桌面开发`，其他可选可不选.
 3. 创建第一个项目：`新建项目`-->`Visual c++`-->`空项目`

---
# Basic
## hello world

 - 创建项目：`新建项目`->`Visaul C++`->`空项目`->`项目名称`->`位置`->`确定`
 - 创建文件：右击`源文件`->`添加`->`新建项`->`起名`->`添加`
 - 书写代码
 
```cpp
#include <iostream>
using namespace std;

/*
the first c++ code
*/

int main()
{
	cout << "hello world" << endl;   //在屏幕中输出“hello world”
	system("pause");
	return 0;
}
```

## Variables and constants
变量可以帮忙更好地管理内存空间；常量用于记录程序中不可更改的数据
```cpp
//宏常量
#define day 7

//变量创建语法：  数据类型 变量名 = 变量初始值
int a = 10;  //a是变量

// const修饰的变量
const int month = 12;
```

## Data types
c++规定在创建一个变量或常量时，必须指定相应数据类型，否则无法为变量分配内存

```cpp
//整型
// short < int <= long <= long long
short num1 =10;  //短整型，占用空间2字节，取值范围(-2^15~2^15-1)
cout << "short占用内存空间为:" << sizeof(short) << endl;   //short占用内存空间为:2
int num2 = 10;  //整型，占用空间4字节，取值范围(-2^31~2^31-1)
long num3 = 10;  //长整型，window为4字节，linux为4字节（32位）或8字节（64位）(-2^31~2^31-1)
long long num4 =10; //长长整型，8字节，（-2^63~2^63-1）

// 实型（浮点型） 用于表示小数
float f1 = 3.14f ; //单精度，sizeof(float)=4
double d1 = 3.14; //双精度，sizeof(double)=8
//科学计数法
float f2 = 3e2 ; // 3 * 10 ^2
float f3 = 3e-2 ; // 3* 0.1 ^2

//字符型  用于显示单个字符
char ch = 'a';
cout << "char字符型变量所占内存：" << sizeof(char) << endl;   // char字符型变量所占内存：1
// 注意1：用单引号将字符括起来
// 注意2：单引号内只能有1个字符，不可是字符串
// 字符型变量并不是把字符本身放在内存中存储，而是将对应ASCII编码放入存储单元
cout << (int)ch << endl; // 强制把ch变成整型    打印结果:97
// a -97
// A- 65

//转义字符 （用于表示一些不能显示出来的ASCII字符）
cout << "hello world\n" ;  // 换行符 \n
cout << "\\" << endl; // 想输出反斜杠，就要写2个反斜杠。
// 水平制表符\t    下面的helloworld都是对齐的，实现整齐输出
cout << "aaa\thelloworld" << endl;   //自动把aaa不足8字符的位置用空格填充
cout << "aaaa\thelloworld" << endl; 
cout << "aa\thelloworld" << endl;   

//字符串型
//C风格字符串  char 变量名[]="字符串值"
char str1[] = "hello world";
//C++风格字符串   string 变量名 = "字符串值"
#include <string>  //必须加这个头文件
string str2 = "hello world";

//布尔类型
bool flag = true; //true代表真
cout << flag <<endl; //1
flag = false ; //false代表假
cout << flag <<endl; //0
cout << "bool类型所占内存空间：" << sizeof(bool) << endl;  //1

//数据的输入
double d = 0;
cout << "请输入浮点型变量：" << endl;
cin >> d ;
cout << d << endl;
```

## Operator
- 算术运算符：处理四则运算
- 赋值运算符：将表达式的值赋给变量
- 比较运算符：用于表达式的比较，并返回一个真值或假值
- 逻辑运算符：用于根据表达式的值返回真值或假值

```cpp
// 算术运算符
// 加减乘除
int a1 = 10;
int b1 = 3;
cout << a1 + b1 << endl; //13
cout << a1 - b1 << endl; //7
cout << a1 * b1 << endl; //30
cout << a1 / b1 << endl; //3    int/int= int
double d1 = 0.5;
double d2 = 0.22;
cout << d1 / d2 <<endl;  //2.27273
// 取模 (求余数)  （！！两个小数不能做取模运算）
int a1 = 10;
int b1 = 3;
cout << a1 % b1 << endl; //1
// 递增递减 (以递增为例)
int a = 10;
++a; //让变量+1
cout << a << endl; //11
int b = 10;
b++; //让变量+1
cout << b << endl; //11
int a2 = 10;
int b2 = ++a2 *10;
cout << a2 << endl; //11
cout << b2 << endl; //110
int a3 = 10;
int b3 = a3++ * 10;
cout << a3 << endl; //11
cout << b3 << endl; //100

// 赋值运算符
// =
int a = 10;
a = 100;
cout << a << endl;  //100
// +=
a = 10;
a += 2; //a = a+2
cout << a << endl; //12
// 同理-=  *=   /=

//比较运算符 （== != > < >= <=）
int a = 10;
int b = 20;
cout << (a == b) << endl;  //0
cout << (a != b) << endl;  //1
cout << (a > b) << endl;  //0
cout << (a < b) << endl;  //1
cout << (a >= b) << endl;  //0
cout << (a <= b) << endl; //1

// 逻辑运算符  (!  &&  ||)
int a = 10;
cout << !a << endl;  //0   非a  c++中除了0都为真
cout << !!a << endl; //1
int b =10;
cout << (a && b) << endl; //1   同真为真，其余为假
int b = 0;
cout << (a || b) << endl; //1   同假为假，其余为真
```

## Program flow structure
### Sequential structure
#### if
```cpp

//单行if语句
int score = 0;
cout << "请输入一个分数：" << endl;
cin >> score ;   
cout << "您输入的分数为："  << score << endl;
if (score > 600)    //注意：此处不要加“”;“”
{
	cout << "恭喜您考上了一本大学"  << endl;
}
//多行if语句
if (score > 600)    //大于600
{
	cout << "恭喜您考上了一本大学"  << endl;
}
else   // 不大于600，执行else后大括号内容
{
	cout << "未考上一本大学" << endl;
}
// 多条件if语句
if (score > 600)
{
	cout << "恭喜您考上了一本大学"  << endl;
}
else if (score > 500)
{
	cout << "恭喜您考上了二本大学"  << endl;
}
else if (score > 400)
{
	cout << "恭喜您考上了三本大学"  << endl;
}
else
{
	cout << "未考上本科，再接再厉"  << endl;
}
// 嵌套if语句
if (score > 600)
{
	cout << "恭喜您考上了一本大学"  << endl;
	if (score > 700)
	{
		cout << "您能考入北京大学" << endl;
	}
	else if (score > 650)
	{
		cout << "您能考入清华大学" << endl;
	}
	else
	{
		cout << "您能考入人民大学" << endl;
	}
}
else if (score > 500)
{
	cout << "恭喜您考上了二本大学"  << endl;
}
else if (score > 400)
{
	cout << "恭喜您考上了三本大学"  << endl;
}
else
{
	cout << "未考上本科，再接再厉"  << endl;
}
```
#### ternary operator
语法：`表达式1 ？ 表达式2 ：表达式3`
解释： 如果表达式1为真，执行表达式2，并返回表达式2的结果；如果表达式1为假，执行表达式3，并返回表达式3的结果

```cpp
// 创建3个变量a b c
// 将a和b做比较，将变量大的值赋值给变量c
int a = 10;
int b = 20;
int c = 0;
c = (a > b ? a : b);
cout << c << endl; //20
//在c++中 三目运算符返回的是变量，可以继续赋值
(a > b ? a : b) = 100；
cout << a << endl; // 10
cout << b << endl; // 100
```
#### switch

```cpp
// 电影打分   10-9 经典   8-7 非常好  6-5一般  5以下 烂片
// 1、提示用户评分
cout << "请给电影打分" << endl;
// 2、用户打分
int score =0;
cin >> score ;
cout << "您打的分数为：" << score << endl;
// 3.根据用户输入分数提示用户结果
switch(score)
{
	case 10:
		cout << "您认为是经典电影" << endl;
		break;  // 退出当前分支
	case 9:
		cout << "您认为是经典电影" << endl;
		break;
	case 8：
		cout << "您认为是电影非常好" << endl;
		break;
	case 7：
		cout << "您认为是电影非常好" << endl;
		break;
	case 6：
		cout << "您认为是电影一般" << endl;
		break;
	case 5：
		cout << "您认为是电影一般" << endl;
		break;
	default:
		cout << "您认为是烂片" << endl;
		break：
}
```
switch缺点：判断时只能是整型或字符型，不可是一个区间；有点是结构清晰，执行效率高

### cycle structure 
#### while

```cpp
//在屏幕中打印0~9这10个数字
int num = 0 ;
while(num < 10)
{
	cout << num << endl;
	num++;
}
```

```cpp
//猜数字游戏
#include<iostream>
using namespace std;
#include <ctime>

int main() {
	// 添加随机数种子，作用是利用当前系统时间生成随机数，防止每次随机数都一样
	srand((unsigned int)time(NULL));
	//1、系统生成随机数
	int num = rand() % 100 + 1;//rand()%100生成0~99的随机数  
	cout << num << endl;
	//2、玩家猜测
	int val = 0;

	while (1)
	{
		cin >> val;
		//3、判断玩家猜测
		if (val > num)
		{
			cout << "猜测过大" << endl;
		}
		else if (val < num)
		{
			cout << "猜测过小" << endl;
		}
		else
		{
			cout << "恭喜您猜对了" << endl;
			break;  //退出当前循环
		}
	}
	system("pause");
}
```
#### do...while
与`while`的区别在于`do...while`会**先执行一次**循环语句，再判断循环条件

```cpp
int num = 0;
do
{
	cout << num << endl;
	num++;
}
while(num<10);
```
**练习案例**：水仙花数
案例描述：水仙花数指一个3位数，它的每个位上的数字的3次幂之和等于它本身
例如： 1^3^+5^3^+3^3^=153
**思路**：
- 将所有三位数进行输出（100-999）
- 在所有三位数中找到水仙花数
-- 153
-- 获取个位   `153%10=3`   对数字取模于10，可获取个位
-- 获取十位  `153/10=15`,`15%10=5`，先整除于10，得到两位数，再取模于10，得到十位
-- 获取百位  `153/100=1`  直接乘除于100，得到百位
```cpp
#include<iostream>
using namespace std;
int main() {
	int num = 100;
	do
	{
		int a = 0; //个位
		int b = 0; //十位
		int c = 0; //百位
		a = num % 10;
		b = num / 10 % 10;
		c = num / 100;
			if (a * a * a + b * b * b + c * c * c == num)   //如果是水仙花数
			{
				cout << num << endl;
			}
		num++;
	} while (num < 1000);
	system("pause");
}
```
#### for
语法：`for(起始表达式；条件表达式；末尾循环体){循环语句;}`

```cpp
//打印数字0-9
for (int i=0;i<10;i++)
{
	cout << i << endl;
}
```
练习案例：敲桌子
案例描述：从1开始数到100，如果数字个位含有7，或者数字十位含有7，或者该数字是7的倍数，我们打印敲桌子，其余数字直接打印输出。
**分析**可能是数字：
- 7的倍数  （7, 14 ,21 ,28）%7 =0
- 个位有7    （7,17,27，...）%10 = 7
- 十位有7   （70,71,72，..）/10  = 7

```cpp
#include<iostream>
using namespace std;
int main() {
	for (int i = 1; i <= 100; i++)
	{
		if (i%7==0 || i%10 ==7 || i/10 ==7)   //如果是特殊数字
		{
			cout << "敲桌子" << endl;
		}
		else
		{
			cout << i << endl;
		}

	}
	system("pause");
}
```
#### nest-loop

```cpp
//打印星图矩阵
#include<iostream>
using namespace std;
int main() {
	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j < 10; j++)
		{
			cout << "* ";
		}
		cout << endl ;
	}
	system("pause");
}
```
练习案例：乘法口诀表

```cpp
#include<iostream>
using namespace std;
int main() {
	//乘法口诀表
	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j <= i; j++)
		{
			cout << j << "*" << i << "=" << i * j << "  ";
		}
		cout << endl;
	}
	system("pause");
}
```
### jump statement
#### break
break用于跳出选择结构或循环结构，使用时机如下：
- 出现在switch条件语句中，作用是终止case并跳出switch
- 出现在循环语句中，作用是跳出当前循环语句
- 出现在嵌套循环中，跳出最近的内层循环语句

```cpp
//出现在switch语句中
cout << "请选择副本难度" <<endl;
cout << "1、普通" <<endl;
cout << "2、中等" <<endl;
cout << "3、困难" <<endl;
int select =0;
cin >> select;
switch(select)
{
case 1:
	cout << "您选择的是普通难度" << endl;
	break;  //退出switch语句
case 2:
	cout << "您选择的是中等难度" << endl;
	break;
case 3:
	cout << "您选择的是困难难度" << endl;
	break;
default:
	break;
}
```

```cpp
//出现在循环语句中
for (int i =0;i<10;i++)
{
	//如果i=5，退出循环
	if (i==5)
	{
		break;
	}
	cout << i << endl;
}
```

```cpp
//使用在嵌套循环中
#include<iostream>
using namespace std;
int main() {
	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j < 10; j++)
		{
			if (j==5)
			{
				break; //不影响外层循环
			}
			cout << "* ";
		}
		cout << endl ;
	}
	system("pause");
}
```
#### continue
作用：在循环语句中，跳过本次循环中余下未执行的语句，继续执行下一次循环

```cpp
#include<iostream>
using namespace std;
int main() {
	// continue语句
	//打印奇数
	for (int i = 0; i <= 100; i++)
	{
		if (i % 2 == 0)
		{
			continue;
		}
		cout << i << endl;
	}
	system("pause");
}
```
#### goto
无条件跳转语句
语法：`goto 标记;`
 ```cpp
cout << "1" <<endl;
goto FLAG;
cout <<"2" <<endl;
cout <<"3" <<endl;
cout <<"4" <<endl;
FLAG:
cout <<"5" <<endl;  //不打印2 3 4
```
> 不建议使用goto，容易造成程序流程混乱

## array
### 1-D array
数组是一个存放了**相同类型数据元素**的集合，数组由**连续内存位置**组成。
三种定义方式：
- 数据类型 数组名[数组长度];
- 数据类型 数组名[数组长度] = {值1, 值2,....};
- 数据类型 数组名[ ] ={值1, 值2,....};

```cpp
//第一种创建方法
int arr[5];
arr[0] = 10; //赋值   数值元素下标从0开始
cout << arr[0] << endl; //访问

//第二种创建方法
int arr2[5] = {10,20,30,40,50}; //如果没有补齐，会用0自动填充
for (int i = 0; i<5; i++)
{
	cout << arr2[i] <<endl;
}

// 第三种创建方式
int arr3[] = {90,80,70,60,50};
```

一维数组名称的用途：
- 统计整个数组在内存中的长度
- 获取数组在内存中的首地址
```cpp
// 通过数组名统计数组占用内存大学
int arr[10] = {1,2,3,4,5,6,7,8,9,10};
cout << "整个数组占用内存空间为：" << sizeof(arr) << endl; //40  40=4*10
cout << "每个元素占用内存空间为：" << sizeof(arr[0]) << endl;  //4
// 通过数组名查看数组首地址
cout << "数组首地址为：" << (int)arr << endl; //把16进制强转为10进制
cout << "数组中第1个元素地址为：" << (int)&arr[0] << endl; 
cout << "数组中第2个元素地址为：" << (int)&arr[1] << endl; 
// 数组名是常量，不能进行赋值操作,因为已经指向具体地址了
// arr = 100;

```
案例1：五只小猪称体重（找出最重的）
```cpp
int arr[5] = {300,350,200,400,250};
int max =0;
for (int i=0; i<5;i++)
{
	if (arr[i]>max)
	{
		max = arr[i];
	}
}
cout << max << endl;
```
案例2：数组元素逆置
```cpp
int arr[5] = {1,3,2,5,4};
int start =0; //起始下标
int end = sizeof(arr) /sizeof(arr[0]) -1; //结束下标
while (start< end)
{
	//实现元素互换
	int temp = arr[start];
	arr[start] = arr[end];
	arr[end] = temp;
	// 下标更新
	start++;
	end--;
}
```
冒泡排序：
- 1.比较相邻的元素，如果第一个比第二个大，就交换他们俩个；
- 2.对每一对相邻元素做同样的工作，执行完毕后，找到第一个最大值；
- 3. 重复以上步骤，每次比较次数-1，直到不需要比较

```cpp
//用冒泡排序实现升序序列
int arr[9] = {4,2,8,0,5,7,1,3,9};


for (int i=0; i<9-1 ;i++) // 排序总轮数=元素个数-1
{
	//内层循环对比
	for (int j=0 ; j<9-i-1 ; j++) // 每轮对比次数 = 元素个数 - 当前轮数-1
	{
		if (arr[j]>arr[j+1])
		{
			int temp = arr[j];
			arr[j] = arr[j+1];
			arr[j+1] = temp;
		}
	}
}
cout << "done" << endl;
```
### 2-D array
四种定义方式：
- 数据类型 数组名[行数][列数]；
- 数据类型 数组名[行数][列数] = {{数据1,数据2},{数据3，数据4}}；  （**推荐这种**）
- 数据类型 数组名[行数][列数] = {数据1，数据2，数据3，数据4};
- 数据类型 数组名[][列数] = {数据1，数据2，数据3，数据4};

```cpp
// 第一种
int arr[2][3];
arr[0][0] = 1;
arr[0][1] = 2;
arr[0][2] = 3;
arr[1][0] = 4;
arr[1][1] = 5;
arr[1][2] = 6;
for (int i=0;i<2;i++)   //外层循环打印行数
{
	for (int j=0;j<3;j++)   //内层循环打印列数
	{
		cout << arr[i][j] <<endl;
	}
}

//第二种
int arr2[2][3] = 
{
	{1,2,3},
	{4,5,6}
};

//第三种  (程序自己划分出来)
int arr3[2][3] = {1,2,3,4,5,6};

//第四种  (列数不能省略，行数可以空着）
int arr4[][3] = {1,2,3,4,5,6};
```

```cpp
//查看占用内存空间大小
int arr[2][3] =
{
	{1,2,3},
	{4,5,6}	
};
cout << "二维数组占用内存空间为：" << sizeof(arr) <<endl;   //24
cout << "二维数组第一行占用内存空间为：" << sizeof(arr[0]) <<endl;   //12
cout << "二维数组第一个元素占用内存为："  << sizeof(arr[0][0]) <<endl;  //4

cout << "二维数组行数为：" << sizeof(arr)/sizeof(arr[0]) <<endl;  //2
cout << "二维数组列数为：" << sizeof(arr[0])/sizeof(arr[0][0]) <<endl;  //3
 
//查看二维数组首地址
cout << "二维数组首地址为：" << (int)arr <<endl;
```
案例：考试统计，有3名同学的成绩如下，请分别输出三位同学的总成绩：
|  | 语文 |数学 |英语
|--|--| -- |--  | --  | 
|  张三| 100 | 100 | 100 |
|  李四| 90 | 50 | 100 |
|  王五| 60 | 70 | 80 |

```cpp
int score[3][3] = 
{
	{100,100,100},
	{90,50,100},
	{60,70,80}
};
for (int i=0;i<3; i++)
{
	int sum = 0;
	for (int j=0;j<3;j++)
	{
		sum += score[i][j];
	}
	cout << "第" << i+1 << "个人的总分为：" << sum << endl;
}
```
## function
```cpp
//实现一个加法函数，功能是传入2个整型数据，计算数据相加结果，并返回
int add(int num1, int num2)  //定义    num1和num2是形参
{
	int sum = num1 + num2;
	returen sum;
}

int main(){
	int a =10;
	int b =20;
	int c = add(a,b);  //调用   a,b是实参  调用时实参的值传递给形参
	cout << c << endl;
}
```

```cpp
//值传递
//定义函数，实现2个数字进行交换的函数

// 如果函数不需要返回值，声明的时候可以写void
void swap(int num1, int num2)
{
	cout << "交换前:" << end1;
	cout << "num1=" << num1 <<endl;
	cout << "num2=" << num2 <<endl;

	int temp = num1;
	num1 = num2;
	num2 = temp;

	cout << "交换后:" << end1;
	cout << "num1=" << num1 <<endl;
	cout << "num2=" << num2 <<endl;
	// 值传递时，形参修饰不了实参
}
```
```cpp
//函数的常见样式
//1、无参无返
void test01()
{
	cout << "this is test01" << endl;
}
//2、有参无返
void test01(int p)
{
	cout << "this is test02 p=" << p << endl;
}
//3、无参有返
int test03()
{
	cout << "this is test03" << endl;
	return 1000;
}
//4、有参有返
int test04(int k)
{
	cout << "this is test04  k=" << k << endl;
} 

int main(){
	//无参无返调用
	test01();  
	//有参无返调用
	test02(100); 
	//无参有返调用
	int a = test03(); 
	cout << a << endl;
	//有参有返调用
	int num2 = test04(10000);
	cout << num2 << endl;
}
```

```cpp
//函数声明
//比较函数，实现两个整型数字的比较，返回较大的值

//提前告诉编译器函数的存在，可以利用函数的声明
//函数的声明
int max(int a, int b);

int main(){
	int a =10;
	int b = 20;
	cout << max(a,b) << endl;
}

int max(int a, int b)   //写在main函数后面 ，就需要声明
{
	return a > b ? a : b ;
}
```
函数的**分文件编写** ：
- 创建后缀名为.h的头文件
- 创建后缀名为.cpp的源文件
- 在头文件中写函数的声明
- 在源文件中写函数的定义

```cpp
/*
swap.h
*/
//函数的声明
# include <iostream>
using namespace std;
void swap(int a,int b );
```
```cpp
/*
swap.cpp
*/
//函数的定义
#include "swap.h"
void swap(int a ,int b)
{
	int temp = a;
	a =b;
	b = temp;
	cout << "a=" << a << endl;
	cout << "b=" << b << endl;
}
```

```cpp
/*
main.cpp
*/
# include <iostream>
using namespace std;
#include "swap.h"
int main(){
	int a = 10;
	int b = 20;
	swap(a,b);
}

```
## Pointer
指针的作用：通过指针间接访问内存。可以通过指针来保存一个地址。简单理解，**指针就是地址**。
- 内存变化是从0开始记录的，一般用16进制表示

```cpp
//定义一个指针(语法：数据类型 * 指针变量名;)
int a = 10;
int * p = &a;//让指针记录变量a的地址
cout << "a的地址为：" << &a << endl;
cout << "指针p为："  <<p << endl;   //与上一行输出相同

//使用指针 (可以通过解引用的方式来找到指针指向的内存)
//指针前加 * 代表解引用，找到指针指向的内存中的数据
*p = 1000;
cout << "a=" << a << endl;   // a=1000
cout << "*p = " << *p << endl;  //*p=1000
```
> 指针也是一种数据类型，那么它占用多少内存空间？

```cpp
int a = 10;
int * p = &a;
cout << "sizeof (int *) = "<< sizeof(p) << endl;
```
**空指针**：指针变量指向内存中编号为0的空间
用途：初始化指针变量
注意：空指针指向的内存是不可以访问的

```cpp
int * p = NULL; //空指针。任何指针变量刚被创建时不会自动成为NULL指针，它的缺省值是随机的，它会乱指一气
// *p = 100； 出错，空指针不能访问。0-255之间的内存编号是系统占用的，都不可以访问。
```
**野指针**：指针变量指向非法的内存空间
```cpp
//
int * p = (int *)0x1100;
cout << *p <<endl;  //报错
```
const修饰指针：
- const修饰指针--常量指针
- const修饰常量--指针常量
- const既修饰指针，又修饰常量

```cpp
//const修饰指针 
int a = 10;
int b = 10;
const int * p = &a; //常量指针，指针指向的值不可以改，指针指向可以改
// *p = 20；  错误
p = &b;
//const修饰常量
int * const p2 = &a; //指针常量，指针指向不可以改，指向的值可以改
*p2 = 100
//p2 = &b; 错误
//const修饰指针和常量
const int * const p3 = &a;
//*p3=100; 错误
//p3=&b;   错误
```

```cpp
//指针和数组
//利用指针访问数组中的元素
int arr[10]={1,2,3,4,5,6,7,8,9,10};
int * p = arr; //arr就是数组的首地址
cout << "利用指针访问第1个元素：" << *p <<endl;
p++; //让指针向后偏移4个字节
cout << "利用指针访问第2个元素：" << *p <<endl;

//用指针遍历数组
int * p2 = arr;
for (int i=0; i<10 ; i++)
{
	cout << *p2 << endl;
	p2++;
}
```

```cpp
//指针与函数
void swap01(int a, int b)
{
	int temp = a;
	a = b;
	b = temp;
}
void swap02(int *p1 , int *p2)
{
	int temp = *p1;
	*p1 = *p2;
	*p2 = temp;
}

int main(){
	//值传递
	int a = 10;
	int b = 20;
	swap01(a,b); //实参a，b没有改变，形参a，b发生改变
	//地址传递  此时可以修饰实参
	swap02(&a,&b);
}
```
> 不想修改实参，就用值传递，如果想修改实参，就用地址传递

案例：封装一个函数，利用冒泡排序，实现对整型数组的升序排序
例如数组： int arr[10] = {4,3,6,9,1,2,10,8,7,5};
```cpp
#include <iostream>
using namespace std;

//冒泡排序  参数1：数组首地址  参数2：数组长度
void BubbleSort(int* arr, int len)  //int * array 也可写为int arr[]
{
	for (int i = 0; i < len - 1; i++)
	{
		for (int j = 0; j < len - i - 1; j++)
		{
			if (arr[j] > arr[j + 1])
			{
				int temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
			}
		}
	}
}

void printArray(int* arr, int len)
{
	for (int i = 0; i < len; i++)
	{
		cout << arr[i] << endl;
	}
}

int main() {
	int arr[10] = { 4,3,6,9,1,2,10,8,7,5 };
	int len = sizeof(arr) / sizeof(arr[0]);
	BubbleSort(arr, len);   //arr相当于把地址放进去了
	printArray(arr, len);
	system("pause");
	return 0;
}
```
## struct
结构体：用户自定义数据类型
语法：`struct 结构体名 {结构体成员列表}`

```cpp
#include <string>
//创建学生类型
struct Student
{
	string name;
	int age;
	int score;
}s3;  //顺便创建一个结构体变量
//通过学生类型创建具体学生
//方法一：struct Student s1
struct Student s1;  //创建变量时，struct可以省略
s1.name = "zhangsan";
s1.age = 18;
s1.score = 100;
//方法二：struct Student s2 = {...}
struct Student s2 = {"lisi",18,98};
//方法三：在定义结构体时顺便创建结构体变量
s3.name = "wangwu";
s3.age =19;
s3.socre = 80;
```
**结构体数组**：将自定义的结构体放入到数组中方便维护。
语法：`struct 结构体名 数组名[元素个数] = {{},{},...{}}`
```cpp
//定义结构体
struct Student
{
	string name;
	int age;
	int score;
};
int main(){
	//创建结构体数组
	struct Student stuArray[3] =
	{
		{"zhangsan",18,100},
		{"lisi",29,99},
		{"wangwu",38,66}
	};
	//给结构体数组中的元素赋值
	stuArray[2].name = "zhaoliu";
	stuArray[2].age = 80;
	stuArray[2].score = 60;
	//遍历结构体数组
	for (int i =0;i<3;i++)
	{
		cout << "name:" << stuArray[i].name
		     << "age :" << stuArray[i].age
		     << "score:"<< stuArray[i].score <<endl;
	}
}
```
**结构体指针**：通过指针访问结构体中的成员

```cpp
struct Student
{
	string name;
	int age;
	int score;
};

int main(){
	struct Student s = {"zhangsan",18,100};
	//通过指针指向结构体变量
	Student * p = &s; 
	//通过指针访问结构体变量中的数据
	cout << "name:" << p->name
}
```
**结构体嵌套结构体**
例如：每个老师辅导一个学员，一个老师的结构体中，记录一个学生的结构体。

```cpp
struct student
{
	string name;
	int age;
	int score;
};

struct teacher
{
	int id;
	string name;
	int age;   
	struct student stu; //辅导的学生
};

int main(){
	teacher t;
	t.id = 10000;
	t.name = "laowang";
	t.age = 50;
	t.stu.name = "xiaowang";
	t.stu.age = 20;
}
```

```cpp
struct student
{
	string name;
	int age;
	int score;
};
//值传递
void printStudent1(struct student s)
{
	cout << s.name << s.age << s.score << endl;
}
//地址传递
void printStudent2(struct student * p)
{
	cout << p->name << p->age << p->score
}


int main(){
	struct student s;
	s.name = "zhangsan";
	s.age = 20;
	s.score = 85;
	printStudent1(s); //修改形参不改变实参
	printStudent2(&s); //修改形参改变实参
}
```
结构体中const的使用场景：防止误操作
```cpp
struct student
{
	string name;
	int age;
	int score;
};
//将函数中的形参改为指针，可以减少内存空间
void printStudent(const student *s) //地址传递时，防止误操作
{
	// s->age = 150;    加入const后，本操作会报错，防止误操作
	cout << s->name << s->age << s->score << endl;
}
int main(){
	student s ={"zhangsan",15,70};
	printStudent(&s);
}
```
案例1：
> 学校正在做毕设，每个老师带5个学生，总共3名老师，需求如下：设计学生和老师的结构体，其中在老师的结构体中，有老师姓名和一个存放5名学生的数组作为成员。学生的成员有姓名、考试分数，创建数组存放3名老师，通过函数给每个老师及所带的学生赋值。最终打印出老师数据以及老师所带学生的数据。

```cpp
#include<iostream>
using namespace std;
#include <string>
#include <ctime>


//学生的结构体
struct Student
{
	//姓名
	string sName;
	//分数
	int score;
};

//老师的结构体定义
struct Teacher
{
	//姓名
	string tName;
	//学生数组
	struct Student sArray[5];
};

//给老师和学生赋值的函数
void allocateSpace(struct Teacher tArray[] , int len )
{

	string nameSeed = "ABCDE";
	//给老师开始赋值
	for (int i = 0; i < len; i++)
	{
		tArray[i].tName = "Teacher_";
		tArray[i].tName += nameSeed[i];

		//通过循环给每名老师所带的学生赋值
		for (int j = 0; j < 5; j++)
		{
			tArray[i].sArray[j].sName = "Student_";
			tArray[i].sArray[j].sName += nameSeed[j];

			int random = rand() % 61 + 40; // 40 ~ 100
			tArray[i].sArray[j].score = random;
		}
		
	}
}


//打印所有信息
void printInfo(struct Teacher tArray[], int len)
{
	for (int i = 0; i < len; i++)
	{
		cout << "老师姓名： " << tArray[i].tName << endl;

		for (int j = 0; j < 5; j++)
		{
			cout << "\t学生姓名： " << tArray[i].sArray[j].sName <<
				" 考试分数： " << tArray[i].sArray[j].score << endl;
		}
	}
}

int main() {

	//随机数种子
	srand((unsigned int)time(NULL));

	//1、创建3名老师的数组
	struct Teacher tArray[3];

	//2、通过函数给3名老师的信息赋值，并给老师带的学生信息赋值
	int len = sizeof(tArray) / sizeof(tArray[0]);
	allocateSpace(tArray, len);

	//3、打印所有老师及所带的学生信息
	printInfo(tArray,len);

	system("pause");

	return 0;
}
```
案例2：
>设计一个英雄的结构体，包括成员姓名，年龄，性别；创建结构体数组，数组中存放5名英雄。通过冒泡排序算法，将数组中的英雄按年龄进行升序排序，最终打印排序结果。

五名英雄信息如下：

 - 刘备，23，男
 - 关羽，22，男
 - 张飞，20，男
 - 赵云，21，男
 - 貂蝉，19，女

```cpp
#include<iostream>
using namespace std;
#include <string>

//1、设计英雄结构体
//英雄结构体
struct Hero
{
	//姓名
	string name;
	//年龄
	int age;
	//性别
	string sex;
};

//冒泡排序 实现年龄升序排列
void bubbleSort(struct Hero heroArray[] , int len)
{
	for (int i = 0; i < len - 1; i++)
	{
		for (int j = 0; j < len - i - 1; j++)
		{
			//如果j 下标的元素年龄 大于 j+1下标的元素的年龄 ，交换两个元素
			if (heroArray[j].age > heroArray[j + 1].age)
			{
				struct Hero temp = heroArray[j];
				heroArray[j] = heroArray[j + 1];
				heroArray[j + 1] = temp;
			}
		}
	}
}

//打印排序后数组中的信息
void printHero(struct Hero heroArray[] , int len)
{
	for (int i = 0; i < len; i++)
	{
		cout << "姓名： " << heroArray[i].name << " 年龄： " << heroArray[i].age
		<< " 性别： " << heroArray[i].sex << endl;
	}

}

int main() {


	//2、创建数组存放5名英雄
	struct Hero heroArray[5] =
	{
		{"刘备",23,"男"},
		{"关羽",22,"男"},
		{"张飞",20,"男"},
		{"赵云",21,"男"},
		{"貂蝉",19,"女"},
	};

	int len = sizeof(heroArray) / sizeof(heroArray[0]);
	cout << "排序前打印： " << endl;
	for (int i = 0; i < len; i++)
	{
		cout << "姓名： " << heroArray[i].name << " 年龄： " << heroArray[i].age
			<< " 性别： " << heroArray[i].sex << endl;
	}

	//3、对数组进行排序，按照年龄进行升序排序
	bubbleSort(heroArray, len);

	cout << "排序后打印： " << endl;
	//4、将排序后结果打印输出
	printHero(heroArray,len);


	system("pause");

	return 0;
}

# core programming(object-oriented)
## Memory partition model
c++程序在执行时，将内存大方向划分为**4**个区域：
- **代码区**：存放函数体的二进制代码，由操作系统进行管理的
- **全局区** ：存放全局变量和静态变量及常量
- **栈区**：由编译器自动分配释放，存放函数的参数值，局部变量等
- **堆区**：由程序员分配和释放，若程序员不释放，程序结束时由操作系统回收

**内存四区意义**：不同区域存放的数据，赋予不同的生命周期，给我们更大的灵活编程

程序运行前：
在程序编译后，生成了exe可执行程序，**未执行**该程序前分为两个区域：
- 代码区：（1）存放CPU执行的机器指令；（2）代码区是共享的，共享的目的是对于频繁被执行的程序，只需要在内存中有一份代码即可；（3）代码区是**只读**的，使其只读的原因是防止程序意外地修改了它的指令；
- 全局区：（1）全局变量和静态变量存放在此；（2）全局区还包含了常量区、字符串常量和其他常量；（3）该区域的数据在程序结束后由操作系统释放

```cpp
#include<iostream>
using namespace std;

//全局变量
int g_a = 10;
int g_b = 10;

//const修饰的全局变量，全局常量
const int c_g_a = 10;
const int c_g_b = 10;

int main() {


	//全局区 

	//全局变量、静态变量、常量


	//创建普通局部变量
	int a = 10;
	int b = 10;

	cout << "局部变量a的地址为： " << (int)&a << endl;
	cout << "局部变量b的地址为： " << (int)&b << endl;

	cout << "全局变量g_a的地址为： " << (int)&g_a << endl;
	cout << "全局变量g_b的地址为： " << (int)&g_b << endl;

	//静态变量  在普通变量前面加static，属于静态变量
	static int s_a = 10;
	static int s_b = 10;
	cout << "静态变量s_a的地址为： " << (int)&s_a << endl;
	cout << "静态变量s_b的地址为： " << (int)&s_b << endl;

	//常量 
	//字符串常量
	cout << "字符串常量的地址为： " << (int)&"hello world" << endl;

	//const修饰的变量
	//const修饰的全局变量，const修饰的局部变量、

	cout << "全局常量 c_g_a的地址为： " << (int)&c_g_a << endl;
	cout << "全局常量 c_g_b的地址为： " << (int)&c_g_b << endl;

	const int c_l_a = 10; // c-const   g- global  l - local
	const int c_l_b = 10;

	cout << "局部常量 c_l_a的地址为： " << (int)&c_l_a << endl;
	cout << "局部常量 c_l_b的地址为： " << (int)&c_l_b << endl;

	system("pause");

	return 0;
}
```
程序运行后：
- **栈区**：由编译器自动分配释放，存放函数的参数值，局部变量等。
< 注意不要返回局部变量的地址，栈区开辟的数据由编译器自动释放
- **堆区**：程序员分配。在c++中用`new`在堆区开辟内存。
```cpp
#include<iostream>
using namespace std;

//栈区数据注意事项  --- 不要返回局部变量的地址
//栈区的数据由编译器管理开辟和释放

int* func(int b) //形参数据也会放在栈区
{
	b = 100;
	int a = 10; //局部变量  存放在栈区，栈区的数据在函数执行完后自动释放
	return &a; //返回局部变量的地址
}

int main() {

	//接受func函数的返回值 
	int * p =  func(1);

	cout << *p << endl; //第一次可以打印正确的数字，是因为编译器做了保留
	cout << *p << endl; //第二次这个数据就不再保留了

	system("pause");

	return 0;
}
```

```cpp
#include<iostream>
using namespace std;

int * func()
{
	//利用new关键字  可以将数据开辟到堆区
	//指针 本质也是局部变量，放在栈上，指针保存的数据是放在堆区
	int * p =  new int(10);
	return p;
}

int main() {

	//在堆区开辟数据
	int *p = func(); 

	cout << *p << endl;
	cout << *p << endl;
	cout << *p << endl;
	cout << *p << endl;

	system("pause");

	return 0;
}
```

```cpp
//1、new的基本语法
int * func()
{
	//在堆区创建整型数据
	//new返回是 该数据类型的指针
	int * p =  new int(10);
	return p;
}

void test01()
{
	int * p = func();
	cout << *p << endl;
	cout << *p << endl;
	cout << *p << endl;
	//堆区的数据 由程序员管理开辟，程序员管理释放
	//如果想释放堆区的数据，利用关键字 delete
	delete p;

	//cout << *p << endl; //内存已经被释放，再次访问就是非法操作，会报错
}

//2、在堆区利用new开辟数组
void test02()
{
	//创建10整型数据的数组，在堆区
	int * arr = new int[10]; //10代表数组有10个元素

	for (int i = 0; i < 10; i++)
	{
		arr[i] = i + 100; //给10个元素赋值  100 ~ 109
	}

	for (int i = 0; i < 10; i++)
	{
		cout << arr[i] << endl;
	}
	//释放堆区数组
	//释放数组的时候 要加[]才可以
	delete[] arr;
}

int main() {
	//test01();
	test02();

	system("pause");

	return 0;
}
```
