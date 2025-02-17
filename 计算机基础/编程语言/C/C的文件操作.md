# C的文件操作

# 文件的两种模式

在计算机中所有文件的内容都以二进制形式（0或1）进行存储，但如果文本使用二进制编码的字符（如ASCII或Unicode）来表示*文本*，则该文件称为**文本文件**；如果文件中的二进制值代表*机器语言代码*或*数值数据*或*图片*或*音乐编码*，则该文件就是**二进制文件。**

文本文件和二进制文件区别在于逻辑层面，而非物理层面，两者只是在编码层次上有差异。例如：存放以下数据

> 5678

文本文件会存放为：

> 00110101   00110110   00110111   00111000 (ASCII)

二进制文件会存放为：

> 00010110   00101110

类似于`char`​类型与`int`​类型的区别

如果要准确的表示数值（如浮点数），则需要存储为二进制文件；因为文本文件相当于把数值的每一位数字转化为字符，可能会导致精度丢失

# 指向标准文件的指针

|标准输入|stdin|键盘|
| :---------| :-------| :-------|
|标准输出|stdout|显示器|
|标准错误|stderr|显示器|

# 函数介绍

## 打开/关闭文件

### fopen()

#### 函数原型

​`FILE *fopen(const char *__restrict__ _Filename, const char *__restrict__ _Mode)`​

即fopen("文件名","打开模式")。

需要将fopen返回的FILE指针赋给声明的FILE指针。

#### 模式(Mode)字符串

|"r"|只读|
| :--------------------------------------------------| :-------------------------------------------------------------------------------------------------------------|
|"w"|只写，会删去原有数据，文件不存在则新建|
|"a"|只写，不会删去原有数据，可在文件末尾添加内容，文件不存在则新建|
|"r+"|更新，可读写|
|"w+"|更新，可读写，会删去原有数据，文件不存在则新建|
|"a+"|更新，可读写，只可以从末尾添加，不会删去原有数据，文件不存在则新建|
|"rb" "wb" "ab" rb+" "r+b" "wb+" "w+b" "ab+" "a+b"|以二进制模式打开|
|"wx" "wbx" "w+x" "wb+x" "w+bx"|如果文件已经存在或者以独占模式打开文件，则返回失败（就是一定会创建新的，如果以前存在过就不会操作，防止误删）|

### fclose()

​`int fclose(FILE *_File)`​，即fclose("文件名")。

关闭一个已经打开的文件，若关闭成功返回`0`​。

因为打开后文件，文件会占用着内存，如果不及时关闭已经处理完毕的文件，可能会导致内存溢出。

## 文本文件I/O

### 从文件中读取

#### getc()

​`int getc(FILE *文件指针)`​，从文件中读取单个字符。

可以将`getchar()`​视为`getc(stdin)`​，`putc()`​同理

#### fscanf()

​`int fscanf(FILE *文件指针, " ", ...)`​

可以将`scanf(...)`​视为`fscanf(stdin,...)`​，`fprintf()`​同理

#### fgets()

​`char *fgets(char *字符串地址, int 一行内最多读取的字符数, FILE *文件指针)`​

从文件中读取一行（或读到第二个参数所指定的字符数，且会读入`'\n'`​），将内容存储在给定的字符串地址上

### 输入至文件中

#### putc()

​`int putc(int 字符, FILE *文件指针)`​

写入一个字符到文件中

#### fprintf()

​`int fprintf(FILE *文件指针, " ", ...)`​

#### fputs()

​`int fputs(const char *字符串地址, FILE *文件指针)`​

向文件中输入字符串，不会额外添加`\n`​（与fputs()对应）

## 二进制文件I/O

### fwrite()

​`size_t fwrite(const void *待写入数据块地址, size_t 待写入数据块大小（单位为B）, size_t 待写入数据块数量, FILE *待写入文件)`​

把待写入数据块地址的二进制数据写入文件，返回成功写入项的数目

### fread()

​`size_t fread(void *待写入数据块地址, size_t 待写入数据块大小（单位为B）, size_t 待写入数据块数量, FILE *待写入文件)`​

与fwrite()数据流方向相反，从二进制文件中读取二进制数据

```c
//使用例，假设fp为文件指针
char buffer[256];
fwrite(buffer, 256, 1, fp);
double earning[10];
fread(earning, sizeof(double), 10, fp);
```

## 文件内容的访问

### rewind()

#### 函数原型

​`void rewind(FILE *_File)`​

#### 作用

返回文件开始处(比如用了fscanf())

### fseek()

#### 函数原型

​`int fseek(FILE *_File, long _Offset, int _Origin)`​

#### 作用

可将文件看作数组，可以在fopen()打开的文件中移动到任意位置

fseek(待查找文件 , 偏移量 , 起始点)

从起始点移动**偏移量**的位置

注意偏移量需要long类型的数据，如果输入常数需要在数值后面加L（因为小写的l与1较难区别）

移动正常会返回`0`​，错误会`-1`​

##### 起始点模式

|SEEK\_SET|文件起始|
| :-------------| :---------|
|SEEK\_CUR|当前位置|
|SEEK\_END|文件末尾|

### ftell()

#### 函数原型

​`long ftell(FILE *_File)`​

#### 作用

返回参数指向文件的当前位置距离文件开始处的字节数

适用于以二进制模式打开的文件

### fgetpos()

#### 函数原型

​`int fgetpos(FILE *__restrict__ _File, fpos_t *__restrict__ _Pos)`​

#### 作用

因为fseek()只能获取long范围内的文件长度，对于超大文件不适用，所以引入fgetpos()以及`fpos_t`​

