第10题，针对第9题进行修改，不使用continue和goto语句。
若ch为非空换行符'\n'，则打印Step 1；若ch为b，则终止循环；若ch为c，则终止当前循环；如果ch为h，则打印Step 3；若为其他字符，则打印Step 2和Step 3。

```
#include "stdio.h"

int main(void) {
    char ch;
    while ((ch = getchar()) != '#') {
        if (ch != '\n') {
            printf("Step 1\n");
            if (ch == 'b') {
                break;
            }
            if (ch != 'c') {
                if (ch == 'h') {
                    printf("Step 3\n");
                } else {
                    printf("Step 2\n");
                    printf("Step 3\n");
                }
            }
        }
    }
    printf("Down\n");
    return 0;
}
```

1．编写一个程序读取输入，读到#字符停止，然后报告读取的空格数、换行符数和所有其他字符的数量。
```
#include "stdio.h"

# define STOP '#'
# define SPACE ' '
//编写一个程序读取输入，读到#字符停止，然后报告读取的空格数、换行符数和所有其他字符的数量。

int main (void) {
    int Space_Num = 0;
    int Return_Num = 0;
    int Letter_Num = 0;
    char ch;

    while ((ch = getchar()) != STOP) {
        if (ch == SPACE) {
            Space_Num++;
        } else if (ch == '\n') {
            Return_Num++;
        } else {
            Letter_Num++;
        }
    }
    printf("%10d个空格， %10d个换行符， %10d个其他字符", Space_Num, Return_Num, Letter_Num);

    return 0;
}
```

编写一个程序读取输入，读到#字符停止。程序要打印每个输入的字符以及对应的ASCII码(十进制)。一行打印8个字符。建议:使用字符计数和求模运算符（%）在每8个循环周期时打印一个换行符。读取整数直到用户输入0。输入结束后，程序应报告用户输入的偶数（不包括0)个数、这些偶数的平均值、输入的奇数个数及其奇数的平均值。
当前是2题和3题的组合题目

```
#include "stdio.h"

#define STOP '#'

//编写一个程序读取输入，读到#字符停止。程序要打印每个输入的字符以及对应的ASCII码(十进制)。一行打印8个字符。建议:使用字符计数和求模运算符（%）在每8个循环周期时打印一个换行符。读取整数直到用户输入0。输入结束后，程序应报告用户输入的偶数（不包括0)个数、这些偶数的平均值、输入的奇数个数及其奇数的平均值。

int main(void) {
    char ch;
    int num = 0, number = 0;            // 定义内部循环参数
    int ascii_number,ascii, even = 0, old = 0, sum_even = 0, sum_old = 0;
    float average_even = 0.0, average_old = 0.0;


    while ((ch = getchar()) != STOP) {
        num++;
        number = num % 8;
        ascii_number = ch;
        ascii = ascii_number % 2;

        if (ch == '0') {        // 判断当前值是否是0，是0的话，之间跳出整个循环
            printf("\n");
            break;
        } else {
            if (ascii == 0) {           // 判断当前值的奇偶性
                even++;
                sum_even = sum_even + ascii_number;
                //            printf("%d %c\n", ascii_number, ch);
                //            printf("%d %d\n", even, sum_even);
            } else {
                old++;
                sum_old = sum_old + ascii_number;
//            printf("%d %c\n", ascii_number, ch);
//            printf("%d %d\n", old, sum_old);
            }
        }
        // 按照每8列打印ch，最后一行不满第8列的情况，通过最后的换行来完成
        if (number == 0) {
            printf("%10c", ch);
            printf("\n");
        } else {
            printf("%10c", ch);
        }
    }
    if (even != 0) {
        average_even = (float) sum_even / even;
    } else {
        average_even = 0.0;
    }

    if (old != 0) {
        average_old = (float) sum_old / old;
    } else {
        average_old = 0.0;
    }
//    average_even = (float)sum_even / even;
//    average_old = (float)sum_old/ old;
    printf("\n");
    printf("even number is %d, even number 's average is %.2lf, old number is %d, old number 's average is %.2lf.\n", even,
           average_even, old, average_old);

    return 0;
}
```

2.编写一个程序读取输入，读到#字符停止。程序要打印每个输入的字符以及对应的ASCII码(十进制)。一行打印8个字符。建议:使用字符计数和求模运算符（%）在每8个循环周期时打印一个换行符。

