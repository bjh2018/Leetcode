Remove Element
==========

1.问题描述
--------

Given an array and a value, remove all instances of that value in-place and return the new length. <br>
Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.<br>
The order of elements can be changed. It doesn't matter what you leave beyond the new length.<br>
Example: <br>
Given nums = [3,2,2,3], val = 3,<br>
<br>
Your function should return length = 2, with the first two elements of nums being 2.<br>
给定一个数组，在不占用其他多余的空间的条件下，把其中等于val的数除去，并返回新的长度。

2.思路
-----

想到昨天做的题目，还是把满足条件的元素放在前面，比较的因素是看其是否与val相等。<br>

3.代码
-----

```c
int removeElement(int* nums, int numsSize, int val) {
    int start=0;
    for (int i=0; i<numsSize; i++) {
        if (nums[i]!=val) nums[start++]=nums[i];
    }
    return start;
}
```

4.总结
----

注意在不占用多余的空间解决题目的方法。
