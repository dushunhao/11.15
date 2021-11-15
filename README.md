#define _CRT_SECURE_NO_WARNINGS

#include<stdio.h>

#include<string.h>

int main()

{

	int a = 0;//初始化
	//int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };//完全初始化
	//int arr[10] = { 1,2,3,4,5 };//不完全初始化

	char ch1[5] = { 'b','i','t' };
	char ch2[]= { 'b','i','t' };
	char ch3[5] = "bit";
	char ch4[] = "bit";
	char ch5[] = "bit";//4个元素
	char ch6[] = { 'b','i','t'};//3个元素

	printf("%d\n", strlen(ch5));//3
	printf("%d\n", strlen(ch6));//随机值

	//printf("%s\n", ch5);
	//printf("%s\n", ch6);
	return 0;
  
}


int main()

{

	int arr[10] = { 0 };
	arr[4] = 5;//[]下标引用操作符
	int i = 0;
	int sz = sizeof(arr) / sizeof(arr[0]);
	for (i = 0; i < sz; i++)
	{
		printf("%d ", arr[i]);
	}
  
	return 0;
  
}

int main()

{

	int arr[10] = { 0 };
	int i = 0;
	for (i = 0; i < 10; i++)
	{
		printf("&arr[%d] = %p\n",i, &arr[i]);//%p按地址格式打印 - 十六进制的打印
	}
	//1.一维数组在内存中是连续存放的
	//2.随着数组下标的增长，地址是由低到高变化的
	return 0;
  
}


int main()

{

	int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };

	int*p = arr;//数组名是数组首元素的地址
	int i = 0;
	for (i = 0; i < 10; i++)
	{
		printf("%d ", *p);
		p++;
	}

	return 0;
  
}


int main()

{

	//二维数组创建
	//int arr[3][4];
	//char ch[3][10];
	//初始化 - 创建的同时给赋值
	//int arr[3][4] = { 1,2,3,4,5,6,7,8,9,10,11,12 };//前行后列
	int arr[3][4] = { {1,2},{3,4},{5,6} };
	int i = 0;
	int j = 0;
	for (i = 0; i < 3; i++)
	{
		for (j = 0; j < 4; j++)
		{
			printf("%d ", arr[i][j]);
		}
		printf("\n");
	}
  
	return 0;
  
}

int main()

{

	//二维数组在数组中存储
	int arr[][4] = { {1,2},{3,4},{5,6} };
    int i = 0;
	int j = 0;
	for (i = 0; i < 3; i++)
	{
		for (j = 0; j < 4; j++)
		{
			printf("&arr[%d][%d] = %p\n", i, j, &arr[i][j]);
		}
	}
	//二维数组在内存也是连续存放的，一行内部连续，换行也是连续的
  
	return 0;
  
}

int main()

{

	int arr[][4] = { {1,2},{3,4},{5,6} };
	int i = 0;
	int j = 0;
	int* p = &arr[0][0];
	for (i = 0; i < 12; i++)
	{
		printf("%d ", *p);
		p++;
	}
  
	return 0;
  
}

//冒泡排序的思想：

//两两相邻的元素进行比较，并且可能的话需要交换

void bubble_sort(int arr[],int sz)//形参arr本质上是指针

{

	//确定趟数
	int i = 0;
	for (i = 0; i < sz - 1; i++)
	{
		//一趟冒泡排序的过程
		int j = 0;
		for (j = 0; j < sz - 1 - i; j++)
		{
			if (arr[j] > arr[j + 1])
			{
				//交换
				int tmp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = tmp;
			}
		}
    
	}

}


int main()

{

	int arr[] = { 9,8,7,6,5,4,3,2,1,0 };
	//排序为升序 - 冒泡排序
    //计算元素个数
	int sz = sizeof(arr) / sizeof(arr[0]);
	bubble_sort(arr,sz);//数组传参的时候，传递的是数组首元素的地址

	return 0;
  
}



//数组名是数组首元素的地址

//但是有两个例外

//1.sizeof(数组名)--数组名表示整个数组-计算的是整个数组的大小单位是字节

//2.&数组名-数组名表示整个数组 - 取出的是整个数组的地址


int main()

{

	int arr[10] = { 0 };
	printf("%p\n", &arr);//1.-&arr取出的是数组的地址
	printf("%p\n", &arr + 1);//相当于+40

	printf("%p\n", arr);//2.
	printf("%p\n", arr + 1);//相当于+4
	//printf("%p\n", &arr[0]);//3.

	int sz = sizeof(arr);//数组名表示整个数组
	printf("%d\n", sz);

	//printf("%p\n", &arr[0]);
	//printf("%p\n", arr);//数组名是数组首元素的地址
  
	return 0;
  
}

int main()

{

    int n, i, j, count;
    scanf("%d", &n);
    for (i = 2; i <= n; i++)
    {
        for (j = 2; j <= i; j++)
        {
            if (i % j == 0)
                break;
        }
        if (i == j)
        {
            printf("%d ", i);
            count++;
        }
    }
    printf("\n%d ", n - count - 1);
    
    return 0;
    
}


int sum(int begin, int end)

{

	int i = 0;
	int b = 0;
	for (i = begin; i <= end; i++) 
	{
		b = b + i;
	}
	return b;
}
int main()
{
	int a = sum(1, 2);
	printf("%d", a);
	return 0;
}
