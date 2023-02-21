下面的一些程序要求输入以EOF终止。如果你的操作系统很难或根本无法使用重定向，请使用一些其他的测试来终止输入，如读到&字符时停止。

1．设计一个程序，统计在读到文件结尾之前读取的字符数。

```
#include "stdio.h"

//#define EOF (-1)

int main(void) {
    int ch;
    int number = 0;

    printf("Please enter number letter:\n");
    while ((ch = getchar()) != EOF) {
        putchar(ch);
        number++;
    }
    //fflush(stdout);
    printf("Now end of EOF before has %d letter\n", number);
    // 当前直接在Clion IDE中使用CMD+D，不会直接输入EOF作为文件的输入终止符，而是直接会终止程序，当前要在IDE中验证EOF文件终止符的功能，可以如下操作：
    // 1、只能在debug模式下，输入好文字
    // 2、点击Enter换行符（这个代表行缓冲）
    // 3、再点击CMD + D，这个时候才是代表真正结束当前输入。
    // PS：当前环境是macOS + Clion IDE

    return 0;
}

```

2．编写一个程序，在遇到EOF之前，把输入作为字符流读取。程序要打印每个输入的字符及其相应的ASCII十进制值。注意，在ASCII序列中，空格字符前面的字符都是非打印字符，要特殊处理这些字符。如果非打印字符是换行符或制表符，则分别打印\n或\t。否则，使用控制字符表示法。例如，ASCII的1是 Ctrl+A，可显示为^A。注意，A的ASCII 值是Ctrl+A的值加上64。其他非打印字符也有类似的关系。除每次遇到换行符打印新的一行之外，每行打印10对值。(注意:不同的操作系统其控制字符可能不同。)

```
#include "stdio.h"

int main(void) {
    char ch;
    int counter = 0;

    printf("Please enter number letter:\n");
    while ((ch = getchar()) != EOF) {
        if (counter++ == 10) {
            printf("\n");
            counter = 1;
        } /*输入计时器，冰判断是否打印换行符*/

        if (ch >= '\040') {
            printf("\'%c\'--%3d", ch, ch);
            /* 大于空格字符的可展示为字符的处理和判断*/
        } else if (ch == '\n') {
            printf("\\n--\\n\n");
            counter = 0;
            /*换行符的处理*/
        } else if (ch == '\t') {
            printf("\\t--\\t ");
            /*制表符的处理*/
        } else {
            printf("\'%c\'--^%c", ch, (ch + 64));
            /*其他非显示字符的处理*/
        }
    }

    // 当前直接在Clion IDE中使用CMD+D，不会直接输入EOF作为文件的输入终止符，而是直接会终止程序，当前要在IDE中验证EOF文件终止符的功能，可以如下操作：
    // 1、只能在debug模式下，输入好文字
    // 2、点击Enter换行符（这个代表行缓冲）
    // 3、再点击CMD + D，这个时候才是代表真正结束当前输入。
    // PS：当前环境是macOS + Clion IDE

    return 0;
}

```

3.编写一个程序，在遇到EOF之前，把输入作为字符流读取。该程序要报告输入中的大写字母和小写字母的个数。假设大小写字母数值是连续的。或者使用ctype.h 库中合适的分类函数更方便。

```
#include <ctype.h>
#include "stdio.h"

int main(void) {
    char ch;
    int counter_lower = 0;
    int counter_upper = 0;

    printf("Please enter number letter:\n");
    while ((ch = getchar()) != EOF) {
//        if (islower(ch) != 0) {
        if (islower(ch)) {
            counter_lower++;
        } /*islower判断是否为a～z的小写字母，是小写字母返回非零值，否则返回为零*/

//        if (isupper(ch) != 0) {  // 判断isupper是否为true，是0就是false，否则为true
        if (isupper(ch)) {
            counter_upper++;
        } /*islower判断是否为A～Z的小写字母，是大写字母返回非零值，否则返回为零*/
    }

    printf("Lower letter's number is %d, upper letter's number is %d\n", counter_lower, counter_upper);
    // 当前直接在Clion IDE中使用CMD+D，不会直接输入EOF作为文件的输入终止符，而是直接会终止程序，当前要在IDE中验证EOF文件终止符的功能，可以如下操作：
    // 1、只能在debug模式下，输入好文字
    // 2、点击Enter换行符（这个代表行缓冲）
    // 3、再点击CMD + D，这个时候才是代表真正结束当前输入。
    // PS：当前环境是macOS + Clion IDE

    return 0;
}

```

