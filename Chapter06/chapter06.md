1.编写一个程序，创建一个包含26个元素的数组，并在其中存储26个小写字母。然后打印数组的所有内容。

```
#include "stdio.h"

int main(void) {
    char letter[26];
    int i;
    char a = 'a';
    const int j = 26;
    for (i = 0; i < j; i++) {
        letter[i] = a++;
    }
    printf("%s\n", letter);     // printf()函数针对字符数组能使用%s输出，会在末尾自动加\0
    for (i = 0; i < j; i++) {
        printf("%-3c", letter[i]);
    }
    return 0;
}
```

2．使用嵌套循环，按下面的格式打印字符:  
$   
$ $   
$ $ $   
$ $ $ $   
$ $ $ $ $  

```
#include "stdio.h"

int main(void) {

    for (int i = 0; i < 5; i++) {
        for (int j = 0; j <= i; j++) {
            printf("$");
        }
        printf("\n");
    }

    return 0;
}
```

3.使用嵌套循环，按下面的格式打印字母:  
F   
FE   
FED   
FEDC   
FEDCB   
FEDCBA  
注意:如果你的系统不使用ASCII或其他以数字顺序编码的代码，可以把字符数组初始化为字母表中的字母:  
char lets [27]=“ABCDEFGHIJKLMNOPQRSTUVWXYZ”;   
然后用数组下标选择单独的字母，例如 lets [0]是 'A‘，等等。

```
#include "stdio.h"

int main(void) {
    char lets[27] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    int num = 6;
    for (int i = 0; i <= num; i ++) {       // 循环6列
        for (int j = 0; j < i; j++) {       //  循环6行
            printf("%c", lets[num - 1 - j]);
        }
        printf("\n");
    }

    return 0;
}
```

4.使用嵌套循环,按下面的格式打印字母:  
A   
BC   
DEF  
GHIJ   
KLMNO   
PORSTU   
如果你的系统不使用以数字顺序编码的代码,请参照练习3的方案解决。

```
#include "stdio.h"

int main(void) {
    char lets[27] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    int num = 6;
    int k = 0;
    for (int i = 0; i <= num; i ++) {       // 循环6行
        for (int j = 0; j < i; j++) {       //  循环6列
            printf("%c", lets[k]);
            k++;
        }
        printf("\n");
    }

    return 0;
}
```

5.编写一个程序,提示用户输入大写字母。使用嵌套循环以下面金字塔型的格式打印字母:  
&nbsp;&nbsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;A  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;ABA   
&emsp;&emsp;&emsp;&emsp;ABCBA   
&emsp;&emsp;ABCDCBA   
ABCDEDCBA   
打印这样的图形,要根据用户输入的字母来决定。例如,上面的图形是在用户输入E后的打印结果。   
提示:用外层循环处理行,每行使用3个内层循环,分别处理空格、以升序打印字母、以降序打印字母。如果系统不使用ASCIl或其他以数字顺序编码的代码,请参照练习3的解决方案。

```
#include "stdio.h"

int main(void) {
    int i, j;
    int n = 5;      // 定义打印行数
    char ch;
    char input;
    int letter[n][2 * n - 1];
    char space = '\0';
    printf("Please input A~Z:\n");


    int x = scanf("%c", &input);
    if (x == 1 && input - 'A' >= 0 && 'Z' - input >= 0) {       // 判断输入的值是否在A到Z
        for (i = 0; i < n; i++) {
            ch = input;                             // 对ch通过input赋值，并存储到数组中
            for (j = 0; j < n - i; j++) {
                letter[i][j] = space;               // 获取ch左边的空格，通过j<n-i，，并存储到数组中
                //printf("%c", letter[i][j]);
            }
            for (j = 0; j <= i; j++) {
                letter[i][n - i - 1 + j] = ch++;        // 获取ch的运算值，，并存储到数组中
                //printf("%c", letter[i][n - 1 - j]);

            }
            for (j = 0; j < n; j++) {
                letter[i][2 * n - 2 - j] = letter[i][j];        // 通过数组的对称性完成ch右边的空格，并存储到数组中
                //printf("%c", letter[i][2*n - 2 - j]);
            }

            printf("\n");

        }
        for (i = 0; i < n; i++) {
            for (int j = 0; j < 2 * n - 1; j++) {
                printf("%c", letter[i][j]);                 // 输出数组值
            }
            printf("\n");
        }
    } else {
        printf("Input letter error!!!");
    }
    return 0;
}
```

