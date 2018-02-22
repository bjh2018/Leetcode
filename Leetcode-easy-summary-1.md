解题方法
======

1.二进制数的加法：就是倒着相加，然后再按转二进制的方法进行加减，如以下代码         ---Add Binary<br>

```c
 *(str+i) = ((*(a+lenA-1)-'0') + (*(b+lenB-1)-'0') + temp)%2 + '0';//-'0'是把字符型的转换成整型，+'0'是把整型转化为字符型
        temp = ((*(a+lenA-1)-'0') + (*(b+lenB-1)-'0') + temp)/2;
```
注：str是字符型数组，i是用来实现循环的,temp是中间变量<br>

2.判断不断被算出来的数（计算的方法相同，单独写一个函数）构成的一串数是否具有周期性的方法        ---Happy Number<br>
用两个数，一个数调用函数一次，另一个调用函数两次，不断的判断两者是否相等，当相等时就跳出循环<br>

```c
do{
    x=sum(x);
    y=sum(y);
    y=sum(y);
    }while(x!=y);//让y执行两次sum函数，使得do……while函数每执行一次就会让y比x多执行一次，如果存在周期的话，肯定会存在x=y的情况。
    if (x==1) return 1;
    else return 0;
```
    
 3.给定一组数，不确定相加的个数，但是相邻的不能相加，求相加的最大值    ---House Robber<br>
 设定两个数，一个是只加指数是偶数的，一个是只加奇数的，每加一个数，就用函数找出两数中较大的数。<br>
 
 ```c
  for (int i=0; i<numsSize; i++) {
        if (i%2==0) {
            a=max(a+nums[i],b);
        }
        else {
            b=max(b+nums[i],a);
        }
    }
    return max(a,b);//最后再取一次两数中大的数，因为不知道房子的数目是奇数还是偶数
}
```

4.关于要删除字符数组（数组）的前几位的方法，只需要把起点改变即可。<br>
5.如果找公共部分的话（字符数组），就先假设第一个是公共部分，与下面的去比较，并对第一个元素进行改动，如果出现不一样的，就把不一样的那一位改成'\0'即可---
Longest Common Prefix<br>

```c
 for (int i=1; i<strsSize; i++) {
       for (int j=0; strs[0][j]!='\0'; j++) {//因为找的是公共部分，所以后面的长度一定要小于等于第一个的长度
           if (strs[i][j]!=strs[0][j]) {
               strs[0][j]='\0';
               break;
           }
       }
   }
```

6.不占用其他空间实现数组中重复元素的删除，或者说删除特定的元素的方法---Move Zeroes---Remove Duplicates from Sorted Array<br>
把有用的元素从指标为0开始赋值，直到把数组的元素遍历完为止。<br>

```c
for (int i=0; i<numsSize; i++) {
        if (nums[i]!=0) nums[start++]=nums[i];//如果不是0，就对nums重新赋值即可
    }
```

7.把整数反转的方法，及把123换成321.---Reverse Integer<br>

```c
while(x>0) {
        result=result*10+x%10;
        x=x/10;
    }
```
8.使字符串倒序的方法：（1）建立新的字符数组，再赋值（2）直接把原字符数组的前后元素调换。---Reverse String<br>
9.（1）一个数的平方容易造成int溢出，一般是转成除法来判断。（2）判断一个数的平方与另一个数的关系时，最大为（x+1）/2.---Sqrt(x)<br>
10.判断给定的一个非负整数是否可以写成两个非负整数的平方的和。---Sum of Square Numbers<br>
在对给定的数字运用完函数sqrt之后，判断得出的值与强制转化为整型的数字是否相等。<br>

```c
bool judgeSquareSum(int c) {
    if (sqrt(c)==(int)sqrt(c))  return true;
    int temp=0;
    for (int i=1; i<c/i; i++) {
        temp=c-i*i;
        if (sqrt(temp)==(int)sqrt(temp)) return true;
    }
    return false;
}
```

11.当递归造成超时的错误时，一般转成递推来解决。---Climbing Stairs

```c
int climbStairs(int n) {
    int *result=(int*)malloc(sizeof(int)*(n+1));
    result[1]=1;
    result[2]=2;
    for (int i=3; i<=n; i++) {
        result[i]=result[i-1]+result[i-2];
    }
    return result[n];
}
```
