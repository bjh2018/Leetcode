Remove Duplicates from Sorted Array
=========

1.问题描述
-----

Given a sorted array, remove the duplicates in-place such that each element appear only once and return the new length.
Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
Example: <br>
Given nums = [1,1,2],<br>
<br>
Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
It doesn't matter what you leave beyond the new length<br>
其实就是把一个数组中重复的数组移除，并且要返回新的长度。要求是不能占用多余的空间，不能新建一个数组来达到目的。<br>

2.思路
------

（1）因为要找重复的部分，所以第一个元素肯定不重复，而且做完变动的数组的长度一定小于等于原数组的长度，所以就把原数组的值直接复制给改动的数组即可。<br>
（2）注意：如果数组的长度为零的话，就要返回长度为零<br>
（3）最后要对标度加一，因为标度与长度不等价<br>

3.代码I
----

```c
int removeDuplicates(int* nums, int numsSize) {
    int start=0;
    for (int i=1; i<numsSize; i++) {
        if (nums[i]!=nums[start]) nums[++start]=nums[i];//如果遍历数组，发现与nums[0]不同的数，就把它赋值给nums[1]
    }
        return (numsSize>0?start+1:start);
}
```

4.总结
-----

（1）i++与++i的区别（复习）<br>
i++:先赋值，再加一  ++i:先加一，再赋值<br>
备注：在赋值运算中有区别，单独使用没有区别<br>
例子1：单独使用<br>
for(int i=0;i<10;i++）{ }<br>
for(int i=0;i<10;++i) { }<br>
这样使用没有区别<br>
<br>
例子2：赋值运算 <br>
a=i++;<br>
（分解：a=i； i=i+1；）<br>
a=++i;<br>
（分解：i=i+1；a=i；）<br>
这样使用a的值是不一样的<br>
注意:如果把++start换成strat++,那么start就为0，不符合题意<br>
（2）学会掌握这种不利用其他空间就实现对数组中重复的元素删除的功能。还要注意要在清楚知道新的数组的长度要小于等于原数组，以免造成重复的现象。