6.编写一个程序打印一个表格,每一行打印一个整数、该数的平方、该数的立方。要求用户输入表格的上下限。使用一个for循环。

```
#include "stdio.h"

int main(void) {

    int x, y;
    printf("Enter lower and upper integer limit:");
    scanf("%d %d", &x, &y);
    printf("%-10s%-10s%-10s\n", "num", "square", "cube");
    for (int i = x; i <= y; i++) {
        printf("%-10d%-10d%-10d\n", i, i * i, i * i * i);
    }

    return 0;
}
```

7.编写一个程序把一个单词读入一个字符数组中,然后倒序打印这个单词。提示: strlen()函数(第4章介绍过)可用于计算数组最后一个字符的下标。

```
#include "stdio.h"
#include "string.h"

int main(void) {
    int i;
    char ch[20];

    printf("Please input array:\n");
    scanf("%s", &ch);   //字符数组需要使用 %s转换说明
    int b = strlen(ch);
    printf("%d\n", b);
    for (i = 0; i < b; i++) {
        printf("%c", ch[b - 1 - i]);
    }
}
```

8.编写一个程序,要求用户输入两个浮点数并打印两数之差除以两数乘积的结果。在用户输入非数字之前,程序应循环处理用户输入的每对值。

```
#include "stdio.h"

int main(void){
    double i,j;
    printf("Please input i & j:\n");
    while (scanf("%lf %lf", &i, &j) == 2){
        printf("%lf\n", (i - j) / (i * j));
    }
    return 0;
}
```

9.修改练习8,使用一个函数返回计算的结果。

```
#include "stdio.h"

double calculation(double a, double b);

int main(void) {
    double i, j;
    printf("Please input two double number:\n");
    while (scanf("%lf %lf", &i, &j) == 2) {
        calculation(i, j);
    }
    return 0;
}

double calculation(double a, double b) {
    return printf("%lf", (a - b) / (a * b));
}
```

10.编写一个程序,要求用户输入一个上限整数和一个下限整数,计算从上限到下限范围内所有整数的平方和,并显示计算结果。然后程序继续提示用户输入上限和下限整数,并显示结果,直到用户输入的上限整数等于或小于下限整数为止。程序的运行示例如下:  
Enter lower and upper integer limits: 59   
The sums of the squares from 25 to 81 is 255   
Enter next set of limits: 3 25   
The sums of the squares from 9 to 625 is 5520   
Enter next set of limits: 55   
Done！

```
#include "stdio.h"

int main(void) {

    int x, y;
    printf("Enter lower and upper integer limit:");
    int z = scanf("%d %d", &x, &y);
    while (x < y && z == 2) {
        int sum = 0;
        for (int i = x; i <= y; i++) {
            sum = sum + i * i;
        }
        printf("The sums of the squares from %d to %d is %d\n", x * x, y * y, sum);
        printf("Enter next set of limits:");
        if (scanf("%d %d", &x, &y) !=2){
            break;
        }
    }
    printf("Done");
    return 0;
}
```

11.编写一个程序,在数组中读入8个整数,然后按倒序打印这8个整数。

```
#include "stdio.h"

#define LEN 8

int main(void) {
    int num[LEN];
    int number;
    for (int i = 0, j = 1; i < LEN; i++, j++) {
        printf("Please input th's %d number:\n", j);
        if (scanf("%d", &number) == 1) {
            num[i] = number;
        } else {
            break;
        }
    }


    for (int i = 0; i < LEN; i++) {
        printf("%d    ", num[LEN - 1 - i]);
    }

    return 0;
}
```

