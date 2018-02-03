1.问题概括
You are climbing a stair case. It takes n steps to reach to the top.
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top? 
爬楼梯的时候每次只能爬1阶或2阶，问爬n阶的楼梯，有几种不同的方法？
2.解决方法
要想知道爬n阶楼梯的方法的数量，就要知道前一步走的是1阶还是2阶，有两种不同的情况，所以用加法，所以爬n阶台阶的方法的数量就等于爬n-1节台阶的方法的种数加上爬
n-2节台阶的方法的种数，考虑用递归或者是递推。
3.代码
（1）int climbStairs(int n) {
    int result;
    if (n==1) return 1;
    else if (n==2) return 2;
    else {
        result=climbStairs(n-1)+climbStairs(n-2);
    }
    return result;
    }
（2）int climbStairs(int n) {
    int *result=(int*)malloc(sizeof(int)*(n+1));
    result[1]=1;
    result[2]=2;
    for (int i=3; i<=n; i++) {
        result[i]=result[i-1]+result[i-2];
    }
    return result[n];
}
3.总结
（一）关于第一个代码，结果是Time Limit Exceeded
关于递归：很多时候递归是很直观的解决问题的方式，但往往递归的分支较多或层数较深的时候会导致程序运行超时或递归栈爆炸。
当递归造成超时的错误时，一般转成递推来解决。于是就有了第二个代码
（二）关于第二个代码从第一节开始到第n阶的种数放在一个数组里，再运用循环和递推公式就可以解决。
