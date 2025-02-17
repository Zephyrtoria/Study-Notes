# C语言程序设计OJ题

1001. Output a string

```cpp
#include <stdio.h>
int main(void)
{
    printf("Hello, class 2027 CSECNU!");
    return 0;
}
```

1002. 较大数

```cpp
#include <stdio.h>

int main(void)
{
    int a,b;
    scanf("%d %d",&a,&b);
    printf("Max=%d",a>b?a:b);
    return 0;
}
```

1003. square root

```cpp
#include <stdio.h>
#include <math.h>

int main(void)
{
   double d;
   scanf("%lf",&d);
   printf("%f",sqrt(d));
   return 0; 
}
```

1004. A+B Problem

```cpp
#include <stdio.h>

int main(void)
{
    int a,b;
    scanf("%d %d",&a,&b);
    printf("%d",a+b);
  
    return 0;
}
```

1005. ADD

```cpp
#include <stdio.h>

int main(void)
{
   int n;
   scanf("%d",&n);
   printf("%d",(1+n)*n/2);
   return 0;
}
```

1006. Compute the value of the Celsius temperature

```cpp
#include <stdio.h>

int main(void)
{
    double fah,cel;
    scanf("%lf",&fah);
    cel = (fah-32)*5/9.0;
    printf("fahrenheit=%lf, celsius=%lf",fah,cel);
    return 0;
}
```

1007. Compute the value of the Fahrenheit temperature

```cpp
#include <stdio.h>

int main(void)
{
    double fah,cel;
    scanf("%lf",&cel);
    fah = cel*9/5.0+32;
    printf("celsius=%lf, fahrenheit=%lf",cel,fah);
    return 0;
}
```

1008. Bytes of int and long long

```cpp
#include <stdio.h>

int main(void)
{
    printf("%zd\n",sizeof(int));
    printf("%zd\n",sizeof(unsigned));
    printf("%zd\n",sizeof(char));
    printf("%zd\n",sizeof(short));
    printf("%zd\n",sizeof(long));
    printf("%zd\n",sizeof(long long));
    printf("%zd\n",sizeof(100));
    printf("%zd\n",sizeof(-100));
    printf("%zd\n",sizeof(12345u));
    printf("%zd\n",sizeof(12345L));
    printf("%zd\n",sizeof(12345LL));
    printf("%zd\n",sizeof(1234567890));
    printf("%zd\n",sizeof(12345678900));
    printf("%zd\n",sizeof(0x12345670));
    printf("%zd\n",sizeof(0x1234567890));
    return 0;
}
```

1009. 取值范围

```cpp
#include <stdio.h>
#include <limits.h>

int main(void)
{
    printf("%d %d\n",CHAR_MIN,CHAR_MAX);
    printf("%d %d\n",INT_MIN,INT_MAX);
    printf("%u %u\n",0,UINT_MAX);
    printf("%hd %hd\n",SHRT_MIN,SHRT_MAX);
    printf("%lld %lld\n",LLONG_MIN,LLONG_MAX);
    printf("%llu %llu\n",0,ULLONG_MAX);
    return 0;
}
```

1010. 计算对数

```cpp
#include <stdio.h>
#include <math.h>

int main(void)
{
    int b;
    double x;
    scanf("%d %lf",&b,&x);
    printf("%.6lf",log(x)/log(b));
    return 0;
}
```

1011. 线性插值法

```cpp
#include <stdio.h>

int main(void)
{
    double x0,y0,x1,y1,x,y;
    scanf("%lf %lf %lf %lf %lf",&x0,&y0,&x1,&y1,&x);
    y = (y0 + (x - x0)*(y1-y0)/(x1-x0));
    printf("%.3lf",y);
  
    return 0;
}

```

1012. 贷款计算

```cpp
#include <stdio.h>
#include <math.h>

int main(void)
{
    int d,p,r;
    double m;
    scanf("%d %d %d",&d,&p,&r);
    m = log10(p/(p-d*r*0.01))/log10(1+r*0.01);
    printf("%.0lf",m);
    return 0;
}
```