12.考虑下面两个无限序列:  
1.0+1.0/2.0+1.0/3.0+1.0/4.0+   
1.0-1.0/2.0+1.0/3.0-1.0/4.0+…
编写一个程序计算这两个无限序列的总和,直到到达某次数。提示:奇数个-1相乘得-1,偶数个1相乘得1。让用户交互地输入指定的次数,当用户输入0或负值时结束输入。查看运行100项、1000项、10000项后的总和,是否发现每个序列都收敛于某值?

```
#include "stdio.h"

int main(void) {
    float i, j, k = 0.0;
    float sum1 = 0.0, sum2 = 0.0;
    printf("Please input order number:\n");
    int m = scanf("%f", &k);
    while (k > 0 && m == 1) {
        for (i = 1.0, j = 1.0, sum1 = 0.0; j < k; j = j + 1.0) {
            if (j == 1.0) {
                printf("%.1f", j);
            } else {
                printf("%+.1f/%.1f", i, j);
            }
            sum1 += i / j;
        }
        printf("\n");
        for (i = 1.0, j = 1.0, sum2 = 0.0; j < k; i = i * (-1.0), j = j + 1.0) {
            if (j == 1.0) {
                printf("%.1f", j);
            } else {
                printf("%+.1f/%.1f", i, j);
            }
            sum2 += i / j;
        }
        printf("\n");
        printf("sum1 equal is %.1f.\n", sum1);
        printf("sum1 equal is %.1f.\n", sum2);
        m = scanf("%f", &k);
    }

    printf("Done!\n");

    return 0;
}
```

13.编写一个程序,创建一个包含8个元素的int类型数组,分别把数组元素设置为2的前8次幂。使用for循环设置数组元素的值,使用 do while循环显示数组元素的值。

```
#include "stdio.h"
#include "math.h"

#define LEN 8

int main(void) {
    int integer[LEN];
    int i = 0;

    for (int i = 0, j = 0; j < LEN; j++, i++) {
        integer[i] = pow(2, j);
        printf("integer[%d] = %d ", i, integer[i]);
    }

    printf("\n");
    
    do {
        printf("integer[%d] = %d ", i, integer[i]);
        i = i + 1;
    } while (i < LEN);

    return 0;

}
```

14.编写一个程序,创建两个包含8个元素的double类型数组,使用循环提示用户为第一个数组输入8个值。第二个数组元素的值设置为第一个数组对应元素的累积之和例如,第二个数组的第4个元素的值是第一个数组前4个元素之和，第二个数组的第5个元素的值是第一个数组前5个元素之和（用嵌套循环可以完成，但是利用第二个数组的第5个元素是第二个数组的第4个元素与第一个数组的第5个元素之和，只用一个循环就能完成任务，不需要使用嵌套循环)。最后，使用循环显示两个数组的内容，第一个数组显示成一行，第二个数组显示在第一个数组的下一行，而且每个元素都与第一个数组各元素相对应。

```
#include "stdio.h"

#define LEN 8

int main(void) {
    //定义两个8个元素的double类型的数组
    double num1[LEN], num2[LEN];
    double i = 0, sum = 0.0;
    int j = 2;
    int m = 0;
    printf("Please input th's 1 number:");
    while (scanf("%lf", &i) == 1 && m < LEN) {
        num1[m] = i;
        ++m;
        if (j > 8) {
            printf("input over!\n");
            break;
        } else {
            printf("Please input th's %d number:", j);
        }
        j++;
    }
    for (int j = 0; j < LEN; j++) {
        printf("%-10lf ", num1[j]);
    }
    printf("\n");
    for (int j = 0; j < LEN; j++) {
        sum += num1[j];
        //printf("%-10lf ", sum);
        num2[j] = sum;
        printf("%-10lf ", num2[j]);

    }

    return 0;
}
```