```
#include "stdio.h"
#define STOP '#'
#define CYCLE_VALUE 8
//编写一个程序读取输入，读到#字符停止。程序要打印每个输入的字符以及对应的ASCII码(十进制)。一行打印8个字符。建议:使用字符计数和求模运算符（%）在每8个循环周期时打印一个换行符。

int main(void) {
    char ch;
    int num = 0, number = 0;            // 定义内部循环参数
    int ascii_number;


    while ((ch = getchar()) != STOP) {
        num++;
        number = num % CYCLE_VALUE;
        ascii_number = ch;

        // 按照每8列打印ch，最后一行不满第8列的情况，通过最后的换行来完成
        if (number == 0) {
            printf("%10c", ascii_number);
            printf("\n");
        } else {
            printf("%10c", ascii_number);
        }
    }

    return 0;
}
```

3．编写一个程序，读取整数直到用户输入0。输入结束后，程序应报告用户输入的偶数（不包括0)个数、这些偶数的平均值、输入的奇数个数及其奇数的平均值

```
#include "stdio.h"

#define STOP 0

//编写一个程序，读取整数直到用户输入0。输入结束后，程序应报告用户输入的偶数（不包括0)个数、这些偶数的平均值、输入的奇数个数及其奇数的平均值

int main(void) {
    int value, bool;
    int num = 0, even = 0, old = 0, sum_even = 0, sum_old = 0;
    float average_even = 0.0, average_old = 0.0;

    printf("Please input a number:\n");
    bool = scanf("%d", &value);
    while (value != STOP && bool == 1) {
        num = value % 2;
        if (num == 0) {
            even++;
            sum_even = sum_even + value;
        } else {
            old++;
            sum_old = sum_old + old;
        }
        printf("Please again input a number:\n");
        bool = scanf("%d", &value);
    }
    if (even != 0) {
        average_even = (float) sum_even / even;
    } else {
        average_even = 0.0;
    }

    if (old != 0) {
        average_old = (float) sum_old / old;
    } else {
        average_old = 0.0;
    }
    printf("even number is %d, even number 's average is %.2lf, old number is %d, old number 's average is %.2lf.\n", even,
           average_even, old, average_old);

    return 0;
}
```

4．使用if else 语句编写一个程序读取输入，读到#停止。用感叹号替换句号，用两个感叹号替换原来的感叹号，最后报告进行了多少次替换。

```
#include "stdio.h"

#define STOP '#'
#define MARK '!'
#define FULL '.'
#define DOUBLE_MARK '!!'

//使用if else 语句编写一个程序读取输入，读到#停止。用感叹号替换句号，用两个感叹号替换原来的感叹号，最后报告进行了多少次替换。

int main(void) {
    char ch;
    int number = 0;

    while ((ch = getchar()) != STOP) {
        printf("%10c", ch);
        if (ch == FULL) {
            ch = MARK;
            printf("%10c", ch);
            number++;
        } else if (ch == MARK) {
            printf("!!");
            number++;
        } else {
            continue;
        }
    }
    printf("\n");
    printf("Charge's number equal %d", number);

    return 0;
}


```

5.使用switch重写练习4。

```
#include "stdio.h"

#define STOP '#'
#define MARK '!'
#define FULL '.'
#define DOUBLE_MARK '!!'

//使用if else 语句编写一个程序读取输入，读到#停止。用感叹号替换句号，用两个感叹号替换原来的感叹号，最后报告进行了多少次替换。

int main(void) {
    char ch;
    int number = 0;

    while ((ch = getchar()) != STOP) {
//        printf("%10c", ch);
        switch (ch) {
            case FULL: {
                ch = MARK;
                printf("%c", ch);
                number++;
                break;
            }
            case MARK: {
                printf("!!");
                printf("");
                number++;
                break;
            }
            default: {
                putchar(ch);
            }
        }
    }
    printf("\n");
    printf("Charge's number equal %d", number);


    return 0;
}

```

6．编写程序读取输入，读到#停止，报告ei出现的次数。
（注意：该程序要记录前一个字符和当前字符。用“Receive your eieio award”这样的输入来测试.）

