 Sum of Square Numbers
=====
1.问题描述
----

判断给定的一个非负整数是否可以写成两个非负整数的平方的和。<br>

2.代码
----

```
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

3.解题要点
-------
（1）让其中一个数变化，然后判断另一个数是否满足能被整开方。<br>
（2）其中要确定变化的那个数的范围，可以确定最大的数也比c除以这个数要小，因为要做除数，所以不能为0，要把本身能整开方的情况列出来。<br>
（3）开方的函数 sqrt，判断是否能整开方的条件是看sqrt(c)==(int)sqrt(c)是否成立。<br>
