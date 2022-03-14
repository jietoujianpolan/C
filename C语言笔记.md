# C语言笔记

## 第一个c程序

```c
#include <stdio.h>

int main()
{
	printf("Hello world!\n");
	return 0;
}
```

""里面的内容叫做“字符串”

printf会把“”中的内容原封不动的输出

\n表示在输出的结果后面换一行

## 计算

```c
#include <stdio.h>

int main()
{
	printf("%d", 12+34);  //printf("12+24=%d\n",12+24);
	return 0;
}
```

,后面的值会代替%d

| C符号 | 意义 | 四则运算 |
| :---: | :--: | :------: |
|   +   |  加  |    +     |
|   -   |  减  |    -     |
|   *   |  乘  |    ×     |
|   /   |  除  |    ÷     |
|   %   | 取余 |          |
| （）  | 括号 |   （）   |

%表示两个数相除以后的余数

## 变量定义

### 算找零

1.有地方放输入的数字

2.有办法输入数字

3.输入的数字能参与计算

```c
# include <stdio.h>

int main()
{
	int price = 0;  //定义一个变量

	printf("请输入金额（元）：");
	scanf("%d", &price);  //vs中要用scanf_s否则会报错：不安全

	int change = 100 - price;

	printf("找您%d元\n", change);

	return 0;
}

```

![image-20220312221101589](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20220312221101589.png)

变量是一个保存数据的地方，用一个变量保存数据，才能参与到后续的计算

变量定义的一般形式

​	<类型名称><变量名称>;

​	int price;

​	int amount;

​	int price,amount;

变量的名字是一种“标识符”

标识符只能由字母、数字和下划线组成，数字不能出现在第一个位置上，C语言的关键字不能用做标识符

C语言的保留字：auto、break、case、char、const、continue、default、do、double、else、enum、extern、float、for、goto、if、int、long、register、return、short、signed、sizeof、static、struct、switch、typedef、union、unsigned、void、volatile、while、inline、restrict

## 变量赋值与初始化

a=b表示一种动作，将b的值赋给a

所有的变量在第一次被使用之前应该先初始化

```c
#include <stdio.h>

int main()
{
	int i;
	int j;
	j = i+10;
	printf("%d\n",j);

	return 0;
}		
```

vs会报错：error C4700: 使用了未初始化的局部变量“i”

其他编译器可能会输出不同的数据

### 变量初始化

<类型名称><变量名称>=<初始值>;

int price = 0；

int amount = 100；

int price = 0， amount = 100；

### 变量类型

所有的变量必须具有确定的数据类型。数据类型表示在变量中可以存放什么样的数据，变量中只能存放指定类型的数据，程序运行过程中也不能改变变量的类型

C99允许在变量使用之前定义类型，ANSI C只能在代码开头定义变量

## 程序输入

### 读整数

`scanf("%d", &price);`

f为formatted，意为格式化的

要求scanf这个函数读入下一个整数，读到的结果赋值给变量price
注意price前面的& 

## 常量VS变量

定义一个常量：

`const int AMOUNT = 100;  //c99的写法`

```c
#include <stdio.h>

int main()
{
	const int AMOUNT = 100;
	int price = 0;

	printf("请输入金额（元）：");
	scanf("%d", price);

	int change = AMOUNT - price;

	printf("找您%d元\n", change);

	return 0;
}		
```

![image-20220312225424665](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20220312225424665.png)

const是一个修饰符，加在int前面用来给这个变量加上一个const（不变的）属性

const属性表示这个变量的值一旦初始化，就不能再修改了，如果尝试对常量进行修改就会报错

```c
#include <stdio.h>

int main()
{
	int amount = 100;
	int price = 0;

	printf("请输入金额（元）：");
	scanf("%d", &price);

	printf("请输入票面（元）：");
	scanf("%d", &amount);

	int change = amount- price;

	printf("找您%d元\n", change);

	return 0;
}			
```

![image-20220312230144253](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20220312230144253.png)

输入多个值可以放在一起用空格隔开

```c
#include <stdio.h>

int main()
{
	int a;
	int b;

	printf("请输入两个数：");
	scanf_s("%d %d", &a, &b);
	printf("%d + %d = %d\n", a, b, a+b);

	return 0;
}
```

![image-20220312230605748](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20220312230605748.png)

在输入时空格和回车都可以，直到输入两个数为止 

# 浮点数

计算身高的程序

```c
#include <stdio.h>

int main()
{
	printf("请输入身高的英尺和英寸，""如输入\"5 7\"表示5英尺和7英寸：");

	int foot;
	int inch;

	scanf_s("%d %d", &foot, &inch);

	printf("身高是%f\n", ((foot + inch / 12) * 0.3048));

	return 0;
}
```

![image-20220314155602572](C:\Users\86136\AppData\Roaming\Typora\typora-user-images\image-20220314155602572.png)

两个整数的运算的结果只能是整数（原来应该有小数点的地方扔掉了，不会进行四舍五入）





