Palindrome Number
=====
1.问题描述
-----

判断给定的数是不是回文数。<br>

2.代码
-----

```
bool isPalindrome(int x) {
    if (x<0) return false;
    else {
        int s=0;
        s=x;
        long result=0;
        while (x>0) {
            result=result*10+x%10;
            x=x/10;
        }
        if(result==s) return true;
        else return false;
    }
}
```

3.解题要点
----
（1）回文数：设n是一任意自然数。若将n的各位数字反向排列所得自然数n1与n相等，则称n为一回文数。<br>
注意：小数、负数都没有回文数<br>
（2）判断回文数的关键就是把给定的数反转以后是否与原整数相等，于是就想到了Reverse Integer这道题，运用这道题的思路解决判断回文数的问题。<br>

