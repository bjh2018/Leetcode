 Two Sum
====
1.问题概括
---

在每组输入只有一种答案的情况下，不重复使用给定数组中的元素，看是否有两个数相加等于给定的数<br>

2.代码
---

```c
int* twoSum(int* nums,      /*  给定的数组 */
            int numsSize,   /*  数组中元素的个数*/
            int target)     /*  两个数的和 */
{
    int *answer=(int*)malloc(sizeof(int)*2);
    for(int i = 0; i < numsSize; i++)  // 对于每一个数据
    {
        // 循环其后面的数据看nums[i] + nums[j] == target是否成立
        // 其实就是看target - nums[i]在不在数组中
        for(int j = i + 1; j < numsSize; j++)
        {
            if(nums[i] + nums[j] == target)
            {
                answer[0] = i;
                answer[1] = j;
                break;
            }
        }
    }
    return answer;
}
```

3.malloc函数的要点 
--------
（1）头文件#include <malloc.h>或#include <stadlib.h><br>
（2）中文叫动态内存分配，用于申请一块连续的指定大小的内存块区域以void*类型返回分配的内存区域地址，当无法知道内存具体位置的时候，想要绑定真正的内存空间，就需要用到动态的分配内存。<br>
（3）void* 类型表示未确定类型的指针。C,C++规定，void* 类型可以通过类型转换强制转换为任何其它类型的指针。<br>
（4）要自己计算出所需的长度<br>
（5）使用公式<br>
(int *)malloc(size of(int)*长度)<br>
