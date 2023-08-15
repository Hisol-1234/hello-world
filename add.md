转换ASCII码值
```c
int main
{
    int arr[] = {73,32,78};
    int i = 0;
    int sa = sizeof(arr)/sizeof(arr[0]);
    //sizeof(arr) - 计算的是数组的总大小，单位是字节
    //sizeof(arr[0]) - 计算的是数组元素的大小
    while(i<sz)
    {
        printf("%c,arr[i]);
        i++;
    }
return 0;
}
```
出生日期输入输出
```c
int main
{
    int year = 0;
    int month = 0;
    int date = 0;
    scanf("%4d%2d%2d",&year,&month,&date);//打印四位
    printf("year = %d\n",year);
    printf("month = %02d\n",month);//打印两位不够补零
    printf("date = %02d\n",date);
}
//通过scanf函数的%m格式控制可以指定输入域宽，输入数据域宽（列数），按此宽度截取所需数据；通过printf函数的%0格式控制符，输出数值时指定左面不使用的空位置自动填0。
```
18