```
#include "stdio.h"

#define STOP '#'
#define FIRSTCHAR 'e'
#define SECONDCHAR 'i'

//编写程序读取输入，读到#停止，报告ei出现的次数。
//（注意：该程序要记录前一个字符和当前字符。用“Receive your eieio award”这样的输入来测试.）

int main(void) {
    char ch, prech;
    int number = 0;

    printf("Please input mangy character:\n");
    while ((ch = getchar()) != STOP) {
//        printf("%10c", ch);
        if (ch == FIRSTCHAR) {
            prech = ch;
            continue;
        }
        if (ch == SECONDCHAR) {
            if (prech == FIRSTCHAR) {
                number++;
                continue;
            } else {
                continue;
            }
        }
    }
    printf("\n");
    printf("This ei's number equal %d", number);


    return 0;
}

```

7．编写一个程序，提示用户输入一周工作的小时数，然后打印工资总额、税金和净收入。做如下假设:  
a．基本工资= 10.00美元/小时   
b. 加班（超过40小时）= 1.5倍的时间   
c. 税率:前300美元为15%   
续150美元为20%   
余下的为25%   
用#define定义符号常量。不用在意是否符合当前的税法。

```
#include "stdio.h"

#define BASIC_SALARY 10.00          // 基础时薪
#define MAGNIFICATION 1.5           // 倍率
#define WEEK_TIME 40            // 每周基础工作时长
#define WEEK_BASIC_SALARY BASIC_SALARY * WEEK_TIME        // 基础工作时长满额薪资
#define TAX_RATE_BASIC 0.15         // 交税第一档次税率
#define TAX_RATE_SECOND 0.2         // 交税第二档次税率
#define TAX_RATE_THIRD 0.25         // 交税第三档次税率
#define TAX_RATE_PHASE_1 300        // 薪水第一档次临界点
#define TAX_RATE_PHASE_2 150        // 薪水第二档次临界点
#define SALARY_TAX_RATE_PHASE_1 TAX_RATE_PHASE_1 * TAX_RATE_BASIC           // 满额第一薪水应缴税收
#define SALARY_TAX_RATE_PHASE_2 SALARY_TAX_RATE_PHASE_1 + TAX_RATE_PHASE_2 * TAX_RATE_SECOND    // 满额第二薪水应缴税收

int main(void) {

    int time = 0;
    float salary = 0.0, tax_revenue = 0.0, total_revenue = 0.0;
    printf("Please input time:\n");

    while (scanf("%d", &time) == 1) {
        if (time <= WEEK_TIME && time >= 0) {
            salary = time * BASIC_SALARY;           // 计算基础周工作时长的薪资
        } else if (time > WEEK_TIME) {
            salary = WEEK_BASIC_SALARY + (time - WEEK_TIME) * BASIC_SALARY * MAGNIFICATION;         // 计算超过基础周工作时长的薪资
        } else {
            printf("Please input greater than 0");
            break;
        }

        if (salary <= TAX_RATE_PHASE_1) {
            tax_revenue = salary * TAX_RATE_BASIC;      // 计算低于第一档次薪水临界点的应缴纳税额
        } else if (salary > TAX_RATE_PHASE_1 && salary <= (TAX_RATE_PHASE_1 + TAX_RATE_PHASE_2)) {
            tax_revenue = SALARY_TAX_RATE_PHASE_1 + (salary - TAX_RATE_PHASE_1) * TAX_RATE_SECOND;          // 计算低于第二档次薪水临界点的应缴纳税额
        } else {
            tax_revenue = SALARY_TAX_RATE_PHASE_2 + (salary - TAX_RATE_PHASE_1 - TAX_RATE_PHASE_2) * TAX_RATE_THIRD;            // 计算低于第三档次薪水临界点的应缴纳税额
        }
        total_revenue = salary - tax_revenue;       // 实收 = 应收 - 税收
        printf("Salary is %.2lf, tax revenue is %.2lf, total revenue is %.2lf\n", salary, tax_revenue, total_revenue);
    }
    printf("Down\n");

    return 0;
}

```

