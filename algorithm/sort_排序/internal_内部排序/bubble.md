冒泡排序
===========
是一种交换排序
其思路是把相邻2个中，较大一者放到右边，则经过一个轮回，最大者必在最右，
与选择排序不同，他不止是把最大者放到最右，每次循环中，较大的数都会向右移动
算法时间复杂度O(n^2)
尽量使用低地址到高地址,利用空间局部性提高访存速度
伪代码:
    for i<-1~n
        for j<-1~n-i
            if data[j]<data[j+1]
                swap tow eles
c实现:
void BubbleSort(int *dataset,int len)
{
    for(int i=0;i<len-1;i++)
    {
        for(int j=1;j<len-i;j++)
        {
            if(dataset[j]<dataset[j-1])
            {
                int tmp=dataset[j];
                dataset[j]=dataset[j-1];
                dataset[j-1]=tmp;
            }
        }
    }
}
改进方案1：若一次循环中无交换，则已排好。(针对非随机较为有效)
void BubbleSort(int *dataset,int len)
{
	BOOL isSort=TRUE:
    for(int i=len-1;i>1;i--)
    {
    	isSort=TRUE:
        for(int j=1;j<i;j++)
        {
            if(dataset[j]<dataset[j-1])
            {
            	isSort=FALSE:
                int tmp=dataset[j];
                dataset[j]=dataset[j-1];
                dataset[j-1]=tmp;
            }
        }
        if(isSort)break;
    }
}
改进方案2：后n个数有序，且都大于前面的数.这时不需对后n个数排序。
在内循环中，右边的数总是最大的，循环中记录最右那次交换位置，下次循环到此处即可。
void BubbleSort(int *dataset,int len)
{
	int pos=len,k;
  	while(pos>0)
  	{
  		k=pos;
  		pos=0;
        for(int j=1;j<k;j++)
        {
            if(dataset[j]<dataset[j-1])
            {
                int tmp=dataset[j];
                dataset[j]=dataset[j-1];
                dataset[j-1]=tmp;
                pos=j;
            }
        }
        
    }
}