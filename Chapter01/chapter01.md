1.你刚被MacroMuscle有限公司聘用。该公司准备进入欧洲市场，需要一个把英寸单位转换为厘米单位(1英寸=2.54厘米)的程序。该程序要提示用户输入英寸值。你的任务是定义程序目标和设计程序。
```
#include <stdio.h>
#define INCHCHARGECM 2.54       //定义一个字符常量
int main() {
    float inch;     //声明
    printf("Print input inch's value:\n");
    while(scanf("%f", &inch) == 1)
        printf("Your input %f inch equal %f cm", inch, inch * INCHCHARGECM);
    printf("Down!");
    return 0;
}

```