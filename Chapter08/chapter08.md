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

```