1013. LeapYearConclusion

```cpp
#include <stdio.h>

int main(void)
{
    int year;
    scanf("%d",&year);
    printf("%d",(((year % 4 == 0) && (year % 100 != 0)) || (year % 400 == 0)) ? 1 : 0);
    return 0;
}
```

1014. 大小写转换

```cpp
#include <stdio.h>

int main(void)
{
    char a;
    scanf("%c",&a);
    printf("%c",a-32);
    return 0;
}
```

1015. 判断奇偶

```cpp
#include <stdio.h>
#include <string.h>

#define MAX 20

int main(void)
{
    char st[MAX];
    int a;
    scanf("%s",st);
    a = st[strlen(st)-1];
    a = a - '0';
    printf("%d",(a % 2 == 0) ? 0 : 1);
    return 0;
}
```

1016. 估算身高

```cpp
#include <stdio.h>

double cal(char sex,double length);

int main(void)
{
    char sex;
    double length;
    scanf("%c %lf",&sex,&length);
    printf("%.1lf",cal(sex,length));
    return 0;
}

double cal(char sex,double length)
{
    if (sex == 'M')
    {
        return (length * 1.88 + 32);
    }
    else if (sex == 'F')
    {
        return (length * 1.94 + 28.7);
    }
}
```

1017. 位求反

```cpp
#include <stdio.h>
int main(void)
{
    int x,p,n;
    int bitval = 1;
    int i;
    scanf("%d %d %d",&x,&p,&n);
    for (i = 0 ; i < 32 ; i++)
    {
        if (i <= p && i >= (p-n+1))
        {
            x ^= bitval;
        }
        bitval <<= 1;
    }
    printf("%d",x);
    return 0;
}
```

1018. 位运算

```cpp
#include <stdio.h>

int bit_change(int i , int j , int x);

int main(void)
{
    int i,j,x;
    scanf("%d %d %d",&x,&i,&j);
    printf("%d",bit_change(i,j,x));
    return 0;
}

int bit_change(int i , int j , int x)
{
    int bit_i,bit_j;
    bit_i = (x >> i) & 1;
    bit_j = (x >> j) & 1;

    if (bit_i != bit_j)
    {
        x ^= (1 << i);
        x ^= (1 << j);
    }


    return x;
}
```

1019. 逻辑运算与位运算

```cpp
#include <stdio.h>

int cal(int a,int b);

int main(void)
{
	int a,b;
	scanf("%d %d",&a,&b);

	printf("%d\n",(a && b));
	printf("%d\n",(a & b));
	if ( 0 <= b && b <= 31)
	{
		printf("%d\n",(a>>b));
		if (a < 0)
		{
			printf("%d",cal(a,b));
		}
		else
		{
			printf("%d",(a>>b));
		}
	
	}
	return 0;
}

int cal(int a,int b)
{
	unsigned int temp = a;
	temp >>= b;
	return temp;
}
```

1020. 重力加速度

```cpp
#include <stdio.h>
#include <math.h>

#define G 9.8
#define HEIGHT 1.75
#define ONE_TWO 5
#define UP_THREE 3

double cal(int n);

int main(void)
{
    int n;
    scanf("%d",&n);
    printf("%.3lf",cal(n));
    return 0;
}

double cal(int n)
{
    double s;
    n -= 1;
    if (n < 3)
    {
        s = ONE_TWO * n;
    }
    else
    {
        s = ONE_TWO * 2 + UP_THREE * (n - 2);
    }
    s += 1.75;
    return (sqrt(2*s/G));
}
```

1021. 二次方程的根

```cpp
#include <stdio.h>
#include <math.h>

int main(void)
{
    double a,b,c,x1,x2,x;

    scanf("%lf %lf %lf",&a,&b,&c);
    x = sqrt(b*b-4*a*c);
    if (x > 0)
    {   
        x1 = (-b-x)/(2*a);
        x2 = (-b+x)/(2*a);
        if (x1 == x2)
            printf("%.6lf",x1);
        else
            printf("%.6lf %.6lf",x1,x2);
    }
    else if (x == 0)
    {
        x1 = (-b-x)/(2*a);
        printf("%.6lf",x1);
    }
      
    else
        printf("No Answer");

}
```

