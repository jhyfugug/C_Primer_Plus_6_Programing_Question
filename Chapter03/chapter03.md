1.通过试验（即编写带有此类问题的程序）观察系统如何出来整数上溢、浮点数上溢和浮点数下溢出的情况。

编程分析：
    由于系统内对数据的存储和操作出来等原因，每一种数据类型都有其最大和最小值限制。实际编程中应当
充分考虑自己的程序需求，使用合适的数据类型。如果超过数据的限制，则会发生不可预期的错误，C语言在
limit.h和float.h头文件里预先定义了常见数据类型的限制。例如，float类型的最大值就是FLT_MAX，int
类型的最大值就是INT_MAX。下面代码大致展示了越界、精度限制和系统预定义的最值。
```
#include "stdio.h"
#include "float.h"
#include "limits.h"

int main(void) {
    int big_int = 2147483647;       // 有符号整数类型的最大值是2的31次方减1
    float float_bit = 3.4438;       // 浮点型数据的最大值一般为3.4E38
    float small_float = 10.0 / 3;         // 浮点型数据的有效位数一般为6位
    printf("The big int data is %d\n", big_int + 1);        // 最大数+1会导致越界，结果为 -2147483648
    printf("The big float data is %f\n", float_bit * 10);       // 浮点数最大数乘以10造成越界，输出inf。如果浮点数数据+1，小数据由于精确度限制，不会造成越界
    printf("The small float data is %f\n", small_float);        // 打印 3.333333，精度丢失
    printf("The MAX float data is %f\n", FLT_MAX);
    printf("The MAX int data is %d\n", INT_MAX);
    return 0;
}

```
2.编写一个程序，要求提示输入一个ASCII码值（如66），然后打印输入的字符。

```
#include "stdio.h"

int main(void){
    int input;
    // 提示输入码值
    printf("Please input code value：");
    scanf("%d", &input);
    printf("Your input value is %d, and char is %c\n", input, input);
    return 0;
}
```


3.编写一个程序，发出一声警报，然后打印下列文本。

```
#include "stdio.h"

int main(void){
    char ch = '\a';
    printf("%c", ch);
    printf("Starled by the sudden sound, Sally shouted, \n");
    printf("\"By the Great Pumpkin, wht was that!\"\n");
    return 0;
}
```

4.编写一个程序，读取一个浮点数，先打印成小数点形式，再打印成指数形式。然后，如果系统支持，再打印成p记数法（ 即十六进制记数法）。按以下格式输出（ 实际显示的指数位数因系统而异）：
Enter a floating-point value: 64.25
fixed-point notation: 64.250000
exponential notation: 6.425000e+01
p notation: 0x1.01p+6

```
#include <stdio.h>

int main(void){
    float input;    // 定义一个float变量
    printf("Enter a floating-point value: ");
    scanf("%f", &input);
    //scanf("Enter a floating-point value: %f\n", &input);
    printf("fixed-point notation: %f\n", input);
    printf("exponential notation: %e\n", input);
    printf("p notation: %a\n", input);
    return 0;
}
```

5.一年大约有3.156x10的7次秒，编写一个程序，提示用户输入年龄，然后显示该年龄对应的秒数。

```
#include <stdio.h>
#define SEC_PRE_YEAR 3.15e7

int main(void){
    float age, second;
    printf("Enter input your age: ");
    scanf("%f", &age);
    second = age * SEC_PRE_YEAR;
    printf("Your age is %.1f, and second is %e\n", age, second);
    return 0;
}
```

6.1个水分子的质量约为3.0*10^-23克。1夸脱水大约是950克。编写一个程序，提示用户输入水的夸脱数，并显示水分子数量。

```
#include <stdio.h>
#define water_gram_quality 3.156e-23
#define KUA_dehydration 950

int main(void){
    float water_quantity, water_quality;
    printf("Plaese input KUA_dehydration: ");
    scanf("%f", &water_quantity);
    water_quality = water_quantity*KUA_dehydration/water_gram_quality;
    printf("Water quality is %e \n", water_quality);
    return 0;
}
```
7.1英寸相当于2.54厘米。编写一个程序，提示用户输入身高（/英寸）,然后以厘米为单位显示身高

```
#include <stdio.h>

int main(void) {
    float pint, cup, ounce, large_spoon, teaspoon;
    printf("Please input cup quality: ");
    scanf("%f", &cup);
    pint = cup / 2;
    ounce = cup * 8;
    large_spoon = ounce * 2;
    teaspoon = large_spoon * 3;
    printf("pint is %f\n", pint);
    printf("cup is %f\n", cup);
    printf("ounce is %f\n", ounce);
    printf("large_spoon is %f\n", large_spoon);
    printf("teaspoon is %f\n", teaspoon);
    return 0;
}
```

8.在美国的体积测量系统中，1品脱等于2杯，1杯等于8盎司，1盎司等于2大汤勺，1大汤勺等于3茶勺。 编写程序，提示用户输入杯数，并以品脱、盎司、汤勺、茶勺为单位显示等价容量。 思考对于该程序，为何使用浮点类型比整数类型更合适

```
#include <stdio.h>

#define PINT_CUP 2
#define OUNCE 8
#define  LARGE_SPOON 2
#define SPOON_TEA 3

int main(void) {
    float pint, cup, ounce, large_spoon, teaspoon;
    printf("Please input cup quality: ");
    scanf("%f", &cup);
    pint = cup / PINT_CUP;
    ounce = cup * OUNCE;
    large_spoon = ounce * LARGE_SPOON;
    teaspoon = large_spoon * SPOON_TEA;
    printf("pint is %f\n", pint);
    printf("cup is %f\n", cup);
    printf("ounce is %f\n", ounce);
    printf("large_spoon is %f\n", large_spoon);
    printf("teaspoon is %f\n", teaspoon);
    return 0;
}
```

