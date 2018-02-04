Arranging Coins
===
1.问题概括
---

You have a total of n coins that you want to form in a staircase shape, where every k-th row must have exactly k coins.
Given n, find the total number of full staircase rows that can be formed.
n is a non-negative integer and fits within the range of a 32-bit signed integer.<br>
你总共有n个硬币，你想要形成一个阶梯形状，每个第k行必须有正好k个硬币。给定n，找到可以形成的完整楼梯行的总数。n是一个非负整数，并且在32位有符号整数的范围
内。<br>
Example<br>
n = 5<br>
<br>
The coins can form the following rows:<br>
¤<br>
¤ ¤<br>
¤ ¤<br>
<br>
Because the 3rd row is incomplete, we return 2<br>

2.解决方法
---

知道了硬币的总数，想到用减法，当减到最后n的值小于最后的一列应该有的硬币数，就停止，并用一个Sum来记录已经排好的楼梯的行数。<br>

3.代码
---

```c<br>
int arrangeCoins(int n) {
    int sum=1;
    for (int i=1; i>0; i++) {
        if (n>=i) {
            n=n-i;
            sum++;}
        else break;
    }
    return sum-1;
}
```
