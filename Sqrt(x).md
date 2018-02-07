Sqrt(x)
======

1.问题描述
---------

Implement int sqrt(int x).
Compute and return the square root of x.
x is guaranteed to be a non-negative integer.<br>

Example 1: <br>
Input: 4<br>
Output: 2<br>
<br>
Example 2: <br>
Input: 8<br>
Output: 2<br>
Explanation: The square root of 8 is 2.82842..., and since we want to return an integer, the decimal part will be truncated.<br>
其实就是寻找一个整数，它的平方小于等于给定的整数，并且给定的整数应该小于该数加一的平方。可以通过循环来实现。<br>

2.思路
-----

让循环的数字i从一开始循环，并且要用除法来判断是否符合条件，还要注意整数除以整数还是整数，所以要加等号。

3.代码
-----

```c
int mySqrt(int x) {
    int result;
    if (x==0) return 0;
    for (int i=1; i>=0; i++) {
        if (i<=x/i&&i>=x/(i+1)) {
           result=i; 
            break; 
        }
    }
}
```

4.简易代码
-------

```c
int mySqrt(int x) {
    int left=1,right=x,mid=0;
    if(x==0) return 0;
    while(1)
    {
        
        mid=(left+right)/2;
        //mid*mid容易导致int溢出
        if(mid>x/mid) right=mid-1;
        else
        {
            if(mid+1>x/(mid+1)) return mid;
            left=mid+1;
        }

    }
    return right;
}
```

4.总结
-----

（1）一个数的平方容易造成int溢出，一般是转成除法来判断。<br>
（2）判断一个数的平方与另一个数的关系时，最大为（x+1）/2.
