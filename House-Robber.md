House Robber
======

1.问题描述
-------

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.
Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.<br>
假设你是你个专业的抢劫者，要抢劫的房子在一条街上，并且相连的房子如果在同一天晚上被抢劫的话，报警系统就会报警，给一个数组代表抢窃的方子中的钱数，问在不惊动警报的前提下，能强的最大的钱数。

2.思路
-----

解决这个问题最主要的就是解决不连续抢劫，同时要获得最大的钱数。于是就把i分奇数偶数两种情况，再运用函数max把每一步都取最大值，最后就会得到最大值。

3.代码
-----

```c
int max(int x, int y) {
    if (x>y) return x;
    else return y;
}
int rob(int* nums, int numsSize) {
    int a=0, b=0;
    for (int i=0; i<numsSize; i++) {
        if (i%2==0) {
            a=max(a+nums[i],b);
        }
        else {
            b=max(b+nums[i],a);
        }
    }
    return max(a,b);//最后再取一次两数中大的数，因为不知道房子的数目是奇数还是偶数
}
```

4.总结
-----

不连续加减的问题可以通过分指数的奇偶来确定是否加减。
