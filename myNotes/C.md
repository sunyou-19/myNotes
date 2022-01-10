/*
1、 gets函数从标准输入读取一行文本并把它存储于作为参数传递给它的数组中。一行输入由一串字符组成，以一个换行符('\n')结尾gets函数丢弃换行符，并在该行的末尾存储一个NUL字节（一个NUL字节是指字节模式为全零的字节，类似'\0'这样的字符常量）。然后，gets函数返回一个非NULL值，表示该行已被成功读取。当gets函数被调用但事实上不存在输入行，它就返回NULL值，表示它到达了输入的末尾。

2、 getchar函数从标准输入读取一个字符并返回它的值。如果输入中不再存在任何字符，函数就会返回常量EOF，用于提示文件的结尾。

3、
（1）EOF的值通常为-1，一般应用于文本文件中，因为ASCII码是0-127，没有负数。
（2）字符串是由NUL字节结尾的字符
（3）翻译过程：源文件通过编译转换为目标代码，各个目标文件由链接器捆绑在一起，形成一个单一而完整的可执行程序。
（4）字面值（字面值常量），指定它自身的值不可改变
（5）枚举类型就是指它的值为符号常量而不是字面值的类型。
```
enum Jar_Type {CUP,PINT,QUART,HALF_GALLON,GALLON};
```
（6）浮点数：如 `3.1415926  1e10  25.  .5  6.023e23`
（7）指针：表示一个地址，指向某个内存单元。
（8）字符串常量；就是以NUL字节结尾的零个或多个字符，字符串通常存储在字符数组中。
（9）正确声明指针的方式： `int *a, *b, *c;`
（10）当函数不是显式地声明返回值地类型时，它默认为整型。
（11）typedef的妙用：它允许为各种数据类型定义新名字
（12）对于常量使用const声明时，要对变量进行初始化
（13）#define指令是创建名字常量的机制

7、
（1）
作用域：文件作用域、函数作用域、代码块作用域和原型作用域
文件作用域：任何所有代码块之外声明的标识符都具有文件作用域
原型作用域：适用于在函数原型中声明的参数名，且该参数名并非必需
函数作用域：
（2）链接属性：源文件被编译之后，多个目标文件链接在一起，形成可执行程序。
链接属性有三种：`external、internal、none`
没有链接属性的标识符（none）总是被当作单独的个体，也就是每个文件中该相同的标识符的多个声明被当作不同的实体
internal：在同一个源文件内的所有声明中都指同一个实体，但位于不同源文件多个声明分属不同的实体
external链接属性的标识符：该标识符的所有声明都属于同一个实体。
（3）关键字extern和static用于在声明中修改标识符的链接属性。
static可修改变量为intenal链接属性
（4）存储类型：普通内存，运行时堆栈，硬件寄存器
凡是在任何代码块之外声明的变量总是存储于静态内存中
在代码块内部声明的变量是存储于堆栈中
（5）break语句，用于跳出最近的循环和switch语句
9、**操作符**
（1）算术操作符：`+、-、*、/、%`
（2）移位操作符：`<<、>>`
（3）位操作符：`^、&、|`
（4）赋值：`=`
（5）单目操作符：`! ++ - & ~ -- + () sizeof`
（6）关系操作符：`> >= < <= != ==`
（7）逻辑操作符：`&& ||`
（8）条件操作符：`exp1 ? exp2 : exp3`
（9）逗号操作符：整个逗号表达式的值就是最后那个表达式的值
（10）下标引用、函数调用和结构成员
（11）操作符的优先级、结核性、以及是否控制执行的顺序
![查看操作符优先级](sypr.png)
10、**指针**
（1）两个指向相同类型数据的指针相减是两个指针在内存中的距离（即以数据元素的长度为单位）
```
int a;
int *p = &a;
int **q = &p;
```
(2)声明一个指针变量并不会自动分配任何内存，指针必须初始化。
11、**函数**
*问题*：`float a = 0.1; //机器如何完成真值到float的转化`
12、stdarg宏，可变参数列表通过宏来实现，这些宏定义于stdarg.h文件中，
这个头文件声明了一个类型va_list和三个宏——va_start、va_arg和va_end
13、**数组**
（1）声明一个数组时，编译器将根据声明所指定的元素数量为数组保留内存空间，然后再创建数组名，它的值是一个常量，指向这段空间的起始地址。声明一个指针变量时，编译器只为指针本身保留内存空间，它并不为任何类型值分配内存空间。
（2）静态数组初始化为零，自动变量数组如果没有显式初始化，其值不为0。
（3）字符数组的初始化；
```
char message[] = {'h','e','l','o',0};
char message[] = "hello";  //字符数组
char *message = "Hello";   //字符串常量，不可被修改
```
14、**指针与数组**
```
int (*p)[10];  //相当于二维数组
int *p[10];  //指针数组，数组元素为int指针类型。
const char keywords[] = {"abc","how","what"};
int len = sizeof(keywords)/sizeof(keywords[0]); //通过sizeof可以求数组长度。sizeof计算变量所占字节
```
*问题*
>变量array1和array2有什么区别
```
void function(int array1[10])
{
    int array2[10];
}
int const a[] = {1,2,3,4};   //array read-only
```
15、字符串、字符和字节
（1）库函数strlen的原型：`size_t strlen(char const *string)`，size_t是一个无符号整数类型。
```
char *x = "balabala";
if (strlen(x) - 10 >= 0)  //左式为无符号数
```
（2）用于复制字符串的函数是strcpy
`char *strcpy(char *dst, char const *src)`
dest必须是字符数组或者是一个指向动态分配内存的数组指针，不能使用字符串常量。
（3）连接字符串strcat，将一个字符串连接到另一个字符串的后面。
`char *strcat(char *dst, char const *src);`
（4）字符串比较strcmp，比较两个字符串对应的字符逐个进行比较，直到发现不匹配为止，
`int strcmp(char const *s1, char const *s2)`
如果s1小于s2，strcmp函数返回一个小于零的值，如果s1大于s2，函数返回一个大于零的值，如果两个字符串相等，函数就返回零。
```
char *strncpy(char *dst, char const *src, size_t len);         //其结果不会以NUL字节结尾  
char *strncat(char *dst, char const *src, size_t len);
int strncmp(char const *s1, char const *s2,size_t len);
```
（5）查找一个字符strchr和strrchr函数
```
char *strchr(char const *str, int ch);   //return a pointer to the first occurrence of ch, return NULL if ch is not in str;
char *strrchr(char const *str, int ch);  //return a pointer to the last occurrence of ch, return NULL if ch is not in str;
```
（6）查找任何几个字符strpbrk，查找任何一组字符第一次在字符串中出现的位置。
`char *strpbrk(char const *str, char const *group); `返回一个指向str中第1个匹配group中任何一个字符的字符位置。
（7）查找一个字串strstr函数
`char *strstr(char const *s1, char const *s2); `
在s1中查找整个s2第1次出现的起始位置，并返回一个指向该位置的指针，如果s2没有在s1中出现，函数返回一个NULL指针。如果第二个参数是一个空字符串，函数就返回s1。
（8）查找一个字符串前缀strspn和strcspn函数
```
size_t strspn(char const *str, char const *group);    //group字符串指定一个或多个字符，strspn返回str起始部分匹配group中任意字符的字符数。
size_t strcspn(char const *str, char const *group);
``` 
（9）查找标记strtok函数
`char *strtok(char *str, char const *sep)`
sep是个字符串，定义了用作分隔符的字符集合
strtok找到str的下一个标记，并将其用NUL结尾，然后返回一个指向这个标记的指针。
（10）字符分类
![](images/QQ截图20220110085314.png)
（11）字符转换
```
int tolower(int ch);
int toupper(int ch);
```
（12）内存操作。根据定义，字符串由一个NUL字节结尾，所以字符串内部不能包含任何NUL字符。
```
void *memcpy(void *dst, void const *src,size_t length);
void *memmove(void *dst, void const *src,size_t length);
void *memcmp(void const *a, void const *b,size_t length);
void *memchr(void const *a, int ch,size_t length);
void *memset(void *a, int ch, size_t length);
```
###结构与联合

```
struct abc{};   //abc是标签
typedef struct {}abcd;   //adcd是类型名
```
（1）结构变量的成员是通过点操作符(.)访问的，点操作符接受两个操作数，左操作数就是结构变量的名字，右操作数就是需要访问的成员的名字。
（2）结构的存储分配
（3）位段(bit field)，位段成员必须声明为int、signed int或unsigned int类型，其次，在成员名的后面是一个冒号和一个整数，这个整数指定该位段所占用的位的数目。
```
struct CHAR
{
    unsigned ch : 7;
    unsigned font : 6;
    unsigned size : 19;
};
struct CHAR ch1;
```
（4）联合(union)，其所有成员引用的是内存中的相同位置。
```
union 
{
    float f;
    int i;
}fi;
fi.f = 3.1415926;
printf("%d\n",fi.i);   //将fi解释为int型
```
联合的长度就是最大成员的长度。

###动态分配内存
（1）C语言库提供了两个函数，malloc和free，分别用于执行动态内存分配和释放。
```
void *malloc(size_t size);   //函数原型
void free(void *pointer);
void *calloc(size_t num_elements, size_t element_size);  //返回指向内存的指针之前把它初始化为0
void realloc(void *ptr, sizeof_t new_size);  //用于修改一个原先已经分配的内存块的大小
```
（2）malloc分配的是一块连续的内存，这些函数维护一个可用内存池，当被调用时，malloc从内存池中提取一块合适的内存。
（3）动态内存分配最常见的错误就是忘记检查所请求的内存是否成功分配。
```
int *p;
p = (int *)malloc(sizeof(int)*10);
if (p == NULL)
{
    printf("Malloc fail");
    exit(1);
}
```
（4）当动态分配的内存不再需要使用时，它应该被释放，分配内存但在使用完毕后不释放将引起内存泄漏。
*问题*
>编写一个函数，从标准输入读取一-个字符串， 把字符串复制到动态分配的内存中，
>并返回该字符串的拷贝。这个函数不应该对读入字符串的长度作任何限制!
