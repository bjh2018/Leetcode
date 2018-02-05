Third Maximum Number
=========

1.问题描述
----

Given a non-empty array of integers, return the third maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).<br>
给一组不空的整数数组，返回数组中第三大的数， 如果不存在第三大的数，就返回最大的数。<br>
Example 1:<br>
Input: [3, 2, 1]<br>
<br>
Output: 1<br>
<br>
Explanation: The third maximum is 1.<br>
<br>
Example 2:<br>
Input: [1, 2]<br>
<br>
Output: 2<br>
<br>
Explanation: The third maximum does not exist, so the maximum (2) is returned instead.<br>
<br>
Example 3:<br>
Input: [2, 2, 3, 1]<br>
<br>
Output: 1<br>
<br>
Explanation: Note that the third maximum here means the third maximum distinct number.<br>
Both numbers with value 2 are both considered as second maximum.<br>

2.思路
-----

根据第三个例子可以得知，重复的数字不向下再排序，而是和上一个同样的数占同一个位次。于是就想到再给数组排序的同时，把一样的数的除第一个数意外都表示成最小的整数-2147483647，再进行排序，同时也要
用一个数几下重复的数字的个数，以便计算该数组的有效长度，看是返回最大值还是第三大的值。<br>

3.代码
-----

```
int thirdMax(int* nums, int numsSize) {
    int temp;
    int determine=0;
    for (int i=0; i<numsSize; i++) {
        for (int j=i+1; j<numsSize; j++) {
            if (nums[i]<nums[j]) {
                temp=nums[i];
                nums[i]=nums[j];
                nums[j]=temp;
            }
            else if (nums[i]==nums[j]&&nums[i]!=-2147483647) {
                nums[j]=-2147483647;
            determine=determine+1;
            }
        }
    }
    if (numsSize<3&&determine==0) return nums[0];
    else if (numsSize>=3&&numsSize-determine<3) return nums[0];
    else return nums[2];
}
```
4.总结
------

(1)一开始没有加上nums[i]!=-2147483647这个条件，导致重复的数字的个数增加，导致错误。<br>
(2)因为是找大的数，所以就把重复的数字写成了最小的。<br>

