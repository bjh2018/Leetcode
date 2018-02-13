Roman to Integer
======

1.问题描述
------

Given a roman numeral, convert it to an integer.<br>
Input is guaranteed to be within the range from 1 to 3999.<br>

2.思路
----

把罗马数字转换成整数就要知道转换的法则，有以下几点:<br>
首先要来了解一下罗马数字表示法，基本字符有7个：I，V，X，L，C，D，M，分别表示1，5，10，50，100，500，1000。br>
在构成数字的时候，有下列规则：<br>
1、相同的数字连写，所表示的数等于这些数字相加得到的数，如：Ⅲ = 3；<br>
2、小的数字在大的数字的右边，所表示的数等于这些数字相加得到的数， 如：Ⅷ = 8；Ⅻ = 12；<br>
3、小的数字，（限于Ⅰ、X 和C）在大的数字的左边，所表示的数等于大数减小数得到的数，如：Ⅳ= 4；Ⅸ= 9；<br>
4、正常使用时，连写的数字重复不得超过三次。<br>
根据法则可以看出对前一个字是假时间取决于后一个数与他的大小关系，所以要建立一个量来确定加减号，又因为罗马数字不能直接进行加减，所以先写了一个函数把罗马数字转换成整数
直接进行比较。<br>

3.代码
-----

```c
int* romanIToint (char* s) {//写一个函数把罗马数字的字母转化成数字来处理
    int len=strlen(s);
    int *answer=(int *)malloc(sizeof(int)*(len));
    for (int i=0; s[i]!='\0';i++) {
        if(s[i]=='I') answer[i]=1;
        else if (s[i]=='V') answer[i]=5;
        else if (s[i]=='X') answer[i]=10;
        else if (s[i]=='L') answer[i]=50;
        else if (s[i]=='C') answer[i]=100;
        else if (s[i]=='D') answer[i]=500;
        else if (s[i]=='M') answer[i]=1000;
    }
    return answer;
}
int romanToInt(char* s) {
    int *result=(int *)malloc(sizeof(int)*(strlen(s)));
    result=romanIToint(s);
    int answer=0, pro=result[0];//用变量pro来记作是下一次要执行的操作
    for (int i=1; i<strlen(s); i++) {
        if (result[i]<=result[i-1]) {//当前的数比前一个数要小，所以要进行加的操作，不过假的要是前一个数，当前的数是加是减要看它与下一个数字之间的大小关系，而pro也就是来记载当前这个数的，在判断完它与下一个数的关系之后就可以在进行下一步操作
            answer=answer+pro;
            pro=result[i];
        }
        else {
            pro=result[i]-pro;//这一步中没有对answer进行操作，因为要做减法的话，就要把下一个数也进行计算，所以没有对answer在进行计算
        }
    }
    answer=answer+pro;//把最后的一个步骤再加上
    return answer;
}
```

4.总结
-----

当加减要由下一个数来决定的时候，可以用一个中间变量来分情况讨论。