1022. 二进制表示

```cpp
#include <stdio.h>

void bit_cal(int c,int output[],int count);

int main(void)
{
	int c;
	int count = 7;
	int output[8] = {0,0,0,0,0,0,0,0};
	scanf("%c",&c);
	bit_cal(c,output,count);
	for (count = 0 ; count < 8 ; count++)
	{
		printf("%d",output[count]); 
	} 
	return 0;
}

void bit_cal(int c,int output[],int count)
{
	if (c / 2 == 0)
		output[count] = c;
	else
	{
		output[count] = c % 2;
		count--;
		bit_cal(c/2, output, count);
	}
}
```

1023. Compute e

```cpp
#include <stdio.h>

double cal(int n , double * tal);

int main(void)
{
    int n = 1;
    double add;
    double temp = 1.0;
    double e = 1;
    while ((add = cal(n,&temp)) && (add > 0.000001))
    {
        e += add;
        n++;
    }
    printf("%.6lf",e);
    return 0;
}

double cal(int n , double * tal)
{
    *tal = (*tal) * n;
    return (1.0/(*tal));
}
```

1024. 整数乘积

```cpp
#include <stdio.h>
int main(void) 
{
	long a,b;
	scanf("%ld %ld",&a,&b);
	printf("%ld",a*b);
	return 0;
}
```

1025. 判断三角形

```cpp
#include <stdio.h>
int main(void)
{
	int a,b,c;
	scanf("%d %d %d",&a,&b,&c);
	int flag = 0;

	if (a + b > c && a + c > b && b + c > a && a - b < c && a - c < b && b - c < a)
		flag = 1;
	printf("%d",flag);
	return 0;
}
```

1026. 乘2输出

```cpp
#include <stdio.h>

void myint(void);
void myfloat(void);
void mychar(void);

int main(void)
{
	int n;
	n = getchar();
	if (n == '1' || n == '2')
		myint();
	else if (n == '3' || n == '4')
		myfloat();
	else
		mychar();
	return 0;
}

void myint(void)
{
	long long x;
	scanf("%lld",&x);
	printf("%lld",x*2);
}
void myfloat(void)
{
	double x;
	scanf("%lf",&x);
	printf("%.3lf",x*2);
}
void mychar(void) 
{
	char x;
	scanf("%c",&x);
	printf("%c",x);
}
```

1027. 月份天数

```cpp
#include <stdio.h>

const int days[] = {31,28,31,30,31,30,31,31,30,31,30,31};

int main(void)
{
	int y,m,ans;
	int flag = 0;
	scanf("%d %d",&y,&m);
	if ((y % 4 == 0 && y % 100 != 0) || (y % 400 == 0))
		flag = 1;
	if (m == 2 && flag == 1)
		ans = days[1] + 1;
	else
		ans = days[m-1];
	printf("%d",ans);
	return 0;
}
```

1028. BitCount

```cpp
#include <stdio.h>
int main(void)
{
	char ch;
	int sum = 0;
	ch = getchar();
	while (ch != 0)
	{
		sum += ch%2;
		ch /= 2;
	}
	printf("%d",sum);
	return 0;
}
```

1029. 字符转换

```cpp
#include <stdio.h>

int main(void)
{
    char ch;
    ch = getchar();
    if ('a' <= ch && ch <= 'z')
        ;
    else if ('A' <= ch && ch <= 'Z')
        ch = ch + 32;
    else if (ch == '\n' || ch == EOF)
        ch = '?';
    else
        ch = '*';
    printf("%c",ch);
    return 0;
}
```

1030. 整数循环右移

```cpp
#include <stdio.h>

int main(void)
{
    unsigned x,a;
    int n,i;
    scanf("%u %d",&x,&n);
    for (i = 0; i < n; i++)
    {
        a = x%2;
        x = (a << 31) + x/2;
    }
    printf("%u",x);
    return 0;
}
```

