1.编写一个程序,把用分钟表示的时间转换成用小时和分钟表示的时间。使用#define 或者const创建一个表示60的符号常量或const变量。通讨while循环让用户重复输入值，直到用户输入小于或等于0的值才停止循环。

```
#include "stdio.h"

#define TIME_UNIT 60

int main(void) {
    int i_hour, i_minute, minute;

    printf("please input minute: ");
    scanf("%d", &i_minute);
    while (i_minute > 0) {
        i_hour = i_minute / TIME_UNIT;
        minute = i_minute % TIME_UNIT;
        printf("输入的分钟数：%d分钟转换为：%d小时%d分钟\n", i_minute, i_hour, minute);
        printf("you can try angin input minute or input number <= 0 to over progarm: \n");
        scanf("%d", &i_minute);
    }
    printf("Down!\n");

    return 0;
}
```

编写一个程序,提示用户输入一个整数，然后打印从该数到比该数大10的所有整数（例如，用户输入5，则打印5~15 的所有整数，包括5和15)。要求打印的各值之间用一个空格、制表符或换行符分开。

```
#include <stdio.h>

int main(void)
{
    int i, j=0;
    printf("Please input a number: \n");
    scanf("%d", &i);
    while (j++ < 11)
    {
        printf("%d\n", i++);
    }
    return 0;
}
```

3．编写一个程序，提示用户输入天数，然后将其转换成周数和天数。例如，用户输入18，则转换成2周4天。以下面的格式显示结果:  
18 days are 2 weeks, 4 days.   
通过while循环让用户重复输入天数，当用户输入一个非正值时(如0或-20)，循环结束。

```
#include "stdio.h"
// 5.11.3 练习题

int main(void) {
    int days, week, day;

    printf("Please input days: \n");
    scanf("%d", &days);
    while (days > 0) {
        week = days / 7;
        day = days % 7;
        printf("%d days are %d weeks, %d days\n", days, week, day);
        printf("Please input days or enter days less than or equal to 0 over program: \n");
        scanf("%d", &days);
    }

    return 0;
}
```

4.编写一个程序，提示用户输入一个身高（单位:厘米)，并分别以厘米和英寸为单位显示该值，允许有小数部分。程序应该能让用户重复输入身高，直到用户输入一个非正值。其输出示例如下:  
Enter a height in centimeters: 182  
182.0 cm = 5 feet, 11.7 inches   
Enter a height in centimeters(<=0 to quit):168.7   
168.7 cm = 5 feet, 6.4 inches   
Enter a height in centimeters(<=0 to quit): 0   
bye

```
#include "stdio.h"

#define FEET 30.48
#define INCHES 2.54

int main(void) {
    float feet;
    float inches, cm;

    printf("Enter a height in centimeters: ");
    scanf("%f", &cm);
    while (cm > 0) {
        feet = cm / FEET;
        feet = (int) feet;
        inches = (cm - feet * FEET) / INCHES;
        printf("%.1f cm = %.0f feet, %.1f inches\n", cm, feet, inches);
        printf("Enter a height in centimeters(<=0 to quit): ");
        scanf("%f", &cm);
    }
    printf("bye");

    return 0;
}
```

5．修改程序addemup.c(程序清单5.13),你可以认为addemup.c是计算20天里赚多少钱的程序(假设第1天赚$1、第2天赚$2、第3天赚$3，以此类推)。修改程序,使其可以与用户交互，根据用户输入的数进行计算（即,用读入的一个变量来代替20）。


```
#include <stdio.h>
// 5.11.5-1练习题

int main(void) {
    float money, sum = 0.0;
    int i = 0, j = 0;
    int const days;
    printf("Please input days: ");
    scanf("%d", &days);
    printf("Please input money in one day: $");
    scanf("%f", &money);
    while (i++ <= days) {
        sum = sum + money;
        printf("第%d天赚钱总计为：%.2f\n", i, sum);
        j = i + 1;
        if (j > 20) {
            break;
        }
        printf("Please input money with %d day: $", j);
        scanf("%f", &money);
    }
    return 0;
}
```

6．修改编程练习5的程序，使其能计算整数的平方和（可以认为第1天赚$1、第2天赚$4、第3天赚$9，以此类推，这看起来很不错)。C没有平方函数，但是可以用n*n来表示n的平方。

