Hamming Distance
======

1.问题描述
-----

The Hamming distance between two integers is the number of positions at which the corresponding bits are different.
Given two integers x and y, calculate the Hamming distance.<br>
Note:<br>
0 ≤ x, y < 2^31.
Example:<br>
Input: x = 1, y = 4<br>
<br>
Output: 2<br>
<br>
Explanation:<br>
1   (0 0 0 1)<br>
4   (0 1 0 0)<br>
<br>
The above arrows point to positions where the corresponding bits are different.<br>
其实就是把给定的数转成二进制数，并且找出它们在相同的位数上不同的情况的个数。

2.思路
-----

把两个数转成二进制后，把他们各位的数放在一个数组中，比较两个数组中元素不同的个数，即为所求。

3.代码
-----

```
```

4.总结
----
掌握了十进制转二进制的方法，用x除以2的余数做第一位数，再把x除以2，再取余数，直到余数为零。