4．编写一个程序，在遇到EOF之前，把输入作为字符流读取。该程序要报告平均每个单词的字母数。
不要把空白统计为单词的字母。实际上,标点符号也不应该统计，但是现在暂时不用考虑这么多(如果你比较在意这点，考虑使用ctype.h系列中的ispunct ()函数)。

```
#include <ctype.h>
#include "stdio.h"

int main(void) {
    char ch;
    int letter = 0;
    float avg_counter = 0.0;
    int words = 0;

    printf("Please enter number letter:\n");
    while ((ch = getchar()) != EOF) {
        if (isgraph(ch) != 0) {
            letter++;
        }/*isgraph判断是否为字母，是字母返回非零值，否则返回为零*/

        if (ispunct(ch) != 0 || ch == ' ') {
            words++;    // 统计了单词的个数
        } /*ispunct判断如果参数是除字母，数字和空格外可打印字符，函数返回非零值，否则返回零值。即没法判断空格*/

    }

    avg_counter = 1.0 * letter / words;

    printf("There are %d words, and %d character, %.2f C/W!\n", words, letter, avg_counter);
    // 当前直接在Clion IDE中使用CMD+D，不会直接输入EOF作为文件的输入终止符，而是直接会终止程序，当前要在IDE中验证EOF文件终止符的功能，可以如下操作：
    // 1、只能在debug模式下，输入好文字
    // 2、点击Enter换行符（这个代表行缓冲）
    // 3、再点击CMD + D，这个时候才是代表真正结束当前输入。
    // PS：当前环境是macOS + Clion IDE

    return 0;
}

```

5．修改程序清单8.4的猜数字程序，使用更智能的猜测策略。例如，程序最初猜50，询问用户是猜大了、猜小了还是猜对了。如果猜小了，那么下一次猜测的值应是50和100中值，也就是75。如果这次猜大了，那么下一次猜测的值应是50和75的中值，等等。使用二分查找(binary search)策略，如果用户没有欺骗程序，那么程序很快就会猜到正确的答案。


```
#include "stdio.h"

//修改程序清单8.4的猜数字程序，使用更智能的猜测策略。例如，程序最初猜50，询问用户是猜大了、猜小了还是猜对了。如果猜小了，
// 那么下一次猜测的值应是50和100中值，也就是75。如果这次猜大了，那么下一次猜测的值应是50和75的中值，等等。
// 使用二分查找(binary search)策略，如果用户没有欺骗程序，那么程序很快就会猜到正确的答案。


int main(void) {
    int head = 1;
    int tail = 100;
    int guess = (head + tail) / 2;
    char ch;

    printf("Pick an integer from 1 to 100. I will try to guess ");
    printf("it.\nrespond with a y if my guess is right and with");
    printf("\nan n if it is wrong.\n");
    do {
        printf("Uh...is your number %d?\n", guess);
        if (getchar() == 'y') {
            break;
        }
        printf("Well, then, %d is larger or smaller than yours? (l or s):", guess);
        while ((ch = getchar) == '\n') {
            continue;
        }
        if (ch == 'l' || ch == 'L') {
            tail = guess - 1;
            guess = (head + tail) / 2;
            continue;
        } else if (ch == 's' || ch == 'S') {
            head = guess + 1;
            guess = (head + tail) / 2;
            continue;
        } else {
            continue;
        }
    } while (getchar != 'y');

    printf("I knew I could do it!\n");

    return 0;
}
```

