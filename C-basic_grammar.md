#### 数据类型

```c
char		//字符数据类型(1个字节)
short		//短整型(2个字节)
int			//整型(4个字节)
long		//长整型(4 / 8个字节)
long long	//更长的整型(8个字节)
float		//单精度浮点数(4个字节)
double		//双精度浮点数(4个字节)
//C语言没有字符串类型?
1. 为什么会出现这么的类型?
2. 每种类型的大小是多少?
```

```c
字节(计算机中的单位)
bit -比特位
byte -字节	1字节 = 8个比特位的大小
kb			 1kb = 1024byte
mb			 1mb = 1024kb
gb			 1gb = 1024mb
tb			 1tb = 1024gb
pb			 1pb = 1024tb
```



```c
#include <stdio.h>//别人的东西-打招呼
                //包含一个叫stdio.h的文件
                //std-标准 standard input output
int main() //主函数-程序的入口-main函数有且只有一个
{
    printf("hello world\n");//函数-print function-printf-打印函数
                            //库函数-C语言本身提供给我们使用的函数
    printf("hello world\n");
    printf("hello world\n");
    printf("hello world\n");
    return 0;//返回0
}

//int 是整型的意思
int main2() //main前面的int表示main函数调用返回一个整型值
{
    return 0;
}
```





```c
#include <stdio.h>
int main()
{
    //char-字符类型
    char ch = 'A'; //内存申请一块空间
    printf("%c\n",ch); //%c - 打印字符格式的数据
    int age = 20;
    printf("%d\n",age); //%d - 打印整型十进制数据
    return 0;
}
//%d - 打印整型
//%c - 打印字符
//%f - 打印浮点数字-打印小数
//%p - 以地址的形式打印
//%x - 打印16进制数字
//%o - 打印八进制数字
```



#### 全局变量和局部变量

1.局部变量的作用域是变量所在的局部范围

2.全局变量的作用域是整个工程

```c
#incldue <stdio.h>
int num2 =20; //全局变量-定义在代码块({})之外的变量
int main(void)
{
    //局部变量和全局变量的名字建议不要相同-容易误会,产生bug
    //当局部变量和全局变量的名字相同的时候,局部变量有限
    int num1 = 10; //局部变量-定义在代码块({})内部
    return 0;
}
```

#### 生命周期

> 变量的生命周期指的是变量的创建到变量销毁的一个时间段

1.局部变量的生命周期是：进入作用域生命周期开始，出作用域生命周期结束。

2.全局变量的生命周期：整个程序的生命周期。

### 常量

C语言中的常量分为一下几种：

- 字面常量
- const 修饰的常量
- #define 定义的标识符常量
- 枚举常量

```c
#inlcude <stdio.h>
//MALE,FEMALE,SECRET - 枚举常量
int main(void)
{
    //const - 常属性
    const int n = 10; //n是变量，但是又有常属性，所以我们说n是常变量
    return 0;
}
```

```c
#include <stdio.h>
enum Sex
{
    MALE,
    FEMALE,
    SECRET
};
//MALE,FEMALE,SECRET - 枚举常量(不可修改)
int main(void)
{
    enum Sex s = FEMALE; //通过枚举类型创建出来的变量可以修改
    printf("%d\n",MALE);
    printf("%d\n",FEMALE);
    printf("%d\n",SECRET);
    return 0;
}
```

### 字符串

这种由双引号引起的一串字符成为字符串字面值，或者简称字符串

> Tips：字符串的结束标志是一个`\0`的转义字符。在计算字符串长度的时候`\0`是结束标志，不算作字符串内容

```c
#include <stdio.h>
int main(void)
{
    char arr1[] = "abc"; //数组
    //"abc" -- 'a' 'b' 'c' '\0' -- '\0' 字符串的结束标志
    char arr2[] = {'a', 'b', 'c'}; //如果有结束符\0 长度为3
    printf("%s\n", arr1);
    printf("%s\n", arr2);
    printf("%d\n", strlen(arr1));//计算字符串长度
    printf("%d\n", strlen(arr2));
    //arr1为3	arr2为6(随机值)
    return 0;
}
```

### 转义字符

| 转义字符 | 释义                                               |
| -------- | -------------------------------------------------- |
| `\?`     | 在书写连续多个问号时使用，防止它们被解析成三字母词 |
| `\'`     | 用于表示常量`'`                                    |
| `\"`     | 用于表示一个字符串内部的双引号                     |
| `\\`     | 用于表示一个反斜杠，防止它被解释为一个转义序列符   |
| `\a`     | 警告字符，蜂鸣                                     |
| `\b`     | 退格符                                             |
| `\f`     | 换页                                               |
| `\n`     | 换行                                               |
| `\r`     | 回车                                               |
| `\t`     | 水平制表符                                         |
| `\v`     | 垂直制表符                                         |
| `\ddd`   | 1到3为位八进制的数字。如：`\130 X`                 |
| `\xdd`   | dd表示2个十六进制数字。如：`\x30 0`                |

```c
#include <stdio.h>
int main(void)
{
    //移 (2进制)位操作符
    //<< 左移 (乘2)
    //>> 右移 (除2)
    int a = 1; //整型1占4个字节-32bit位
    a << 1;
    return 0;
}
```

```c
#include <stdio.h>
int main()
{//(2进制)位操作
 //& 按位与
 //| 按位或
 //^ 按位异或,对应二进制位相同则为0,对应的二进制位相异，则为0
 //与:全一则一; 或:有一则一; 异或:有一则一全一则零
    int a = 3;
    int b = 5;
    int c = a ^ b;
    
    return 0;
}
```

### 操作符

```c
//单目操作符
!		逻辑反操作
-		负值
&		正值
sizeof	操作数的类型长度(以字节为单位)
~		对一个数的二进制按位取反
--		前置、后置--
++		前置、后置++
*		间接访问操作符(解引用操作符)
(类型)	强制类型转换
//关系操作符
>
>=
<
<==
!=		用于测试“不相等”
==		用于测试“相等”
//逻辑操作符
&&		逻辑与
||		逻辑或
//条件操作符
exp1 ? exp2 : exp3 //如果表达式1为真就执行表达式2，如果为假就执行表达式3
//逗号表达式
exp1, exp2, exp3, ...expN
//下标引用、函数调用和结构成员
[]	()	.	->
```

### 常见的关键字

```c
auto	break	case	char	const	continue	default	do	double	else	enum	extern	for		goto	if		int		long	register	return	short	sizeof	static	struct	switch	typedef	union	unsigned	void	volatile	while  
```