1031. Rotate digits

```cpp
#include <stdio.h>
#include <string.h>

int main(void)
{
    char n[20];
    int m,length,flag = 0;
    char temp;
    int i;
    scanf("%s %d",n,&m);
    length = strlen(n);
    m = length - m % length;
    printf("%d ",length);
    for (i = 0; i < length; i++)
    {
        temp = n[(m+i)%length];
        if (temp != '0')
            flag = 1;
        if (length == 1 && temp == '0')
            flag = 1;
        if (flag)
            printf("%c",temp);
    }
    return 0;
}
```

1032. square root

```cpp
#include <stdio.h>
#include <math.h>

int main(void)
{
    double lx,rx,mx,mx2;
    double x;
    int flag = 1;
    scanf("%lf",&x);
    mx = x;
    if (x > 1.0)
    {
        lx = 0;
        rx = x;
        while (flag)
        {   
            mx = (lx+rx)/2;
            mx2 = mx*mx;
            if (fabs(x - mx2) < 1E-6)
                flag = 0;
            else if (mx2 > x)
                rx = mx;
            else
                lx = mx;
        }
    }
    else if (x > 0)
    {
        lx = x;
        rx = 1.0;
        while (flag)
        {   
            mx = (lx+rx)/2;
            mx2 = mx*mx;
            if (fabs(x - mx2) < 1E-6)
                flag = 0;
            else if (mx2 > x)
                rx = mx;
            else
                lx = mx;
        }
    }
  
    printf("%.8lf",mx);
    return 0;
}
```

1033. 素数判断

```cpp
#include <stdio.h>
#include <math.h>

int is_prime(int n);

int main(void)
{
    int n;
    scanf("%d",&n);
  
    if (n == 1 || !is_prime(n))
        printf("No");
    else
        printf("Yes");
    return 0;
}

int is_prime(int n)
{
    int x = (int)(sqrt(n)+1);
    int i;
    int flag = 1;
    for (i = 2; i < x; i++)
    {
        if (n % i == 0)
            flag = 0;
    }
    return flag;
}
```

1034. 统计1的个数

```cpp
#include <stdio.h>
int main(void)
{
    unsigned int n;
    int sum = 0;
    scanf("%u",&n);
    while (n)
    {
        sum += n % 2;
        n /= 2;
    }
    printf("%d",sum);
    return 0;
}
```

1035. 数字猜想

```cpp
#include <stdio.h>

int main(void)
{
    unsigned int x;
    scanf("%u",&x);
    while (x != 1)
    {
        printf("%d ",x);
        if (x % 2 == 0)
            x = x / 2;
        else
            x = x * 3 + 1;
    }
    printf("1");
    return 0;
}
```

1036. 进制转换

```cpp
#include <stdio.h>
#define N 8

//********** Specification of hex2int **********
unsigned h2i(char s[])
/*
PreCondition:
s is a string consisting of 0~9,A-F or a-f with at most 8 characters
PostCondition:
return a decimal number equivalent to s
Examples: "100"==>256 ; "a"==> 10 ; "0"==> 0
*/
{
    const int he[] = {10,11,12,13,14,15};
    int i,sign = 1,ret_val = 0;

    for (i = 0; s[i]; i++)
    {
        if (s[i] == '-')
            sign = 1;
        else if ('A' <= s[i] && s[i] <= 'F')
            ret_val = ret_val * 16 + he[s[i] - 'A'];
        else if ('a' <= s[i] && s[i] <= 'f')
            ret_val = ret_val * 16 + he[s[i] - 'a'];
        else
            ret_val = ret_val * 16 + (s[i] - '0');
    }
    return sign * ret_val;
}
/***************************************************************/
int main()
{
    char s[N+1];
    scanf("%s",s);
    //********** hex2int is called here ****************
    printf("%u\n",h2i(s));
    //**************************************************
    return 0;
}
```

