冒泡排序
===========
是一种交换排序
其思路是每次把最值移到一端,如同最值不断冒泡到一端,最终使数据有序
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
    for(int i=0;i<len;i++)
    {
        for(int j=0;j<len-i;j++)
        {
            if(dataset[j]<dataset[j+1])
            {
                int tmp=dataset[j];
                dataset[j]=dataset[j+1];
                dataset[j+1]=tmp;
            }
        }
    }
}
            