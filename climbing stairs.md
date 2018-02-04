Climbing Stairs
===
1.问题概括<br>
---

You are climbing a stair case. It takes n steps to reach to the top.<br>
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top? <br>
爬楼梯的时候每次只能爬1阶或2阶，问爬n阶的楼梯，有几种不同的方法？<br>

#2.解决方法<br>
---

要想知道爬n阶楼梯的方法的数量，就要知道前一步走的是1阶还是2阶，有两种不同的情况，所以用加法，所以爬n阶台阶的方法的数量就等于爬n-1节台阶的方法的种数加<br>上爬n-2节台阶的方法的种数，考虑用递归或者是递推。<br>

3.代码<br>
---

（1）int climbStairs(int n) {<br>
    int result;<br>
    if (n==1) return 1;<br>
    else if (n==2) return 2;<br>
    else {<br>
        result=climbStairs(n-1)+climbStairs(n-2);<br>
    }<br>
    return result;<br>
    }<br>
（2）int climbStairs(int n) {<br>
    int *result=(int*)malloc(sizeof(int)*(n+1));<br>
    result[1]=1;<br>
    result[2]=2;<br>
    for (int i=3; i<=n; i++) {<br>
        result[i]=result[i-1]+result[i-2];<br>
    }<br>
    return result[n];<br>
}<br>

4.总结<br>
---

（一）关于第一个代码，结果是Time Limit Exceeded<br>
关于递归：很多时候递归是很直观的解决问题的方式，但往往递归的分支较多或层数较深的时候会导致程序运行超时或递归栈爆炸。<br>
当递归造成超时的错误时，一般转成递推来解决。于是就有了第二个代码<br>
（二）关于第二个代码从第一节开始到第n阶的种数放在一个数组里，再运用循环和递推公式就可以解决。<br>
