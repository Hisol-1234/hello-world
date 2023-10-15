### tips
* 初始化是个好习惯
* vs2019环境如何运行代码 - ctrl+f5  或在调试中点开始执行（不调试）或fn+ctrl+f5
* ctrl+先k后c - 注释  ctrl+先k后u - 取消注释  上面工具栏也有，前提要先选中注释
* \n换行 %d - 打印整型 %c - 打印字符 %s - 打印字符串 %f - 打印float类型数据 %lf - 打印double类型的数据 %p - 取地址  
* 使用printf需要引用#include <stdio.h>
* getchar和scanf需要输入缓冲区
* ```c
  int ch = 0;
  while ((ch = getchar())!='\n')
  {
  	;
  }//清空缓存区
  ```
  #include <stdio.h>引用系统的
  #include "xxx.h"引用自己的头文件
### 关键字：  
1. 数据类型 char - 字符型 short - 短整型 int - 整型 long - 长整型 long long - 更长的整型 float - 单精度浮点数 double - 双精度浮点数  
2. c语言没有字符串类型，用" "当字符串  
### 变量：  
#### 命名：  
* 只能由字母（包括大写和小写）、数字和下划线（ _ ）组成。  
* 不能以数字开头。  
* 长度不能超过63个字符。  
* 变量名中区分大小写的。  
* 变量名不能使用关键字。  
#### 分类：  
一. 全局变量：跟随整个程序的生命周期  
二. 局部变量：出了局部变量会销毁  
### 常量：  
1. 字面常量 //3.14 	'w' - 单引号引字符	"abc" - 字符串常量
2. const 修饰的常变量  const int a = 10  在c语言中，const修饰的a，本质是变量，但是不能直接修改，是有常量的属性  
const float a = 3.14  
float = 7//err,是不能直接修改的
3. #define 定义的标识符常量
#define max 100
printf("max = %d\n",max)
输出结果为100  
4. 枚举常量   enum  枚举常量不能改？？？？？？？？？？？？？？？？？？？？？？？？？
```c
   enum sex
{  
        male//这仨只是符号类型，不会开辟空间
        female
        secret//他仨是Color未来的可能取值。这三个可能的取值就是枚举常量
}
int main
{
  enum sex a = female;//用这个仨类型去创建变量的时候才会向内存申请空间
}
```
### 字符串  
字符串的结束标志是一个 \0 的转义字符。  
```c
#include <stdio.h>
//下面代码，打印结果是什么？为什么？（突出'\0'的重要性）
int main()
{
    char arr1[] = "bit";
    char arr2[] = {'b', 'i', 't'};
    char arr3[] = {'b', 'i', 't'， '\0'};
    printf("%s\n", arr1);
    printf("%s\n", arr2);
    printf("%s\n", arr3);
    return 0;
}
//输出结果
//bit
//bit烫烫烫烫烫烫烫烫烫烫烫烫烫烫蘠it
//bit
```
### 声明来自外部的符号  
extern int a;
### 转义字符
* \? 在书写连续多个问号时使用，防止他们被解析成三字母词
* \' 用于表示字符常量'
* \“ 用于表示一个字符串内部的双引号
* \\ 用于表示一个反斜杠，防止它被解释为一个转义序列符。
* \a 警告字符，蜂鸣
* \b 退格符
* \f 进纸符
* \n 换行
* \r 回车
* \t 水平制表符
* \v 垂直制表符
* \ddd d d d表示1~3个八进制的数字。 如： \130 表示字符X
* \xdd d d表示2个十六进制数字。 如： \x30 表示字符0  
```c
#include <stdio.h>
int main()
{
    //问题1：在屏幕上打印一个单引号'，怎么做？
    //问题2：在屏幕上打印一个字符串，字符串的内容是一个双引号“，怎么做？
    printf("%c\n", '\'');
    printf("%s\n", "\"");
    printf("%s\n", "are you ok\?\?");
    printf("%s\n", "c:\\user\\test");//打印路径需要两个斜杠，让前面的斜杠转义后面的斜杠，进而让后面的斜杠不再转义\t
    return 0;
} 
```
### 注释  
* C语言风格的注释 /*xxxxxx*/  
缺陷：不能嵌套注释
* C++风格的注释 //xxxxxxxx  
可以注释一行也可以注释多行
### 语句
#### 选择语句
```c
#include <stdio.h>
int main()
{
    int coding = 0;
    printf("你会去敲代码吗？（选择1 or 0）:>");
    scanf("%d", &coding);
    if(coding == 1)
   {
       prinf("坚持，你会有好offer\n");
   }
    else
   {
       printf("放弃，回家卖红薯\n");
   }
    return 0;
}
```
#### 循环语句
* while
* for
* do...while
```c
//while循环的实例
#include <stdio.h>
int main()
{
    printf("加入比特\n");
    int line = 0;
    while(line<=20000)
   {
        line++;
        printf("我要继续努力敲代码\n");
   }
    if(line>20000)
        printf("好offer\n");
    return 0;
}
```
### 函数
```c
//写函数
int add(int a, int b)
{
	int c = 0;
	c = a + b;
	return c;
	return(a + b);
}
int main()
{
	int a = 0;
	int b = 0;
	scanf("%d%d",&a,&b);
	//int c = a + b;
	int c = add(a, b);
	printf("%d\n",c);
	return 0;
}
```
### 数组：一组相同类型元素的集合
`int arr[10] = {1,2,3,4,5,6,7,8,9,10};`  
* C语言规定：数组的每个元素都有一个下标，下标是从0开始的。
* 数组的每个元素都有一个下标，下标都是从0开始的
* 使用方法
```c
#include <stdio.h>
int main()
{
 int i = 0;
 int arr[10] = {1,2,3,4,5,6,7,8,9,10};//10可以不写，系统会自动根据后面的大小填充
 for(i=0; i<10; i++)
 {
       printf("%d ", arr[i]);//arr[1]就是2
 }
 printf("\n");
    return 0;
}
```
### 操作符
* 算数操作符 + - * / %
* 移位操作符 >> <<
* 位操作符 & ^ | 跟二进制有关
& 与--左右操作数，相同位都为1，操作结果该位才为1  
| 或--左右操作数，相同位有一个为1，操作结果就为1  
^ 异或  --左右操作数，对应的位不相同时，操作结果为1
* 赋值操作符 = += -= *= /= &= ^=  |=    >>=   <<=
* 单目操作符 ! 逻辑反操作 - 负值 + 正值 & 取地址 sizeof 操作数的类型长度（以字节为单位） ~ 对一个数的二进制按位取反  
-- 前置、后置--  
++ 前置、后置++  
间接访问操作符(解引用操作符) (类型) 强制类型转换
* 关系操作符 > >= < <=
!=   用于测试“不相等”  
==      用于测试“相等”
* 逻辑操作符
&&  逻辑与  
||  逻辑或
* 条件操作符 exp1 ? exp2 : exp3  
例子`int r = a > b ? a : b;`  
如果exp1成立，则取exp2，反之则取exp3
* 逗号表达式 exp1,exp2,exp3,...expN
从左向右依次计算
* 下标引用、函数调用和结构成员
 []  ()  .   ->
