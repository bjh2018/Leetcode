Assign Cookies
=======

1.问题描述
------

假设你是一个很棒的家长，并想给你的孩子一些饼干。 但是，你应该给每个孩子最多一个饼干。 每个孩子都有一个贪婪的因素gi，这是孩子满足的一个饼干的最小尺寸; 每个cookie j的大小为sj。 如果sj> = gi，
我们可以将cookie j分配给孩子i，而孩子将会满足。 您的目标是最大化您的内容子项的数量并输出最大数量。<br>
注意：<br>
(1)你可能会认为贪婪因素总是正面的。<br>
(2)您不能为一个孩子分配多个Cookie<br>

2.解题要点
------
(1)一个孩子只能分得一个饼干，所以要把最大的饼干给贪婪值最大的孩子，就想到要把两个数组按一定的顺序排好，然后再分配饼干。<br>
(2)可以把最小的饼干放在第一个，去找适合它的孩子，然后把这个孩子的贪婪值加到比饼干最大的尺寸还大，就可以在下次遍历的时候不考虑这个孩子。<br>

3.代码
-----

```
void sort (int *a, int length) {
    int temp;
    for (int i=0; i<length; i++) {
        for (int j=0; j<length; j++) {
            if (a[i]<a[j]) {
                temp=a[i];
                a[i]=a[j];
                a[j]=temp;
            }
        }
    }
}
int findContentChildren(int* g, int gSize, int* s, int sSize) {
    int result=0;//用来记最终的结果
    sort (g,gSize);
    sort (s,sSize);
    for (int i=0; i<sSize; i++) {
        for (int j=gSize-1; j>=0; j--) {
            if (s[i]>=g[j]) {
                result++;
                g[j]=s[sSize-1]+1;
                break;
            }
        }
    }
    return result;
}
```

4.总结
-------
（1）因为两个数组都要按一定的顺序排列，所以写了个函数来实现。运用完sort函数后，都按从小到大的顺序排列。<br>
（2）一开始没有加break导致出现wrong answer的情况，因为这样会把一个饼干分给多个孩子，不符合题意。
