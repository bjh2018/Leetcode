Missing Number
==========

1.问题描述
--------

Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.<br> 
Example 1 <br>
Input: [3,0,1]<br>
Output: 2<br>
<br>
Example 2 <br>
Input: [9,6,4,2,3,5,7,0,1]<br>
Output: 8<br>
<br>
Note:<br>
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity<br>

2.思路
-------

把数组中的元素按从小到大的顺序排列后，定义一个数为0，遍历数组中的数，找出缺少的数。<br>

3.代码I
------

```c
int missingNumber(int* nums, int numsSize) {
    int n;
    for (int i=0; i<numsSize; i++) {
        for (int j=0;j<numsSize; j++) {
            if (nums[i]<nums[j]) {
                n=nums[i];
                nums[i]=nums[j];
                nums[j]=n;
            }
        }
    }
    int temp=0;
    for (int i=0; i<numsSize; i++) {
        if (nums[i]==temp) temp++;
        else break;
    }
    return temp;
}
```

4.代码II
------

```c
int missingNumber(int* nums, int numsSize) 
{
    int ans = nums[0]^1;
    for(int i = 1;i<numsSize;i++)
    {
        ans = (ans^(i+1))^nums[i];
    }
    return ans;
}
```

5.总结
-------

^异或运算<br>
异或运算当两个操作数(bool)同为true(1)或false(0)时,返回结果是false(0),否则返回结果是true(1)。<br>
整型int运算：int  a，b ； (a^b)^a=b;<br>
//a^b中，a，b相同的部分为0，不同的部分为1，(a^b)^a时，a和b相同的部分有1也有0，当是1时，因为(a^b)对应的位是0，1^0=1；当是0时，因为(a^b)对应的位是0，0^0=0；所以这样可以得到b与a相同的位。a和b不同的部分有1也有0，但肯定是与a对应的位相反，(a^b)上对应的位为1，当a上为1时，1^1=0；当a上为0时，0^1=1；所以这样 得到b与a不同的位。<br>
可以用来交换整型数字: int  a,b;  a=a^b; b=a^b=a;  a=a^b=b;