15．编写一个程序，读取一行输入，然后把输入的内容倒序打印出来。可以把输入储存在.char类型的数组中，假设每行字符不超过255。回忆一下，根据‰c转换说明，scanf()函数一次只能从输入中读取一个字符，而且在用户按下Enter键时scanf()函数会生成一个换行字符（ \n)。

```
#include "stdio.h"

int main(void){

    char value[256];
    int i = 0, j = 0;
    printf("Please input < 255 char:\n");
    do{
        scanf("%c", &value[i]);

    } while (value[i] != '\n' && ++i);

    for (i--; i >= 0; i--) {
        printf("%c ", value[i]);
    }

    return 0;
}

```

16.Daphne以10%的单利息投资了100美元(也就是说,每年投资获利相当于原始投资的10%).Deirdre以5%的复合利息投资了100美元（也就是说，利息是当前余额的5%，包含之前的利息)。编写一个程序，计算需要多少年 Deirdre的投资额才会超过Daphne，并显示那时两人的投资额。

```
#include "stdio.h"

int main(void) {
    float sum1 = 100.0, sum2 = 100.0;
    int j = 0;
    // 方法一
    /*
    for (int i = 1; i < 10000; i++) {
        sum1 = sum1 + 100 * 0.1;
        sum2 = sum2 * (1 + 0.05);
        if (sum2 > sum1) {
            printf("year = %d\n", i);
            printf("sum1 = %f, sum2 = %f\n", sum1, sum2);
            break;
        }

    }
     */
    //方法二
    /*
    while ((sum1 - sum2) >= 0 && ++j) {
        sum1 = 100.0 + 100.0 * 0.1 * j;
        sum2 = sum2 + sum2 * 0.05;
        //printf("year = %d, sum1 = %f, sum2 = %f\n", j, sum1, sum2);
        //++j;
    }

    printf("year = %d, sum1 = %f, sum2 = %f\n", j, sum1, sum2);
*/
    //方法三
    int k = 1;
    do {
        sum1 = 100.0 + 100.0 * 0.1 * k;
        sum2 = sum2 + sum2 * 0.05;
        //printf("year = %d, sum1 = %f, sum2 = %f\n", k, sum1, sum2);
        //++j;
    } while ((sum1 - sum2) > 0 && ++k);

    printf("year = %d, sum1 = %f, sum2 = %f\n", k, sum1, sum2);


    return 0;
}
```

17.Chuckie Lucky赢得了100万美元（税后)，他把奖金存人年利率8%的账户。在每年的最后一天，Chuckie取出10万美元。编写一个程序，计算多少年后Chuckie会取完账户的钱?

```
#include "stdio.h"

int main(void){
    int year = 0;
    double sum = 0;
    for (year = 1, sum = 1000000; year < 1000; year++){
        sum = sum * (1 + 0.08) - 100000;
        printf("%f\n", sum);
        if (sum <= 0){
            printf("%f\n", sum);
            printf("%d\n", year);
            break;
        }
    }
    return 0;
}

```

18.Rabnud博士加入了一个社交圈。起初他有5个朋友。他注意到他的朋友数量以下面的方式增长。第1周少了1个朋友，剩下的朋友数量翻倍;第2周少了2个朋友，剩下的朋友数量翻倍。–般而言，第N周少了N个朋友，剩下的朋友数量翻倍。编写一个程序，计算并显示Rabnud博士每周的朋友数量。该程序一直运行，直到超过邓巴数(Dunbar 's number)。邓巴数是粗略估算一个人在社交圈中有稳定关系的成员的最大值，该值大约是150。

```
#include "stdio.h"

int main(void){

    int week = 1;
    int allMount = 5;

    while(allMount <= 150){
        allMount = 2 * (allMount - week);
        printf("The %d week's friend is %d\n", week, allMount);
        week++;
    }

    return 0;
}
```