1037. 二分查找

```cpp
#include <stdio.h>

int binarySearch(int a[], int n, int x) {
    // TODO: your function definition
    int l = 0,m,r = n-1;
    while (l <= r)
    {   
        m = (l + r) / 2;
        if (a[m] == x)
            return m;
        if (a[m] > x)
            l = m + 1;
        else
            r = m - 1;
    }
    return -1;
}

/***************************************************************/
#define N 100000
int a[N];
int main() {
    int n;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    //********** binarySearch is called here *************
    int q, x;
    scanf("%d", &q);
    for (int i = 0; i < q; i++) {
        scanf("%d", &x);
        printf("%d\n", binarySearch(a, n, x));
    }
    //**************************************************
    return 0;
}
```

1038. 二分查找

```cpp
#include <stdio.h>
#include <stdlib.h>

int Binary_search_L(int A[], int n, int T);
int Binary_search_R(int A[], int n, int T);

int main(void)
{
    int n,T,i,out,l,r;
    int *A;
    scanf("%d",&n);
    A = (int(*))malloc(sizeof(int) * n);
    for (i = 0; i < n; i++)
        scanf("%d",&A[i]);
    scanf("%d",&T);
    l = Binary_search_L(A,n,T);
    r = Binary_search_R(A,n,T);
    if (l != -1 && r != -1)
    {
        out = (l << 16) + r;
    }
    else
        out = -1;
    printf("%X",out);
    return 0;
}

int Binary_search_L(int A[], int n, int T)
{
    int l = 0,m,r = n-1;
    while (l <= r)
    {
        m = (l + r) / 2;
        if (A[m] < T)
            l = m + 1;
        else
            r = m - 1;
    }
    if (A[r+1] == T)
        return r+1;
    else
        return -1;
}

int Binary_search_R(int A[], int n, int T)
{
    int l = 0;
    int m,r = n-1;
    while (l <= r)
    {
        m = (l + r) / 2;
        if (A[m] <= T)
            l = m + 1;
        else
            r = m - 1;
    }
    if (A[l-1] == T)
        return l-1;
    else
        return -1;
}
```

1039. 平均数

```cpp
#include <stdio.h>
#include <stdlib.h>

#define N 11
int A[N] = {0}, B[N] = {0};
int a, b;

int * myadd(int A[], int B[]);
int mydiv(int *c, int d);

int main(void)
{
    int *pc;
    int tempa,tempb;
    scanf("%d %d", &a, &b);
    tempa = a, tempb = b;

    if (a < 0)  //negetive
    {
            A[0] = 1;
            a = -a;
    }
    else A[0] = 0;  //positive

    if (b < 0)  //negetive
    {
            B[0] = 1;
            b = -b;
    }
    else B[0] = 0;  //positive

    for (int i = 1; a != 0; i++)
    {
        A[i] = a % 10;
        a /= 10;
    }

    for (int i = 1; b != 0; i++)
    {
        B[i] = b % 10;
        b /= 10;
    }

    if (A[0] == B[0])
    {
        pc = myadd(A, B);
        printf("%d",mydiv(pc, 2));
    }
    else
        printf("%d",(tempa + tempb) / 2);
    return 0;
}

int * myadd(int A[], int B[])
{
    int * C;
    C = (int*)malloc(sizeof(int) * N);
    C[0] = A[0];
    int t = 0;
    for (int i = 1; i < N; i++)
    {
        t += A[i] + B[i];
        C[i] = t % 10;
        t /= 10;
    }
    return C;
}

int mydiv(int *c, int d)
{
    int ret_val = 0;
    int t = 0;
    int C[N];
    for (int i = N - 1; i > 0; i--)
    {
        t = t * 10 + c[i];
        C[i] = t / d;
        t %= d;
    }
    for (int i = N - 1; i > 0; i--)
        ret_val = ret_val * 10 + C[i];
    if (c[0] == 1)
        ret_val = -ret_val;
    return ret_val;
}
```

1040. Maximum product

