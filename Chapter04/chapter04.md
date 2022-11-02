1.编写一个程序，提示用户输入名和姓，然后以"名，姓"的格式打印出来。

```
#include <stdio.h>
// 编写一个程序，提示用户输入名和姓，然后以"名，姓"的格式打印出来
int main(void)
{
    char name[40];
    char surname[40];
    printf("Enter input your name and surname:\n");
    scanf("%s %s", name, surname);
    printf("Hello, %s,%s", name, surname);

    return 0;
}
```

2.编写一个程序，提示用户输入名字，并执行以下操作：   
a.打印名字，包括双引号；   
b.在宽度为20的字段有段打印名字，包括双引号；   
c.在宽度为20的字段左端打印名字，包括双括号;   
d.在比姓名宽度宽3的字段中打印名字。

```
#include "stdio.h"
#include "string.h"
// 编写一个程序，提示用户输入名字，并执行一下操作：
//a. 打印名字，包括双引号；
//b. 在宽度为20的字段右端打印名字，包括双引号；
//c. 在宽度为20的字段左端打印名字，包括双引号；
//d. 在比姓名宽度宽3的字段中打印名字

int main(void) {
    char name[40];
    int width;
    printf("Enter input your name:\n");
    scanf("%s", name);
    //width = printf("\"%s\".\n", name);
    printf("\"%s\".\n", name);
    printf("\"%s\".\n", name);
    printf("\"%20s\".\n", name);
    printf("\"%-20s\".\n", name);
    width = strlen(name);
    printf("%*s.\n", (width + 3), name);

    return 0;
}
```

3.编写一个程序，读取一个浮点数，首先以小数点记数法打印，然后以指数记数法打印。用下面的格式进行输出（系统不同，指数记数法显示的位数可能不同):  
a. The input is 21.3 or 2.1e+001.   
b. The input is +21.290 or 2.129E+001.

```
#include <stdio.h>

int main() {
    float value;
    printf("please input a number:");
    scanf("%f", &value);
    printf("The input is %.1f or %.1e\n", value, value);
    printf("The input is %+.3f or %.3E", value, value);
    return 0;
}

```
4.写一个程序,提示用户输入身高(单位:英寸)和姓名,然后以下面的格式显示用户刚输入的信息:  
Dabney, you are 6.208 feet tall   
使用 float类型,并用/作为除号。如果你愿意,可以要求用户以厘米为单位输入身高,并以米为单位显示出来。

```
#include "stdio.h"

// 编写一个程序，提示用户输入身高（单位：英寸）和姓名，然后以下面的格式显示用户刚刚输入的信息：
// Dabney， you are 6.208 feet tall

int main(void) {
    float tall;
    char name[40];
    printf("Please enter input your tall:\n");
    scanf("%f", &tall);
    printf("Please enter input your name:\n");
    scanf("%s", name);
    printf("%s, you are %.3f feet tall.\n", name, (tall / 12.0));

    return 0;
}
```

5.编写一个程序,提示用户输入以兆位每秒(Mb/s)为单位的下载速度和以兆字节(MB)为单位的文件大小。程序中应计算文件的下载时间。注意,这里1字节等于8位。使用 float类型,并用/作为除号。该程序要以下面的格式打印3个变量的值(下载速度、文件大小和下载时间),显示小数点后面两位数字:  
At 18.12 megabits per second, a file of 2. 20 megabytes   
downloads in 0. 97 seconds.

```
#include <stdio.h>

int main() 
{
	float speed, size;
	printf("请输入下载速度(megabits):");
	scanf("%f", &speed);
	printf("请输入文件大小(megabytes):");
	scanf("%f", &size);
	printf("At %.2f megabits per second,a file of %.2f megabytes \ndownloads  in %.2f seconds.",speed,size,size/(speed/8));
	return 0;
}

```

6.编写一个程序,先提示用户输入名,然后提示用户输入姓。在一行打印用户输入的名和姓,下一行分别打印名和姓的字母数。字母数要与相应名和姓的结尾对齐,如下所示:  
Melissa Honeybee  
             7             8   
接下来,再打印相同的信息,但是字母个数与相应名和姓的开头对齐,如下所示:  
Melissa Honeybee   
7            8

```
#include <stdio.h>
#include "string.h"

int main() {

    char fname[40];
    char lname[40];
    printf("请输入您的姓:");
    scanf("%s", &fname);
    printf("请输入您的名:");
    scanf("%s", &lname);
    printf(" %s %s\n", lname, fname);       //  printf（）的*和后面的参数一一对应，且*修饰符代表字段宽度
    printf(" %*u %*u\n", strlen(fname), strlen(fname), strlen(lname), strlen(lname));
    printf(" %-*u %-*u\n", strlen(fname), strlen(fname), strlen(lname), strlen(lname));
    return 0;
}
//scanf（）的*和printf（）的*不同。scanf（）的*是放在%和转换字符之间是，会使scanf（）跳过相应的输入项。
```

7.编写一个程序,将一个double类型的变量设置为1.0/3.0,一个float类型的变量设置为1.0/3.0。分别显示两次计算的结果各3次:一次显示小数点后面6位数字；一次显示小数点后面12位数字一次显示小数点后面16位数字。程序中要包含.h头文件, 并显示 FLT_DIG和 DBL_DIG的值。1.0/3.0的值与这些值一致吗?

```
#include <stdio.h>
#include <float.h>

int main(void)
{
    double a = 1.0 / 3.0;
    float b = 1.0 / 3.0;
    printf("%.6f %20.6f\n", a, b);
    printf("%.12f %20.12f\n", a, b);
    printf("%.16f %20.16f\n", a, b);
    printf("%d %20d", FLT_DIG, DBL_DIG);
    return 0;
}

```

8.编写一个程序,提示用户输入旅行的里程和消耗的汽油量。然后计算并显示消耗每加仑汽油行驶的英里数,显示小数点后面一位数字。接下来,使用1加仑大约3.785升,1英里大约为1.609千米,把单位是英里/加仑的值转换为升/100公里(欧洲通用的燃料消耗表示法),并显示结果,显示小数点后面1位数字。注意,美国采用的方案测量消耗单位燃料的行程(值越大越好),而欧洲则采用单位距离消耗的燃料测量方案(值越低越好。使用#define创建符号常量或使用 const限定符创建变量来表示两个转换系数。

```
#include <stdio.h>

/*const或者define
#define TRANS_GL 3.785
#define TRANS_MM 1.609
*/
int main(void) {
    const float TRANS_GL = 3.785;
    const float TRANS_MM = 1.609;
    float distance, gallon;
    printf("Please enter the mileage of your trip:\n");
    scanf("%f", &distance);
    printf("Please enter the gallons you consumption:\n");
    scanf("%f", &gallon);
    printf("The speed is %.1f (mile/gallon)\n", distance / gallon);
    printf("The speed is %.1f (L/100Km)\n", (gallon * TRANS_GL) / (distance * TRANS_MM * 100));

    return 0;
}

```