修改程序清单8.8中的get first ( )函数，让该函数返回读取的第1个非空白字符，并在一个简单的程序中测试。

```
#include "stdio.h"

char get_first(void);

int main(void) {
    char ch;
    ch = get_first();
    printf("%c\n", ch);

    return 0;
}

char get_first(void) {
    char ch;

    do {
        ch = getchar();
    } while (ch == ' ' || ch == '\n' || ch == '\t');
    return ch;
}
```

7．修改第7章的编程练习8，用字符代替数字标记菜单的选项。用q代替5作为结束输入的标记。

```
#include "stdio.h"
#include <stdbool.h>

void show_salary(int time_salary);

#define salary_time_1 8.75
#define salary_time_2 9.33
#define salary_time_3 10.00
#define salary_time_4 11.20
#define MAGNIFICATION 1.5           // 倍率
#define WEEK_TIME 40            // 每周基础工作时长
#define TAX_RATE_BASIC 0.15         // 交税第一档次税率
#define TAX_RATE_SECOND 0.20         // 交税第二档次税率
#define TAX_RATE_THIRD 0.25         // 交税第三档次税率
#define TAX_RATE_PHASE_1 300        // 薪水第一档次临界点
#define TAX_RATE_PHASE_2 150        // 薪水第二档次临界点
#define SALARY_TAX_RATE_PHASE_1 TAX_RATE_PHASE_1 * TAX_RATE_BASIC           // 满额第一薪水应缴税收
#define SALARY_TAX_RATE_PHASE_2 SALARY_TAX_RATE_PHASE_1 + TAX_RATE_PHASE_2 * TAX_RATE_SECOND    // 满额第二薪水应缴税收

int main(void) {

    int time = 0, number = 1;
    bool flag = 0;
    float time_salary = 10.00;

    printf("Enter the number corresponding to the desired pay rate or action:");
    printf("a) $8.75/hr   \n"
           "b)$9.33/hr   \n"
           "c)$10.00 /hr   \n"
           "d)$11.20 /hr  \n"
           "q）quit\n");

    while ((flag == 0 && scanf("%d", &number) == 1)) {

        switch (number) {
            case 'a':
            case 'A': {
                time_salary = salary_time_1;
                show_salary(time_salary);
                flag = 1;
                break;
            }
            case 'b':
            case 'B': {
                time_salary = salary_time_2;
                show_salary(time_salary);
                flag = 1;
                break;
            }
            case 'c':
            case 'C': {
                time_salary = salary_time_3;
                show_salary(time_salary);
                flag = 1;
                break;
            }
            case 'd':
            case 'D': {
                time_salary = salary_time_4;
                show_salary(time_salary);
                flag = 1;
                break;
            }
            case 'q': {
                printf("quit\n");
                break;
            }
            default: {
                printf("Please enter correct letter:");
                break;
            }
        }

    }

    printf("Down\n");


    return 0;
}

void show_salary(int time_salary) {
    int time;
    float salary = 0.0, tax_revenue = 0.0, total_revenue = 0.0;

    printf("Please input time:\n");
    while (scanf("%d", &time) == 1) {

        if (time <= WEEK_TIME && time >= 0) {
            salary = time * time_salary;           // 计算基础周工作时长的薪资
        } else if (time > WEEK_TIME) {
            salary = WEEK_TIME * time_salary +
                     (time - WEEK_TIME) * time_salary * MAGNIFICATION;         // 计算超过基础周工作时长的薪资
        } else {
            printf("Please input less than 0 or error");
        }

        if (salary <= TAX_RATE_PHASE_1) {
            tax_revenue = salary * TAX_RATE_BASIC;      // 计算低于第一档次薪水临界点的应缴纳税额
        } else if (salary > TAX_RATE_PHASE_1 && salary <= (TAX_RATE_PHASE_1 + TAX_RATE_PHASE_2)) {
            tax_revenue = SALARY_TAX_RATE_PHASE_1 +
                          (salary - TAX_RATE_PHASE_1) * TAX_RATE_SECOND;          // 计算低于第二档次薪水临界点的应缴纳税额
        } else {
            tax_revenue = SALARY_TAX_RATE_PHASE_2 + (salary - TAX_RATE_PHASE_1 - TAX_RATE_PHASE_2) *
                                                    TAX_RATE_THIRD;            // 计算低于第三档次薪水临界点的应缴纳税额
        }
    }


    total_revenue = salary - tax_revenue;       // 实收 = 应收 - 税收
    printf("Salary is %.2lf, tax revenue is %.2lf, total revenue is %.2lf\n", salary, tax_revenue,
           total_revenue);
}
```