```
#include <stdio.h>

int main(void) {
    float sum = 0.0;
    int i = 0;
    int const days;
    printf("Please input days: ");
    scanf("%d", &days);

    while (i++ < days) {
        sum = sum + i * i;
        printf("第%d天赚钱总计为：%.2f\n", i, sum);
    }
    return 0;
}
```

7.编写一个程序,提示用户输入一个double类型的数，并打印该数的立方值。自己设计一个函数计算并打印立方值。main()函数要把用户输入的值传递给该函数。

```
#include <stdio.h>

double cube(double number);     //函数原型声明

int main(void) {
    double num;
    printf("Please input a number:\n");
    scanf("%lf", &num);     //double类型的输入需要使用lf%，不能使用%f
    //printf("%lf\n", num);
    cube(num);
    return 0;
}

double cube(double number) {
    double total = 0.0;
    total = number * number * number;
    printf("your input number %lf cube is %lf", number, total);
    return total;
}
```

8．编写一个程序,显示求模运算的结果。把用户输入的第1个整数作为求模运算符的第2个运算对象,该数在运算过程中保持不变。用户后面输入的数是第1个运算对象。当用户输入一个非正值时，程序结束。其输出示例如下:  
This program computes moduli，   
Enter an integer to serve as the second operand: 256   
Now enter the first operand: 438   
438%256 is 182   
Enter next number for first operand (<= 0 to quit):1234567   
1234567 &256 is 135   
Enter next number for first operand (<= 0 to quit) : 0   
Done

```
#include "stdio.h"

int main(void) {
    int a = 0, b = 0, c = 0;
    printf("This program computers moduli.\n");
    printf("Enter an integer to serve as the second operand: ");
    scanf("%d", &a);
    printf("Now enter the first operand: ");
    scanf("%d", &b);
    while (b > 0) {
        c = b % a;
        printf("%d %% %d is %d\n", b, a, c);
        printf("Enter next number for first operand (<= 0 to quit): ");
        scanf("%d", &b);
    }
    printf("Done\n");
    return 0;
}
```

编写一个程序，要求用户输入一个华氏温度。程序应读取double类型的值作为温度值，并把该值作为参数传递给一个用户自定义的函数Temperatures()。该函数计算摄氏温度和开氏温度，并以小数点后面两位数字的精度显示3种温度。要使用不同的温标来表示这3个温度值。下面是华氏温度转摄氏温度的公式:  
摄氏温度=5.0/9.0*(华氏温度-32.0)  
开氏温标常用于科学研究，0表示绝对零，代表最低的温度。下面是摄氏温度转开氏温度的公式：   
开氏温度=摄氏温度+273.16   
Temperatures ()函数中用const创建温度转换中使用的变量。在main ()函数中使用一个循环让用户重复输入温度，当用户输入q或其他非数字时,循环结束。scanf()函数返回读取数据的数量，所以如果读取数字则返回1，如果读取q则不返回1。可以使用==运算符将scanf()的返回值和1作比较,测试两值是否相等。

```
#include <stdio.h>

double Temperatures(double temperature);

int main(void) {

    double temperature;     //   定义华氏温度
    printf("please input temperature's number: ");
    while (scanf("%lf", &temperature) == 1) {
        Temperatures(temperature);
        printf("Please again input temperature's number: ");
    }
    printf("Done");
    return 0;
}

double Temperatures(double temperature) {
    const float Chinese_Temperatures_num1 = 5.0;
    const float Chinese_Temperatures_num2 = 9.0;
    const float Chinese_Temperatures_num3 = 32.0;
    const float Open_Temperatures_num = 273.16;

    double Celsius = 0.0, Kelvin = 0.0;     // Celsius 摄氏温度， Kelvin 开式温度
    Celsius = Chinese_Temperatures_num1 / Chinese_Temperatures_num2 * (temperature - Chinese_Temperatures_num3);
    Kelvin = Celsius + Open_Temperatures_num;
    printf("temperature is %.2f,Celsius is %.2f, Kelvin is %.2f\n", temperature, Celsius, Kelvin);
    return temperature, Celsius, Kelvin;
}

```

