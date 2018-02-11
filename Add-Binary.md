Add Binary
======

1.问题描述
---------

Given two binary strings, return their sum (also a binary string). <br>
For example,<br>
a = "11"<br>
b = "1"<br>
Return "100".<br>
就是把字符类型的按二进制的整数求和，再以二进制和字符类型输出。

2.思路
----

一开始是打算直接把两个字符数组中所有的情况都列出来计算（因为不知道字符型的数该如何相加，结果一直出错，因为要分好多好多种情况），其实只要按照平常整数转二进制数
的方法即可，还有就是要倒着进行计算。

3.代码
---

```c
char *addBinary(char *a, char *b) {
    int i,j, temp,temp1,lenA,lenB,len;
    char *str;
    lenA = strlen(a);
    lenB = strlen(b);
    len = lenA>lenB?lenA:lenB;//找出两字符数组中较长的长度
    str= (char *)malloc((len+2)*sizeof(char));//申请的空间要大于最大的字符串长度加1，第一个1指字符串相加后可能进位，第二个1指字符串最后的'\0'结束字符
    memset(str,'\0',(len+2)*sizeof(char));//把字符串中的元素全都初始化为'\0'
    j = len-1;temp  = 0;
    for(i=len;i >= 0 && lenA > 0 && lenB > 0; i--){
        *(str+i) = ((*(a+lenA-1)-'0') + (*(b+lenB-1)-'0') + temp)%2 + '0';//-'0'是把字符型的转换成整型，+'0'是把整型转化为字符型
        temp = ((*(a+lenA-1)-'0') + (*(b+lenB-1)-'0') + temp)/2;
        lenA--;
        lenB--;
    }
    if(lenA == 0){//则对b字符串进行赋值给str
        for(i=i; lenB > 0;i--){
            *(str+i) = ((*(b+lenB-1)-'0') +temp)%2 + '0';
            temp = ((*(b+lenB-1)-'0') +temp)/2;
            lenB--;
        }
    }
    else if(lenB == 0){//对a字符串进行赋值给str
        for(i=i; lenA >0;i--){
            *(str+i) = ((*(a+lenA-1)-'0') + temp)%2+'0';
            temp = ((*(a+lenA-1)-'0') + temp)/2;
            lenA--;
        }
    }
    if(temp == 1) {*(str) = temp+'0';return str;}//若temp进位为1，则赋值给str
    return str+1;//表明字符串的第一个元素是str[1]
}
````

4.总结
------

（1）十进制转成二进制的方法<br>
用x%2做第一位的数，对x=x/2的操作，在进行取余的操作。<br>
在这个题目中不同的是要进行进位的操作，于是就定义了一个temp，在进行完去余的操作之后，再令temp等于两数之和除以2，达到进位的目的。<br>
（2）关于字符类型与整型之间的转化<br>
-'0'是字符型转化为整型         +'0'是整型转化为字符型<br>
（3）关于函数memset<br>
头文件  #include<mem.h><br>
memset()函数原型是extern void *memset(void *buffer, int c, int count)<br>     
buffer：为指针或是数组, <br>
c：是赋给buffer的值,<br>
count：是buffer的长度.<br>
       1)void *memset(void *s,int c,size_t n)<br>
        总的作用：将已开辟内存空间 s 的首 n 个字节的值设为值 c。<br>
       2).memset() 函数常用于内存空间初始化。如：<br>
           char str[100];<br>
           memset(str,0,100);<br>
       3).memset可以方便的清空一个结构类型的变量或数组。<br>
           如：<br>
           struct sample_struct{<br>
                      char csName[16];<br>
                       int iSeq;<br>
                       int iType;<br>
           };<br>
           对于变量：<br>
           struct sample_strcut stTest;<br>
           一般情况下，清空stTest的方法：<br>
           stTest.csName[0]='/0';<br>
           stTest.iSeq=0;<br>
           stTest.iType=0;<br>
           用memset就非常方便：<br>
           memset(&stTest,0,sizeof(struct sample_struct));<br>
           如果是数组：<br>
           struct sample_struct TEST[10];<br>
           则<br>
           memset(TEST,0,sizeof(struct sample_struct)*10);<br>
 （4）关于要删除字符数组（数组）的前几位的方法，只需要把起点改变即可。          