调用函数时，它把**fpost**类型的值放在pos指向的位置上，该值描述了文件中的当前位置距离文件开头的字节数

如果成功，函数返回`0`​；失败返回非0

### fsetpos()

#### 函数原型

​`int fsetpos(FILE *_File, const fpos_t *_Pos)`​

#### 作用

调用该函数时，使用pos指向位置上的**fpost**类型值来设置文件指针指向偏移该值后指定的位置

成功返回0；失败返回非0

在调用该函数前，应该先用fgetpos()获取pos

## 其他标准I/O

### ungetc()

#### 函数原型

​`int ungetc(int _Ch, FILE *_File)`​

#### 作用

把**ch**指定的字符放回输入流中（即下一次调用输入会获取该字符）

### fflush()

#### 函数原型

​`int fflush(FILE *_File)`​

#### 作用

引起输出缓冲区中所有未写入数据被发送到指定输出文件中（即**刷新缓冲区**）

有时printf()需要输出缓冲区满才会输出，导致程序运行过程中不显示

所以需要fflush()强制刷新缓冲区，使得缓冲区中的内容输出

### setvbuf()

#### 函数原型

​`int setvbuf(FILE *__restrict__ _File, char *__restrict__ _Buf, int _Mode, size_t _Size)`​

#### 作用

创建一个供标准I/O函数替换使用的缓冲区（相当于独立开辟一个新区来操作文件）

操作成功返回`0`​

**File**指向文件

**Buf**指向创建的区域，若为`NULL`​，则会自行分配

**Mode**选择创建模式

**Size**创建的缓冲区的大小，单位为B

##### Mode

|\_IOFBF|完全缓冲（在缓冲区满时刷新）|
| :-----------| :-----------------------------------|
|\_IOLBF|行缓冲（缓冲区满或输入换行时刷新）|
|\_IONBF|无缓冲|

### feof()

#### 函数原型

​`int feof(FILE *_File)`​

#### 作用

检测上一次输入是否到达文件结尾，是返回非零值；否，返回`0`​

### ferror()

#### 函数原型

​`int ferror(FILE *_File)`​

#### 作用

若读写出现错误，返回非零值；否，返回`0`​

# 代码实例

```c
//通过命令行参数为程序提供多个文件名，第一个参数将作为目标文件，程序会将其他文件的内容追加到目标文件中
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define BUFSIZE 4096

void append(FILE *source , FILE *dest);
char * s_gets(char st[] , int n);

int main(int argc, char * argv[])
{
    FILE *fa , *fs;  //创建两个文件指针，fa指向目标文件，fs指向只读文件
    int files = 0;  //用来统计追加了多少个文件
    int count = 2;  //用来访问*argv[]的下标
	int ch;  //最后用来读取文件内容所用

    if (argc > 2)  //通过命令行参数获取文件名
    {
        if ((fa = fopen(argv[1],"a+")) == NULL)  //使用更新模式打开文件并判断是否打开成功
        {
            fprintf(stderr,"Can't open %s\n",argv[1]);  //打开文件失败，返回错误信息并退出程序
            exit(EXIT_FAILURE);
        }
        if ((setvbuf(fa,NULL,_IOFBF,BUFSIZE)) != 0)  //为文件操作创建缓冲区
        {
            fputs("Can't create output buffer\n",stderr);  //创建缓冲区失败，返回错误信息并退出程序
            exit(EXIT_FAILURE);
        }
        while (argv[count])  //当还有文件没有处理时
        {
            if (strcmp(argv[1],argv[count]) == 0)  //判断两个文件名是否一致，防止为自身添加自身
                fputs("Can't append file to itself\n",stderr);
            else if ((fs = fopen(argv[count],"r")) == NULL)  //以只读方式打开另一个文件
                fprintf(stderr,"Can't open %s\n",argv[count]);
            else
            {
                if (setvbuf(fs,NULL, _IOFBF , BUFSIZE) != 0)  //为新打开的文件创建缓冲区
                {
                    fputs("Can't create input buffer\n",stderr);
                    continue;
                }
                append(fs,fa);  //调用添加函数
                if (ferror(fs) != 0)  //判断文件操作是否成功
                    fprintf(stderr,"Error in reading file &s.\n",argv[count]);
                if (ferror(fa) != 0)
                    fprintf(stderr,"Error in writing file %s.\n",argv[1]);
                fclose(fs);  //记得要关掉文件
                printf("File %s appended.\n" , argv[count]);
                count++; 
                files++;
                puts("Next file");
            }
        }
    }
	else
	{
		fputs("The number of arguments is not enough.\n",stderr);
		exit(EXIT_FAILURE);
	}
    printf("Done appending. %d files appended.\n",argc-2);
    rewind(fa);  //回到目标文件的开头
    printf("%s contents: \n",argv[1]);
    while ((ch = getc(fa)) != EOF)  //输出目标文件此时的内容
        putchar(ch);  
    puts("Done displaying.");
    fclose(fa);  //记得关闭文件

    return 0;
}

void append(FILE *source , FILE *dest)  //将source文件的内容添加到dest文件中
{
    size_t bytes;
    static char temp[BUFSIZE];
    while ((bytes = fread(temp,sizeof(char),BUFSIZE,source)) > 0)  //如果读取的内容不为空
        fwrite(temp,sizeof(char),bytes,dest);  //写入
}

char * s_gets(char st[] , int n)  //字符串输入
{
    char * ret_val , *find;
    ret_val = fgets(st,n,stdin);
    if (ret_val)
    {
        find = strchr(st,'\n');
        if (find)
            *find = '\0';
        else
            while (getchar() != '\n')
                continue;
    }
    return ret_val;
}
```

‍
