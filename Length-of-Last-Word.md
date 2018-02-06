Length of Last Word
=========

1.问题描述
--------

Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.
If the last word does not exist, return 0.<br>
Note: <br>
A word is defined as a character sequence consists of non-space characters only.<br>
一个单词是指不包含空格的字母。<br>
Example:<br>
Input: "Hello World"<br>
Output: 5<br>

2.思路
-------

根据对单词的定义可知单词中不包含空格，并且根据求的最后一个单词的长度，得出应该让字符串倒序输出来计算最后一个单词的长度。<br>

3.代码
--------

```
int lengthOfLastWord(char* s) {
    int len=strlen(s);
    int sum=0;
    for (int i=len-1; i>=0; i--) {
        if (s[i]!=' ') {
            sum++;
        }
        else if (s[i]==' '&&(s[i+1]=='\0'||s[i+1]==' ')) {
            sum=sum;
        }
        else break;
    }
    return sum;
}
```

4.错误的点
---------

（1）一开始没有考虑到最后一个字母为空格的情况，从而导致错误，后来想到可能会有连串的空格在最后的情况，所以就想到用查看它后面的情况，从而断定空格是单词的开始还是单词的结尾。<br>
（2）如果空格的后面是空格或者\0就说明空格是在结尾处，就继续进行，直到不是空格,就让sum进行加一的操作。

5.总结
-------

要考虑到事情的多个情况，而不是单纯的只考虑一种情况。
