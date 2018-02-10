 Implement strStr()
 ==========
 
 1.问题描述
 ------
 
 Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack. <br>
Example 1: <br>
Input: haystack = "hello", needle = "ll"<br>
Output: 2<br>
<br>
Example 2: <br>
Input: haystack = "aaaaa", needle = "bba"<br>
Output: -1<br>
如果第二个字符数组是第一个的一部分，就返回它们相等的第一个元素的指针，如果不是，就返回-1.<br>

2.思路
------

判断第二个数组是不是第一个数组的一部分是解决问题的关键，在解决这个问题的过程中调用了strncmp函数，来判断在一定的长度内两字符串是否相等。<br>

3.代码I
----

```c
int strStr(char* haystack, char* needle) {
    int len1=strlen(haystack);
    int len2=strlen(needle);
    if(len1==0&&len2==0) return 0;//两字符数组中都没有元素，那他们一定相等，返回0
    for (int i=0; i<=len1-len2; i++) {
    if (strncmp((haystack+i), needle, len2)==0)//haystack+i是haystack字符串比较的开始的位置，他开始的位置不断地变化，就可以找到两字符数组开始相等的位置
            return i;
    }
    return -1;
}
```

4.总结
-----

关于strncmp函数<br>
int strncmp ( const char * str1, const char * str2, size_t n );<br>
【参数】str1, str2 为需要比较的两个字符串，n为要比较的字符的数目。<br>
字符串大小的比较是以ASCII 码表上的顺序来决定，此顺序亦为字符的值。strncmp()首先将s1 第一个字符值减去s2 第一个字符值，若差值为0 则再继续比较下个字符，直到字符结束标志'\0'，若差值不为0，则将差值返回。例如字符串"Ac"和"ba"比较则会返回字符"A"(65)和'b'(98)的差值(-33)。<br>
注意：要比较的字符包括字符串结束标志'\0'，而且一旦遇到'\0'就结束比较，无论n是多少，不再继续比较后边的字符。
【返回值】若str1与str2的前n个字符相同，则返回0；若s1大于s2，则返回大于0的值；若s1 若小于s2，则返回小于0的值。<br>
