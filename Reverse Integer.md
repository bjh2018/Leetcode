Reverse Integer
====

1.问题描述
----

Given a 32-bit signed integer, reverse digits of an integer.<br>
给定一个32位有符号整数，确定该整数的反转数字。<br>
Example 1:<br>
Input: 123<br>
Output:  321<br>
<br>
Example 2:<br>
Input: -123<br>
Output: -321<br>
<br>
Example 3:<br>
Input: 120<br>
Output: 21<br>
根据例子可以看出当x为负数时，只是让数字反转，并没有改变符号，所以要有一个标准来判断其正负，并在最后为其加上负号。（temp）<br>
<br>
Note:<br>
假设我们处理一个只能保持32位有符号整数范围内的整数的环境。 当函数在反向整数溢出时返回0。<br>

2.代码
------

```
int reverse(int x) {
    int temp=0;//作为判断x的正负的标志，若x为正，则temp为0，若x为负，则temp为1；
    if(x<0) {
        temp=1;
        x=-x;
    }
    long result=0;//定义返回值为long型是因为最终的结果可能会超出整数的最大范围，造成溢出
    while(x>0) {
        result=result*10+x%10;//解决问题的关键1.
        x=x/10;//
    }
    if (temp==1) result=-result;
    if (result>2147483647||result<-2147483647) return 0;//整数类型的数的范围
    return (int)result;
}
```

3.解题要点
------
（1）在得出该整数的个位之后要把它当作新的整数的最高位，同时x也要除以10再除以10取余数获得新整数的下一位，在不断地乘以10，使得原整数的个位成为最终结果的最高位。<br>
（2）因为可能出现反过来的数溢出的情况，把最终结果定义为long型，如果没有溢出，再用强制类型转换把结果转化为整型。<br>