```cpp
#include <stdio.h>

int main(void)
{
    int n,times;
    unsigned long long int ret_val = 1;
    scanf("%d",&n);
    times = n / 3;
    if (n <= 3)
        ret_val = n;
    else if (n % 3 == 0)
    {
        for (int i = 0; i < times; i++)
        {
            ret_val *= 3;
        }
    }
    else if (n % 3 == 1)
    {
        for (int i = 0; i < times-1; i++)
        {
            ret_val *= 3;
        }
        ret_val *= 4;
      
    }
    else
    {
        for (int i = 0; i < times; i++)
            ret_val *= 3;
        ret_val *= 2;
    }
    printf("%llu",ret_val);
    return 0;
}
```

1041. 最大公约数

```cpp
/***************************************************************/
/*                                                             */
/*  DON'T MODIFY main function ANYWAY!                         */
/*                                                             */
/***************************************************************/
#include <stdio.h>

//********** Specification of GCD **********
int GCD(int m,int n)
/* PreCondition:
m,n are two positive integers
PostCondition:
return Greatest Common Divisor of m and n
*/
{
    if (n == 0) return m;
    else return GCD(n,m%n);
}
/***************************************************************/
int main()
{
    int m,n;
    scanf("%d%d",&m,&n);
    //********** GCD is called here ********************
    printf("GCD(%d,%d)=%d\n",m,n,GCD(m,n));
    //**************************************************
    return 0;
}
```

1042. Compute

```cpp
/***************************************************************/
/*                                                             */
/*  DON'T MODIFY main function ANYWAY!                         */
/*                                                             */
/***************************************************************/
#include <stdio.h>
double sum(int n)
{
    if (n == 1) return 1;
    else
    {
        if (n % 2 != 0) return 1.0/n + sum(n-1);
        else return (-1.0)/n + sum(n-1);
    }
 // TODO: your function definition

}
int main()
{
    int n;
    scanf("%d",&n);
    printf("%lf\n",sum(n));
    return 0;
}
```

1043. 字符串处理

```cpp
void del(char s[]);
//Precondition：s存放一个字符串;
//Postcondition：删除s中所有空格，其余字符按原来顺序存放在s中。

#include <stdio.h>
#include <string.h>
void del(char s[])
{
    char temp[110000];
    int k = 0;
    for (int i = 0; s[i] != '\0'; i++)
        if (s[i] != ' ')
            temp[k++] = s[i];
    for (int i = 0; i < k; i++)
        s[i] = temp[i];
    s[k] = '\0';
}
int main()
{
    char s[110000];
    gets(s);  //输入一行字符
    del(s);
    printf("%s\n",s);
    return 0;
}
```

1044. itob

```cpp
/***************************************************************/
/*                                                             */
/*  DON'T MODIFY main function ANYWAY!                         */
/*                                                             */
/***************************************************************/


#include <stdio.h>

void itob(int n,char s[100],int b)
{
    // TODO: your function definition
    int flag = 0;
    int temp,i;
    char tmp[100];
    if (n < 0)
    {
        s[0] = '-';
        n = -n;
        flag = 1;
    }

    for (i = flag; n != 0; i++)
    {
        temp = n % b;
        if (temp < 10)
            tmp[i] = temp + '0';
        else
            tmp[i] = (temp - 10) + 'A';
        n /= b;
    }
  
    for (int k = flag,j = i - 1; k < i; k++,j--)
        s[j] = tmp[k];

    s[i] = '\0';
}

int main()
{
    int n,b;
    char s[100];
    scanf("%d%d",&n,&b);
    itob(n,s,b);
    printf("%s\n",s);
    return 0;
}
```

1045. 整数的二进制倒置

```cpp
#include <stdio.h>

int main(void)
{
	int k, a, i = 31;
	int ret_val = 0;
	int binary[32] = {0};
	int output[32] = {0};
	scanf("%d",&a);
	while (a > 0)
	{
		binary[i--] = a % 2;
		a /= 2;
	}
	//for (int j = 0; j <= 31; j++) printf("%d ",binary[j]);
//	puts("");
	k = i + 1;
	for (int j = 31; j > i ; j--)
		output[j] = binary[k++];
	for (int j = i + 1; j <= 31; j++)
	{
		ret_val = ret_val * 2 + output[j];
	}
	
	
	printf("%d",ret_val);
	return 0;

}
```

