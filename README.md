#include<stdio.h>
#include"math.h"
#include"string.h"

	struct Date
	{
		int year;
		int month;
		int day;
	};

int main()
{
    struct Date p1,p2;
    scanf("%d%d%d",&p1.year,&p1.month,&p1.day);
    scanf("%d%d%d",&p2.year,&p2.month,&p2.day);
    int a[12]={31,28,31,30,31,30,31,31,30,31,30,31};
    int cha;
    if(p1.year!=p2.year)
    {
        int y;
        y=p2.year-p1.year;
        cha=(y)*365;
        int i;
        for(i=p1.year;i<p2.year;i++)
        {
            if((i%4 == 0&&i%100!=0)||i%400==0)    //计算相差多少年，并判断是不是闰年。
            {
                cha=cha+1;//如果是闰年天数加一
            }
        }

        int sum1,sum2;
        sum1=p1.day;sum2=p2.day;
        for(i=0;i<p1.month-1;i++)
            sum1+=a[i];
        if(((p1.year%4==0 && p1.year%100!=0)||p1.year%400==0) && p1.month>2)
            sum1=sum1+1;
        for(i=0;i<p2.month-1;i++)
            sum2+=a[i];
        if(((p2.year%4==0 && p2.year%100!=0)||p2.year%400==0) && p2.month>2)
            sum2=sum2+1;
        cha=cha-sum1+sum2;//计算相差多少天
    }

    else
    {
        int sum1,sum2,i;
        sum1=p1.day;sum2=p2.day;
        for(i=0;i<p1.month-1;i++)
            sum1+=a[i];
        if(((p1.year%4==0 && p1.year%100!=0)||p1.year%400==0) && p1.month>2)//闰年
            sum1=sum1+1;
        for(i=0;i<p2.month-1;i++)
            sum2+=a[i];
        if(((p2.year%4==0 && p2.year%100!=0)||p2.year%400==0) && p2.month>2)//闰年
            sum2=sum2+1;
        cha=sum2-sum1; //计算相差多少天
    }
    printf("%d",cha);
    return 0;

}
