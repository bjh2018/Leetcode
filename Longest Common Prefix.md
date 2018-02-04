 Longest Common Prefix
 ======
 
 1.问题描述
 -------
 
 Write a function to find the longest common prefix string amongst an array of strings.<br>
 编写一个函数来查找字符串数组中最长的公共前缀字符串<br>
 （个人理解）有一个由字符串组成的字符数字，找出各个字符串的公共部分，并返回这个字符串。<br>
 
 2.解题思路
 ----
 
 先把第一个字符串当作是各个字符串的公共部分，与其他的进行比较，如果出现不一样的地方，就把出现不同的那个字母改成'\0'。如果第一个字母就是'\0'，就返回"",<br>
 如果不是，就返回字符串。<br>
 
 3.代码
 ------
 
 ```
 char* longestCommonPrefix(char** strs, int strsSize) {
    for (int i=1; i<strsSize; i++) {
        for (int j=0; strs[0][j]!='\0'; j++) {
            if (strs[i][j]!=strs[0][j]) {
                strs[0][j]='\0';
                break;
            }
        }
    }
    if (strs[0]=='\0') return "";
    else return strs[0];
}
```

4.总结
-----

（1）当遇到求公共部分的题目的时候，可以把第一个元素当作公共部分与其他的元素进行比较。<br>
（2）由题目中的char** strs可知strs是一个二维数组，所以只需返回strs[0]即可。<br>
（3）一开始把strs[0][j]!='\0'写成了strs[i][j]!='\0'导致错误，因为第二个字符串可能比已经的出来的公共部分要短，这样就会把公共部分拉长，从而造成错误。<br>
（4）字符串的结束标志时'\0'，并且也是遇到'\0'结束，可以充分利用这个特性解决问题。
