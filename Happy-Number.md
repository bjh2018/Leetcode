Happy Number
=======

1.问题描述
----------

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.<br>
<br>
Example: 19 is a happy number<br>
<br>
1^2+9^2= 82<br>
8^2+2^2= 68<br>
6^2+8^2= 100<br>
1^2+0^2+0^2= 1<br>
其实就是说一个数的各位的平方相加组成一个新的数，在重复这个操作，如果存在周期，且没有一个数等于1，就返回错误，如果有数等于1，就是返回正确。<br>

2.思路
--------

一开始不知道该怎么知道他是否具有周期性，就参考了一下答案，发现是写了一个函数，把得到的数不断地进行这个函数，并且取两个数都等x，使其中一个调用函数一次，另一个调用函数两次，如果两数有相等的时候，就返回错误，如果有一个等于1就返回正确。

3.代码
-----

```
int sum(int n) {
    int sum=0;
    int temp;
    while (n>0) {
       temp=n%10;
        sum=sum+temp*temp;
        n=n/10;
    }
    return sum;
}
bool isHappy(int n) {
    int x,y;
    x=n;
    y=n;
    do{
    x=sum(x);
    y=sum(y);
    y=sum(y);
    }while(x!=y);//让y执行两次sum函数，使得do……while函数每执行一次就会让y比x多执行一次，如果存在周期的话，肯定会存在x=y的情况。
    if (x==1) return 1;
    else return 0;
}
```

4.总结
-------

掌握了判断不断算出来的数是否具有周期的办法。
