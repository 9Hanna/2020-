##欧几里得算法求最大公约数 和最小公倍数

#欧几里得求最大公约数算法用了递归思想。
 本程序输入输出示例：
 输入：
 10 14
 9 18
 输出：
 70
 18
 
##程序如下：

#include<stdio.h> 
int max(int a,int b) //最大公约数，采用递归的思想
{
	if(a%b==0)
		return b;
	return max(b,a%b);

} 

int main()
{  //求最小公倍数
	int a,b;
	while(scanf("%d%d",&a,&b)!=EOF)
	{
		int t;
		if(a<b) // 令a>b
		{
			t=a;
			a=b;
			b=t;
		} 	
		printf("%d\n",a*b/max(a,b));		
	}

	return 0;
}
