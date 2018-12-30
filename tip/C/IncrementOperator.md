# C语言自增(减)运算符总结

学C语言转眼怕是快10年了，对于这些细节问题有时候依然模糊不清，在此做个总结。

## ++/--运算符
这个符号估计很多初学者都知道并且“会用”，但坑比较多，先大体说明下：  
1. ++/--是自增/自减运算符号，对变量本身增加或减小一个长度单位，注意不是加一或减一
2. i++表示先赋值后自增，++i表示先自增再赋值，--符号同理，搞不清楚的建议随时小括号伺候
3. ++/--优先级较高，仅比`[]、()、.、->、-`低

## 自问自答
1. `for (i = 0; i < 10; i++, ++i)`，第二次for时i的值  
  答： 1 = 2， 因为这是for循环，和++优先级无关

2. `while (i++)`，假设i初值为0，第一次循环时i的值  
  答： i = 1，循环语句，先执行条件判断

3. `s[i++] = i++ + ++i`，设i = 0，问s[?] = ?  
  答： s[2] = 2，(能想清楚这道题我觉得++/--就不是问题了😉)先明确C语言是先运算后赋值，因此先看右边，`i++`返回0， 然后`+ ++i`的时候i先变成1，再自增一次变成2，所以`i++ + ++i`总的返回2。再看表达式的左值`s[i++]`，此时i=2，所以s[i++]相当于s[2]，赋值之后s[2] = 2，但是i最终值为3

4. 设`struct {int a; char b;} *s = 0x1234;`， 问执行s++后，s的地址是多少？  
  答： (s++) == 0x123c，因为结构体内存对齐长度为8，s自增一个长度(8)为0x1234+8

5. `struct {int a; char b;} s = {1, 'a'}`， 执行`++s.a`后是什么结果  
  答： s = {2, 'a'}，因为`.`的优先级高于`++`，所以相当于执行++(s.a)，容易误解为s本身自增操作

## 一个老段子
某人宣称自己发现了一个C语言的隐藏操作符：‘`-->`’可以算作是for循环的语法糖  
比如`for (i = 9; i > 0; i--)`你可以写成这样`while ()`
```c
int i = 10;
int sum = 0;
while (i --> 0)
  sum += i;
printf("sum = %d\n", sum); // output: 45
```

哈哈，基于此我也迅速地找到了一个C语言的究极隐藏操作符：‘`--^--`’  
它的功能是“吸收”左右值，输出-1，不论左右是什么数字，只要符号刚好相反😂
```c
int a = 123;
int b = -123;
printf("%d\n", a--^--b); //output: -1
```