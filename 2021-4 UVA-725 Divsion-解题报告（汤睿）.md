#  2021-4 UVA-725 Divsion-解题报告（汤睿）

##  题目大意

输入一个数N （2<=N<=79）,判断是否存在 abcde / fghij =N（每个数字都不能重复），若存在则输出abcde / fghij =N，不存在则输出 There are no solutions for N .

##  解题思路

枚举分母，然后再判断它与N的乘积是否能用完剩下的数字并没有重复。

##  复杂度分析

由于只循环了分母，所以复杂度为O（N）

##  心得体会

这种题放在比赛里肯定是要抢时间的，所以要又快又准，多积累一些解题的方法并熟练运用才能在比赛中取胜。

##  代码

```c
#include<bits/stdc++.h>
using namespace std;
int main()
{
	int sum,num,n,j;
	int a,b,c,d,e;
	int f,g,h,l,m;
	int x[10],flag=0;
	while(~scanf("%d",&n)&&n)
	{
		if(flag==0)
		flag=1;
		else
		printf("\n");
		sum=0;
		for(int i=1234;i<=98765;i++)
		{
			memset(x,0,sizeof(x));//每循环一次用于记录的数组清零
			f=i%10,g=i/10%10,h=i/100%10,l=i/1000%10,m=i/10000%10;
			num=i*n;
			if(num>98765)
			break;
			a=num%10,b=num/10%10,c=num/100%10,d=num/1000%10,e=num/10000%10;
			x[a]++,x[b]++,x[c]++,x[d]++,x[e]++;
			x[f]++,x[g]++,x[h]++,x[l]++,x[m]++;//记录每个数字的个数，要求不能大于1（即不能重复）
			for(j=0;j<=9;j++)
			if(x[j]>1)
			break;
			if(j==10)
			{
				printf("%d%d%d%d%d / %d%d%d%d%d = %d\n",e,d,c,b,a,m,l,h,g,f,n);
				sum++;
			}
			else
			continue;
		}
		if(sum==0)
		printf("There are no solutions for %d.\n",n);
	}
	return 0;
 } 
```

