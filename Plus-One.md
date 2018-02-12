Plus One
=======

1.问题描述
----------

Given a non-negative integer represented as a non-empty array of digits, plus one to the integer.<br>
You may assume the integer do not contain any leading zero, except the number 0 itself.<br>
The digits are stored such that the most significant digit is at the head of the list.<br>
把一个数组看作一个整数，对其进行加一的操作，最终返回加一后的数组，和该数组的长度。<br>

2.思路
------

其实就和Add Binary那道题的思路一样，只不过要注意的是只有该数组的最后一位要加一，其他数字是否改变要看是否进位。<br>

3.代码

```c
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* plusOne(int* digits, int digitsSize, int* returnSize) {
    int *answer=(int *)malloc(sizeof(int)*(digitsSize+1));//比原数组的长度多一，因为可能要进位
    memset(answer,0,(digitsSize+1)*sizeof(int));//把数组中的数初始化
    int temp=0;//判断是否要进位的标志
    answer[digitsSize]=(digits[digitsSize-1]+1)%10;//只有最后一位要加一，所以要单独拿出来讨论
    temp=(digits[digitsSize-1]+1)/10;
        for (int i=digitsSize-2; i>=0; i--) {
        answer[i+1]=(digits[i]+temp)%10;
        temp=(digits[i]+temp)/10;
        }
    if (temp==1) {
        *returnSize=digitsSize+1;//新的数组的长度
        answer[0]=1;//因为数组answer的长度要比digits的长度短，进位也只会进一，所以自己把answer[0]赋值即可
        return answer;
    }
    else {
        *returnSize=digitsSize;
        return answer+1;//没有进位就把answer的起点改变即可
    }
}
```

4.总结
-----

（1)掌握进位的方法，不管是几进制的，类比即可。<br>
（2）一开始没有读懂题，以为是要把每位都加一，造成错误，还有不理解Return an array of size (*returnSize). 这句话的意思，因为错把(*returnSize)当成了数组。<br>
（3）关于指针<br>
1、指针指向变量：<br>
下面有这样一个代码块：<br>
```c
int  main（）
{int a=10;
int b=15;
test(a,b);
printf("a=%d,b=%d\n",a,b);
}
void test(int  x,int y)
{
int tmp;
tmp=x;
x=y;
y=tmp;
}
```

最后输出的结果还是a=10,b=15。因为在函数调用时，实参和形参之间只是值传递。但我们使用指针结果就不一样了，如：<br>
```c
int  main（）
{int a=10;
int b=15;
test(&a,&b);
printf("a=%d,b=%d\n",a,b);return 0;
}
void test(int * x,int *y)
{
int tmp;
tmp=*x;
*x=*y;
*y=tmp;
}
```

输出结果a=15,b=10。变量a和b的值发生了交换。这是因为我们利用指针访问变量的存储单元，间接修改变量的值。<br>
2、指针指向数组：<br>
定义一个数组并初始化，int array[5]={2，5，12，7，8},定义一个指针变量并把数组的地址赋给它，int *p=array，注意数组名就是数组的地址，而且数组的地址就是首元素的地址。因此我们的指针变量就指向了数组的首元素，*p=2。如果把(p+1),那么指针变量就指向了数组的下一个元素5,因此我们可以利用指针来遍历数组的各个元素：<br>
```c
int  main()
{int array[5]={2，5，12，7，8};
int *p =array;
for(int i=0;i<5;i++){
printf("array[%d]=%d\n",i,*(p+i));
}return 0;
}
```
3、指针指向字符串：
我们都知道用数组存储字符串，如char name[20]="jack"，上面已经简单讲述了指针指向数组，所以我们可以这样做，char *name="jack",指针变量指向字符串的首个字符并可以依次访问字符串的各个字符。<br>
 4、指针指向函数：
我们需要知道怎样表示一个指针指向函数，说白了就是语法要正确，下面我也取一个代码块来说明一下：<br>
```c
int sum(int x,int y){
return x+y;
}
int main(){
int a=5;
int b=6;
int (*p)(int,int);
p=sum;
int result=(*p)(a,b);
printf("The result is %d\n",result);
return 0;
}
```

不难发现上面代码块里语句（*p）(a,b)可以用p(a,b)来代替，因为p和sum就是一样的，只是用前者可能更容易理解一点。而我们要知道怎样定义一个指针指向函数，int (*p)(int,int)这是固定写法，前面的int是指针将来指向的函数的返回值的类型，如果没有函数返回值，那就是void，后面括号里的两个int 当然就是指针将指向的函数的形参。<br> 
5，指针指向结构体：<br>
我们首先首先定义一个结构类型，<br>
```c
struct student
{
     char *name;
      int  ages;
}
```
再根据类型定义结构体变量 struct student stu={"Rose",15};定义一个指针指向结构体类型，struct student *p;把结构体变量stu的地址赋给指针变量p,p=&stu;我们可以有3种方式来访问结构体中的属性ages：
stu.ages=15;(*p).ages=15;p->ages=15;不过第三种方式在C语言中只能用来指向结构体。
