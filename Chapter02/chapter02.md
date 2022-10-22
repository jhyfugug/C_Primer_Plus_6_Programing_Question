1.编写一个程序，调用一次 printf()函数，把你的姓名打印在一行。再调用一次 printf()函数，把你的姓名分别打印在两行。然后，再调用两次printf()函数，把你的姓名打印在一行。输出应如下所示（当然要把示例的内容换成你的姓名）：

Gustav Mahler       <--第1次打印的内容
Gustav              <--第2次打印的内容
Mahler              <--仍是第2次打印的内容
Gustav Mahler       <--第3次和第4次打印的内容

```
#include <stdio.h>

int main(void){
    printf("Gustav Mahler\n");
    printf("Gustav\n");
    printf("Mahler\n");
    printf("Gustav ");
    printf("Mahler\n");
    return 0;
}
```
2.编写一个程序，打印你的姓名和地址。
```
#include "stdio.h"

int main(void){

    char name[20], address[40];         // 定义两个char类型的数组，分别用于记录姓名和地址
    printf("Please input your name and your address:\n");
    scanf("%s %s", name, address);              // PS:scanf()函数遇到空格和换行就会跳出读取
    printf("Your name is %s, your address is %s", name, address);

    return 0;
}
```

3.编写一个程序把你的年龄转换成天数，并显示这两个值。这里不用考虑闰年的问题。
```
#include <stdio.h>

//3.编写一个程序把你的年龄转换成天数，并显示这两个值。这里不用考虑闰年的问题。

int main(void){
    const int days_of_year = 365;
    int age, days;      // 定义年龄和天数
    printf("Please input your age:\n");
    if (scanf("%d", &age) == 1){
        days = age * days_of_year;
        printf("Your age is %d, and have %d days.\n", age, days);
    }
    return 0;
}
```
4.编写一个程序，生成以下输出：

For　he's　a　jolly　good　fellow!

For　he's　a　jolly　good　fellow!

For　he's　a　jolly　good　fellow!

Which　nobody　can　deny!

除了 main()函数以外，该程序还要调用两个自定义函数：一个名为 jolly()，用于打印前 3 条消息，调用一次打印一条；另一个函数名为deny()，打印最后一条消息。

```
#include "stdio.h"

void jolly(void);

void deny(void);


int main(void) {

    jolly();
    jolly();
    jolly();
    deny();

}

void jolly(void) {
    printf("For he's a jolly good fellow!\n");
}

void deny(void) {
    printf("Which nobody can deny!\n");
}
```
5.编写一个程序，生成如下输出：函数

Brazil, Russia, India, Chinaspa

India, China,code

Brazil, Russiathree

除了main()之外，该程序还要调用两个自定义函数：一个名为br()，调用一次打印一次"Brazil, Russia"；另外一个名为ic()，调用一次打印一次"India, China"。其余内容在main()函数中完成。

```
#include <stdio.h>

void br(void);

void ic(void);

int main(void) {
    br();
    printf(", ");
    ic();
    printf("\n");
    ic();
    printf("\n");
    br();

    return 0;
}

void br(void) {
    printf("Brazil, Russia");
}

void ic(void) {
    printf("India, China");
}
```
6.编写一个程序,创建一个整型变量toes,并将toes设置为10。程序中还要计算toes的两倍和toes的平方。该程序应打印3个值,并分别描述以示区分
```
#include <stdio.h>

int main(void) {
int toes = 10;           //define a toes variable, and initialization is 10

    printf("toes is %d, toes's double is %d, toes square is %d.", toes, 2 * toes, toes * toes);
}
```

7.许多研究表明，微笑益处多多。编写一个程序，生成以下格式的输出：

Smile!Smile!Smile!

Smile!Smile!

Smile!

该程序要定义一个函数，该函数被调用一次打印一次“Smile!”，根据程序的需要使用该函数。

```
#include <stdio.h>

void smile(void);       //define a function statement

int main(void){
    for (int i = 3; i > 0; i--) {
        for (int j = i; j > 0; j--) {
            smile();
        }
        printf("\n");
    }
    return 0;
}

void smile(void){
    printf("Smile!");
}
```

8.在C语言中，函数可以调用另一个函数。编写一个程序，调用一个名为one_three()的函数。该函数在一行打印单词“one”，再调用第2个函数two()，然后在另一行打印单词“three”。two()函数在一行显示单词“two”。main()函数在调用 one_three()函数前要打印短语“starting now:”，并在调用完毕后显示短语“done!”。因此，该程序的输出应如下所示：

starting　now:

one

two

three

done!

```
#include <stdio.h>


void one_three(void);

void two(void);

int main(void) {
    printf("starting now:\n");
    one_three();
    printf("done!\n");
    return 0;
}

void one_three(void) {
    printf("one\n");
    two();
    printf("three\n");
}

void two(void) {
    printf("two\n");
}
```