8．编写一个程序，显示一个提供加法、减法、乘法、除法的菜单。获得用户选择的选项后，程序提示用户输入两个数字,然后执行用户刚才选择的操作。该程序只接受菜单提供的选项。程序使用float类型的变量储存用户输入的数字，如果用户输入失败，则允许再次输入。进行除法运算时，如果用户输入О作为第2个数（除数)，程序应提示用户重新输入一个新值。该程序的一个运行示例如下:  
Enter the operation of your choice:  
a. add&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;s. subtract   
m. multiply&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d. divide   
q. quit   
a   
Enter first number: 22 .4   
Enter second number: one   
one is not an number.   
Please enter a number,such as 2.5，-1.78E8, or 3: 1   
22.4 + 1 =23.4   
Enter the operation of your choice:  
a. add&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;s. subtract  
m. multiply&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d. divide  
q. quit   
d   
Enter first number : 18. 4   
Enter second number: 0   
Enter a number other than 0: 0.2   
18.4 / 0.2 = 92   
Enter the operation of your choice :  
a. add&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;s. subtract   
m. multiply&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d. divide  
q. quit   
q   
Bye!

```
#include "stdio.h"

void show_menu(void);

float get_number(void);

int main(void) {
    char operate;
    float first, second;

    do {
        show_menu();
        operate = getchar();
        while (getchar() != '\n') {
//            printf(putchar(operate));
            continue;
        }

        switch (operate) {
            case 'a':
                printf("Enter first number: ");
                first = get_number();
                printf("Enter second number: ");
                second = get_number();
                printf("%g + %g = %g \n", first, second, first + second);
                break;
            case 's':
                printf("Enter first number: ");
                first = get_number();
                printf("Enter second number: ");
                second = get_number();
                printf("%g - %g = %g \n", first, second, first - second);
                break;
            case 'm':
                printf("Enter first number: ");
                first = get_number();
                printf("Enter second number: ");
                second = get_number();
                printf("%g * %g = %g \n", first, second, first * second);
                break;
            case 'd':
                printf("Enter first number: ");
                first = get_number();
                printf("Enter second number: ");
                while ((second = get_number()) == 0) {
                    printf("Enter a number other than 0: ");
                }
                printf("%g / %g = %g \n", first, second, first / second);
                break;
            case 'q':
                break;
            default:
                printf("Please enter a char, such as a, s, m, d and q: \n");
                while (getchar() != '\n');
//                printf(putchar(operate));
                break;
        }
        while (getchar() != '\n');
//            printf(putchar(operate));
//        }
    } while (operate != 'q');
    printf("Bye!\n");
    return 0;
}

void show_menu(void) {
    printf("Enter the operation of your choice: \n");
    printf("a. add                                 s. subtract\n");
    printf("m. multiply                            d. divide\n");
    printf("q. quit\n");
}

float get_number(void) {
    float f;
    char c;
    while (scanf("%g", &f) != 1) {
        while ((c = getchar()) != '\n') {
            putchar(c);
        }
        printf(" is not a number.\n");
        printf("Please enter a number, such as 2.5, -1, 78E8,or 3: ");
    }
    return f;
}
```