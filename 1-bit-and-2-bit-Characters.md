1-bit and 2-bit Characters
=======

1.问题描述
---------

We have two special characters. The first character can be represented by one bit 0. The second character can be represented by two bits (10 or 11). <br>
Now given a string represented by several bits. Return whether the last character must be a one-bit character or not. The given string will always end with a zero.<br>
Example 1:<br>
Input: <br>
bits = [1, 0, 0]<br>
Output: True<br>
Explanation: <br>
The only way to decode it is two-bit character and one-bit character. So the last character is one-bit character.<br>
<br>
Example 2:<br>
Input: <br>
bits = [1, 1, 1, 0]<br>
Output: False<br>
Explanation:<br> 
The only way to decode it is two-bit character and two-bit character. So the last character is NOT one-bit character.<br>
<br>
Note: <br>
1 <= len(bits) <= 1000.<br>
bits[i] is always 0 or 1.<br>
其实就是说一个数组由1和0组成，1和后面的数字组成一个2位的数，而0如果在前的话就只能构成一位。

2.思路
------

因为是要判断最后一位是单独的一位还是两位，就想到要从开始遍历，如果是1就加2，是0的话就加1，并把i+1与数组的尺寸作比较。<br>

3.代码
------

```c
bool isOneBitCharacter(int* bits, int bitsSize) {
    int i=0;
    for (i=0; i+1<bitsSize; i++) {
        if (bits[i]==1) i++;
    }
    if (i==bitsSize-1) return 1;
    else return 0;
}
```

```c
bool isOneBitCharacter(int* bits, int bitsSize) {
    int i = 0;
    while (i < bitsSize)
    {
        if (i == (bitsSize - 1))
            return true;
        
        i = bits[i] ? (i + 2) : (i + 1);
    }
    return false;
}
```

4.总结
-----

认真理解题目！！！！