1046. LCM

```cpp
#include <stdio.h>
#define N 9

long long LCM(int a[], int n)
{
 // precondition: 1≤n≤9， 1≤a[i]≤100
 // postcondition: return LCM of all integers 
    long long ta[N] = {a[0]};
    for (int i = 0; i < n - 1; i ++)
    {
        long long a1 = ta[i], a2 = a[i + 1];
        while (a2 > 0)
        {
            long long tmp = a1;
            a1 = a2;
            a2 = tmp % a2;
        }
        ta[i + 1] = (ta[i] * a[i + 1]) / a1;
    }
  
    return ta[n - 1];
}

int main()
{ 
   int i,n,a[N];
   for (scanf("%d",&n),i=0;i<n;i++) scanf("%d",&a[i]);
   printf("%lld\n", LCM(a,n));
   return 0;
}
```

1047. 查找字符串

```cpp
#include <stdio.h>
#include <string.h>
#define N 80
int strReverseIndex(char s[],char t[])
/* precondition: NULL
postcondition: return index of t in s from right to left, -1 if none
*/
{
    //TODO: your function definition
    int ret_val = -1;
    for (int i = 0; i < N; i++)
    {
        int j = i;
        while (s[j] && t[j - i] && s[j] == t[j - i]) j++;
        if (j - i == strlen(t))
        {
            ret_val = i;
        }
    }
    return ret_val;
}
/***************************************************************/

int main()
{
    char s[N+1],t[N+1];
    scanf("%s%s",s,t);
    //********** strReverseIndex is called here ********************
    printf("%d\n",strReverseIndex(s,t));
    //**************************************************
    return 0;
}
```

1048. strend

```cpp
#include <stdio.h>
#include <string.h>
#define N 20
int strend(const char *s, const char *t);

int main(void)
{
    char s[N + 1], t[N + 1];
    scanf("%s %s",s,t);
    printf("%d",strend(s,t));
    return 0;
}

int strend(const char *s, const char *t)
{   
    for (int i = strlen(s) - 1, j = strlen(t) - 1; j >= 0; i--, j--)
    {
        if (s[i] != t[j]) return 0;
    }
    return 1;
}
```

1049. atof

```cpp
#include <stdio.h>
#define MAXLINE 80
/***************************************************************/
/*                                                             */
/*  DON'T MODIFY main function ANYWAY!                         */
/*                                                             */
/***************************************************************/

double atof(char s[]) {
    // TODO: your function definition
    double ret_val = 0;
    double times = 0;
    int flag = 1,tmp = 0;
    double sign_z = 1,sign_f = 1;
  
    for (int i = 0; s[i]; i++)
    {
        if ('0' <= s[i] && s[i] <= '9')
        {
            ret_val = ret_val * 10.0 + (double)(s[i] - '0');
            if (!flag) times -= 1;
        }
        else if (s[i] == 'e' || s[i] == 'E')
        {
            for (int j = i + 1; s[j]; j++)
            {
                if (s[j] == '-') sign_f = -1;
                if ('0' <= s[j] && s[j] <= '9') tmp = tmp * 10 + s[j] - '0';
            }
            tmp *= sign_f;
            times += tmp;
            break;
        }
        else if (s[i] == '.')
            flag = 0;
        else if (s[i] == '-')
            sign_z = -1;
    }

    if (times < 0)
    {
        while (times++ != 0) ret_val *= 0.1;
    }
    else
    {
        while (times-- != 0) ret_val *= 10;
    }

    return ret_val * sign_z;
}

  /* maximum input line length */

int main() {
    char s[MAXLINE];
    scanf("%s", s);
    printf("%f\n", atof(s));
    return 0;
}
```
