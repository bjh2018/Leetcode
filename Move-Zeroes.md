Move Zeroes
======

1.问题描述
------

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements. 
For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0]. <br>
Note:<br>
You must do this in-place without making a copy of the array.<br>
Minimize the total number of operations.<br>
把数组中的0都移到后面去，并且要保证其他不为0的数的顺序不发生改变，并且不能占用多余的空间，不能对数组复制一遍。<br>

2.思路
-----

因为要保证顺序不发生改变，所以要在原数组的原数组的原始情况下对数组进行变化。<br>

3.代码
------

```c
void moveZeroes(int* nums, int numsSize) {
    int start=0;
    for (int i=0; i<numsSize; i++) {
        if (nums[i]!=0) nums[start++]=nums[i];//如果不是0，就对nums重新赋值即可
    }
    for (int j=start; j<numsSize; j++) {//把后面的数全都赋值为0
        nums[j]=0;
    }
}
```
4.总结
---

要掌握这种不占用其他空间直接对数组进行改变的方法。还有就是这个题不用返回任何东西，只是对数组nums改变而已。