8．修改练习7的假设a，让程序可以给出一个供选择的工资等级菜单。使用switch完成工资等级选择。   
运行程序后，显示的菜单应该类似这样:  
Enter the number corresponding to the desired pay rate or action:1) $8.75/hr   
2)$9.33/hr   
3)$10.00 /hr   
4)$11.20 /hr  
5）quit
如果选择1-4其中的一个数字，程序应该询问用户工作的小时数。程序要通过循环运行，除非用户输入5。如果输入1~5以外的数字，程序应提醒用户输入正确的选项，然后再重复显示菜单提示用户输入。使用#define创建符号常量表示各工资等级和税率。

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
    printf("1) $8.75/hr   \n"
           "2)$9.33/hr   \n"
           "3)$10.00 /hr   \n"
           "4)$11.20 /hr  \n"
           "5）quit\n");

    while ((flag == 0 && scanf("%d", &number) == 1)) {

        switch (number) {
            case 1: {
                time_salary = salary_time_1;
                show_salary(time_salary);
                flag = 1;
                break;
            }
            case 2: {
                time_salary = salary_time_2;
                show_salary(time_salary);
                flag = 1;
                break;
            }
            case 3: {
                time_salary = salary_time_3;
                show_salary(time_salary);
                flag = 1;
                break;
            }
            case 4: {
                time_salary = salary_time_4;
                show_salary(time_salary);
                flag = 1;
                break;
            }
            case 5: {
                printf("quit\n");
                break;
            }
            default: {
                printf("Please enter correct number:");
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

9．编写一个程序，只接受正整数输入，然后显示所有小于或等于该数的素数。

```
#include <stdbool.h>
#include "stdio.h"
#include "math.h"

int main(void) {

    int number, remainder_number, remainder_k;
    bool flag = 1;

    printf("Please input a number and greater than 0:");
    while (scanf("%d", &number) == 1 && flag == 1) {

        if (number == 1) {
            printf("1不是素数！");
            printf("Please also input a number:\n");
            flag = 1;
            continue;
        }

        for (int i = 2; i <= number; i++) {         // loop less than number's positive integer equal i
//            remainder_number = number % i;
//            printf("remainder_number = %d, i = %d\n", remainder_number, i);
            for (int j = 2; j < i; j++) {           // loop less than i's positive integer equal j
                remainder_k = i % j;
//                printf("remainder_k = %d, j = %d\n", remainder_k, j);
                if (remainder_k == 0) {             // 判断是否为素数(如果余数都不为0，则为素数）
                    flag = 0;
                    break;
                } else {
                    flag = 1;
                }
//                printf("%d\n", flag);
            }
            if (flag == 1) {
                printf("%5d", i);
            }
        }
        flag = 1;
        printf("\n");
    }
    printf("Down\n");

    return 0;
}
```

10.1988年的美国联邦税收计划是近代最简单的税收方案。它分为4个类别，每个类别有两个等级。
下面是该税收计划的摘要（美元数为应征税的收入):  
类别 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;税金   
单身&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;17850美元按15%计，超出部分按28%计   
户主&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;23900美元按15%计，超出部分按28%计   
已婚，共有&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;29750美元按15%计，超出部分按28%计   
已婚，离异&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;14875美元按15%计，超出部分按28%计

例如，一位工资为20000美元的单身纳税人，应缴纳税费0.15×17850+0.28×（20000-17850）美元。编写一个程序，让用户指定缴纳税金的种类和应纳税收入，然后计算税金。程序应通过循环让用户可以多次输入。

```
#include "stdio.h"
#define SINGLE 1
#define HOUSEHOLDER 2
#define MARRIED_CO_OWNERSHIP 3
#define MARRIED_AND_DIVORCED 4
#define TAX_ONE 0.15
#define TAX_two 0.28

double choice_personnel_type (int type);
double salary_calculation_tax (double money, double salary);

int main(void) {

    int type, flag = 1, prime = 1;
    double salary, money, tax = 0.0;

    printf("Choice a type:\n");
    while ((flag == 1) && (scanf("%d", &type) == 1)) {
        if (type > 0) {
            flag = 0;
//            printf("%d", flag);
            money = choice_personnel_type (type);
//        printf("%.2lf\n", money);
            printf("Enter salary:\n");
            while ((prime == 1) && (scanf("%lf", &salary) == 1)) {
                tax = 0.00;
//            printf("salary is %.2lf\n", salary);
//            printf("money is %.2lf\n", money);
                tax = salary_calculation_tax(money, salary);
                if (tax >= 0.00 ) {
                    printf("tax is %.2lf\n", tax);
                    prime = 0;
                }
            }
        } else {
            flag = 1;
            printf("Your choice is error!\n");
            printf("Enter also a type:\n");
        }

    }
     printf("Down!");

    return 0;
}


double choice_personnel_type (int type) {
    float money = 0.00;
    int flag = 1;
    switch (type) {
        case 1: {
            money = 17850;
            flag = 1;
            break;
        }
        case 2: {
            money = 23900;
            break;
        }
        case 3: {
            money = 29750;
            break;
        }
        case 4: {
            money = 14875;
            break;
        }
        default: {
            printf("Your input number error!");
            printf("Enter also a type:\n");
        }
    }

    return money;
}

double salary_calculation_tax (double money, double salary) {
    float tax;
    int prime;
    if (salary >= 0 && salary <= money) {
        tax = salary * TAX_ONE;
    } else if (salary > money) {
        tax = money * TAX_ONE + (salary - money) * TAX_two;
    } else {
        printf("Please input correct salary:\n");
    }

    return tax;
}
```

11.ABC邮购杂货店出售的洋蓟售价为2.05美元/磅，甜菜售价为1.15美元/磅，胡萝卜售价为1.09美元/磅。在添加运费之前，100美元的订单有5%的打折优惠。少于或等于5磅的订单收取6.5美元的运费和包装费，5磅～20磅的订单收取14美元的运费和包装费，超过20磅的订单在14美元的基础上每续重Ⅰ磅增加0.5美元。编写一个程序，在循环中用switch语句实现用户输入不同的字母时有不同的响应，即输入a的响应是让用户输入洋蓟的磅数，b是甜菜的磅数，c是胡萝卜的磅数，q是退出订购。程序要记录累计的重量。即，如果用户输入4磅的甜菜，然后输入5磅的甜菜，程序应报告9磅的甜菜。然后，该程序要计算货物总价、折扣（如果有的话)、运费和包装费。随后，程序应显示所有的购买信息:物品售价、订购的重量（单位:磅)、订购的蔬菜费用、订单的总费用、折扣（如果有的话)、运费和包装费，以及所有的费用总额。

