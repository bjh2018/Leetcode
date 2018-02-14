Single Number
====

1.问题描述
-----

Given an array of integers, every element appears twice except for one. Find that single one.<br>
Note:<br>
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?<br>
在不占用多余的空间的条件下，找出在一个数组中只出现一次的数，并返回这个数。

2.思路
-----

因为要找到只出现一次的数，所以要对数组进行遍历，并用一个temp来看是否由与它相同的数出现，从而确定要输出的数。<br>

3.代码I（超时）
-----

```c
int singleNumber(int* nums, int numsSize) {
    int i=0, temp=0;
    for (int i=0; i<numsSize; i++) {
        for (int j=0; j<numsSize; j++) {
            if (nums[j]==nums[i]) {
                temp++;
            }
    }
        if (temp==1) {
                break;
        }
        temp=0;
    }
    return nums[i];
}
```
4.代码II（Accepted）
----

```c
int singleNumber(int* nums, int numsSize) {
 int x = 0;
 int i = 0;
 for (i = 0; i<numsSize;i++)
 {
   x=x^nums[i];
 }
 return x;
}
```
5.总结
----

第二个代码运用了异或运算，根据异或运算的性质可以知道，相同的数进行异或运算结果为0，0与其他数进行异或运算后还是其本身，于是就可以得到只出现一次的数了。
