#include <stdio.h>
#include <stdlib.h>
#define MAX 1000001
#define cycle(a,b) for(int a=0;a<b;a++)
#define cycle1(a,b) for(int a=1;a<b;a++)
int main()
{
    long long *qaq,N,max,*aa;

    qaq=(long long *)malloc(MAX*sizeof(long long));
    aa=(long long *)malloc(MAX*sizeof(long long));//动态建立数组

    while(scanf("%lld",&N)!=EOF)
    {
        //for(i=0;i<N;i++)
        cycle(i,N)//输入数组
            scanf("%lld",&aa[i]);

        qaq[0]=aa[0];
        max=aa[0];
        //for(i=1;i<N;i++)
        cycle1(i,N)//动态规划查找最大子序列
        {//当dp[j-1]+a[i]>a[i]时，证明dp[j-1]>0,段长要继续加a[i]，使序列和最大。

 //当dp[j-1]<0时，肯定不能加上含有a[i]的序列，此时a[i]作为新序列的首元素，dp[j]=a[i].
            qaq[i]=(qaq[i-1]+aa[i])>aa[i]?(qaq[i-1]+aa[i]):aa[i];//动态方程：dp[j]=max{dp[j-1]+a[i],a[i]} 
            if(qaq[i]>max)
                max=qaq[i];
        }

        printf("%lld\n",max);
    }
    return 0;
}