```
#include "stdio.h"

#define ARTICHOKE 2.05
#define BEET 1.15
#define CARROT 1.09
#define DOLLAR 100.0
#define DISCOUNT 0.5
#define POUND_1 5.0
#define POUND_2 20.0
#define PACKAGING_FEE_ONE 6.5
#define PACKAGING_FEE_TWO 14
#define PACKAGING_FEE_THREE 0.5

int main(void) {
    double a = 0.0, b = 0.0, c = 0.0, num_Artichokes = 0.0, num_beets = 0.0, num_carrot = 0.0;
    double discount = 0.0, sum_money = 0.0, sum_num = 0.0, total_money = 0.0, freight = 0.0;
    char ch;

    printf("Enter a to buy artichokes, b for beets, ");
    printf("c for carrots, q to quit: ");
    while ((ch = getchar()) != 'q') {

        switch (ch) {
            case 'a': {
                printf("Enter artichokes is pound：\n");
                scanf("%lf", &a);
                num_Artichokes += a;
                getchar();
                break;
            }
            case 'b': {
                printf("Enter beets is pound：\n");
                scanf("%lf", &b);
                num_beets += b;
                getchar();
                break;
            }
            case 'c': {
                printf("Enter carrots is pound：\n");
                scanf("%lf", &c);
                num_carrot += c;
                getchar();
                break;
            }
            default: {
                printf("You input letter is error！\n");
            }
        }
    }

    sum_money = num_Artichokes * ARTICHOKE + num_beets * BEET + num_carrot * CARROT;
    sum_num = num_Artichokes + num_beets + num_carrot;
    if (sum_money > DOLLAR) {
        discount = DOLLAR * DISCOUNT;
        sum_money = sum_money - discount;
    }

    if (sum_num >= 0  && sum_num <= POUND_1) {;
        freight = PACKAGING_FEE_ONE;
        total_money = sum_money + freight;
    } else if ( sum_num < POUND_2) {
        freight = PACKAGING_FEE_TWO;
        total_money = sum_money + freight;
    } else {
        freight = PACKAGING_FEE_TWO + (sum_num - POUND_2) * PACKAGING_FEE_THREE;
        total_money = sum_money + freight;
    }

    if (num_Artichokes != 0) {
        printf("Artichoke's price is %.2lf/pound, pound is %.2lf\n", ARTICHOKE, num_Artichokes);
    }
    if (num_beets != 0) {
        printf("Beet's price is %.2lf/pound, pound is %.2lf\n", BEET, num_beets);
    }
    if (num_carrot) {
        printf("Carrot's price is %.2lf/pound, pound is %.2lf\n", CARROT, num_carrot);
    }

    printf("Commodity payment is %.2lf, discount is %.2lf, package and fee is %.2lf, total price is %.2lf\n", sum_money, discount, freight, total_money);

    printf("Down\n");

    return 0;
}

```