### 常见关键字
auto  break   case  char  const   continue  default  do   double else  enum   
extern float  for   goto  if   int   long  register    return   short  signed
sizeof   static struct  switch  typedef union  unsigned   void  volatile  while  
void最常见的用法，就是在函数中限定函数的参数和返回值的 void draw(void); 表明函数draw没有参数也没有返回值，void在别的的地方的应用我也没见过；
#### 关键字 typedef
typedef 顾名思义是类型定义，这里应该理解为类型重命名。  
```c
//将unsigned int 重命名为uint_32, 所以uint_32也是一个类型名
typedef unsigned int uint_32;
int main()
{
    //观察num1和num2,这两个变量的类型是一样的
    unsigned int num1 = 0;
    uint_32 num2 = 0;
    return 0;
}
```
#### 关键字static
在C语言中：  
static是用来修饰变量和函数的
1. 修饰局部变量-称为静态局部变量
2. 修饰全局变量-称为静态全局变量
3. 修饰函数-称为静态函数
   //static修饰局部变量的时候，局部变量出了作用域，不销毁的，本质上static修饰局部变量的时候，改变了变量的存储位置。static延长了局部变量的生命周期
//栈区，局部变量，出了出了会销毁
//静态区，静态变量 ，存储位置变了，影响了变量的生命周期 static延长了变量的生命不周期，和程序的生命周期一样长
### 结构
#### 顺序结构
#### 选择结构
if switch  
##### if语句
```c
if(表达式)
    语句1;//如果if为真执行语句 a=3也为真
else
    语句2;
//多分支
int age = 0
scanf(%d,&age);
if(age <18)
    printf();
else if(age >=18 && age <40)
    printf();
else if(age >=40 && age <60)
    printf();
else
    printf();
//if或else后面如果要跟多条语句，需要使用大括号
if()
{
    printf();
    printf();
}
else
//else和他离的最近的if匹配
int main
{
    int a =0
    int b = 2
    if(a ==1)
	if(b == 2)
	    printf("hehe\n")
	else printf("haha\n")
}
//结果不打印任何东西
//一个常量和一个变量比较时，5 == a的判断写法比a == 5要好，因为5 = a会报错而a = 5不会报错
```
##### switch语句（适用于多分支）
switch语句是可以嵌套的，break只会跳出自己所在的switch，不会全跳
```c
int main()
{
int day = 0;
scanf("%d", &day);
switch(day)//<--表达式必须包含整型（字符也是整型）
{
case 1://case后必须是整型常量表达式
	printf("星期1\n");
case 2:
	printf("星期2\n");
	break;//跳转语句（如果输入1结果输出星期1、星期二，如果输入2结果是星期二）
case 3:
	printf("星期3\n");
case 4:
	printf("星期4\n");
default://所有的case都不能匹配就转到default
	printf("err\n")
	break;
}
return 0;
}
```
```c
int main()
{
int day = 0;
scanf("%d", &day);
switch(day)//<--表达式必须包含整型
{
case 1:
case 2:
case 3:
case 4:
case 5:
	printf("工作日\n");
	break;//break在需要时使用就行了
case 6:
case 7:
	printf("周末\n")
	break;//switch语句最后一个语句最好加上break
}
return 0;
}
```
#### 循环结构
for while do while
```c
while()
{
    循环语句//只要为真就一直循环
}
//while循环里只要碰到break被执行就终止循环，continue被执行会跳过本次循环后面的代码且再次进入循环判断是否循环
```
#### 指针
存放指针（地址）的变量就是指针变量
