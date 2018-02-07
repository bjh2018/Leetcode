Ugly Number
=======

1.问题描述
---------

Write a program to check whether a given number is an ugly number. <br>
Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.<br> 
Note that 1 is typically treated as an ugly number. <br>
这样的数字其实就是本身的质因数只有2，3，5，不含其他质因数的数。其中一是一个特例。<br>

2.思路
-----

只包含2，3，5这三个质因数说明如果不断地被2，3，5这三个数除，最终会得到一，根据这个条件就可以写出代码。<br>
注意把num是非正数和是一的情况单独拿出来讨论。<br>

3.代码
------

```c
bool isUgly(int num) {
    if (num==1) {
        return 1;
    }
    else if (num<=0) {
        return 0;
    }
    else {
        for (int i=2; i<6; i++) {
            while (num%i==0) {//让num除以i的前提，并用一个while循环来实现对num的化简。
                num=num/i;
            }
        }
        if (num==1) return 1;
        else return 0;
    }
}
```
4.其他简易代码
---------

```c
bool isUgly(int num) {   
    for(int i = 2; i < 6 && num; i++)//让i等于1没有意义，i<6并且num为真，当num为0时while循环是一个死循环，num为false。
    {
        while(num % i == 0)
            num /= i;
    }
    
    return num == 1;//num==1是一个判断条件，直接返回判断的结果即可。
}
```

5.总结
-------

for循环的第二个语句不满足时直接终止for循环，不再进行++的操作。
