函数
=====

memset函数
------------

(1)头文件  #include<mem.h><br>
(2)函数原型  void *memset(void *buffer, int c, int count)<br>
   其中buffer为指针或数组    c是赋给buffer的值   count是接受赋值的长度<br>
(3)作用：1)void *memset(void *s,int c,size_t n)<br> 
          总的作用：将已开辟内存空间 s 的首 n 个字节的值设为值 c。<br>
        2)memset() 函数常用于内存空间初始化。如：<br>
           char str[100];<br>
           memset(str,0,100);<br>
        3)memset可以方便的清空一个结构类型的变量或数组。如：
           
 ```c
           struct sample_struct{
                      char csName[16];
                       int iSeq;
                       int iType;
           };
 ```
           
           对于变量：<br>
           struct sample_strcut stTest;<br>
           一般情况下，清空stTest的方法：<br>
           stTest.csName[0]='/0';<br>
           stTest.iSeq=0;<br>
           stTest.iType=0;<br>
           用memset就非常方便：<br>
           memset(&stTest,0,sizeof(struct sample_struct));<br>
           如果是数组：<br>
           struct sample_struct TEST[10];<br>
           则memset(TEST,0,sizeof(struct sample_struct)*10); <br>
           
strncmp函数
------

(1)头文件  #include<string.h><br>
(2)函数原型    int strncmp ( const char * str1, const char * str2, size_t n );<br>
              其中str1, str2 为需要比较的两个字符串，n为要比较的字符的数目<br>
(3)作用 字符串大小的比较是以ASCII 码表上的顺序来决定，此顺序亦为字符的值。strncmp()首先将s1 第一个字符值减去s2 第一个字符值，若差值为0 则再继续比较下个字符，直到字符结束标志'\0'，若差值不为0，则将差值返回。例如字符串"Ac"和"ba"比较则会返回字符"A"(65)和'b'(98)的差值(-33)。注意:要比较的字符包括字符串结束标志'\0'，而且一旦遇到'\0'就结束比较，无论n是多少，不再继续比较后边的字符。<br>
(4)返回值     若str1与str2的前n个字符相同，则返回0;若s1大于s2，则返回大于0的值;若s1 若小于s2，则返回小于0的值。<br>

位运算
======

按位异或运算(^)
-----

(1)用法：异或运算当两个操作数(bool)同为true(1)或false(0)时,返回结果是false(0),否则返回结果是true(1)。<br>
(2)运算法则：1. a ^ b = b ^ a  
　　        2. a ^ b ^ c = a ^ (b ^ c) = (a ^ b) ^ c
　          3. d = a ^ b ^ c 可以推出 a = d ^ b ^ c------d ^ b ^ c=(a ^ b ^ c) ^ b ^ c= a ^ ( b ^ b ) ^ ( c ^ c)= a ^ 0 = a<br> 
            4. a ^ b ^ a = b如上
(3)可以用来交换整型数字: int  a,b;  a=a^b; b=a^b=a;  a=a^b=b;

按位与运算(&)
---

(1)用法：按位与运算将两个运算分量的对应位按位遵照以下规则进行计算：<br>
        0 & 0 = 0, 0 & 1 = 0, 1 & 0 = 0, 1 & 1 = 1。<br>
        即同为 1 的位，结果为 1，否则结果为 0。<br>
(2)“与运算”的特殊用途：<br>
    1)清零。如果想将一个单元清零，即使其全部二进制位为0，只要与一个各位都为零的数值相与，结果为零。<br>
    2)取一个数中指定位<br>
      方法：找一个数，对应X要取的位，该数的对应位为1，其余位为零，此数与X进行“与运算”可以得到X中的指定位。<br>
      例：设X=10101110，<br>
      取X的低4位，用 X & 0000 1111 = 0000 1110 即可得到；<br>
      还可用来取X的2、4、6位。<br>
      
按位或运算(|)
------

(1)用法：按位或运算将两个运算分量的对应位按位遵照以下规则进行计算：<br>
         0 | 0 = 0, 0 | 1 = 1, 1 | 0 = 1, 1 | 1 = 1<br>
         即只要有1个是1的位，结果为1，否则为0。<br>
         另，负数按补码形式参加按位或运算。<br>
(2)或运算”特殊作用：<br>
   常用来对一个数据的某些位置1。<br>
   方法：找到一个数，对应X要置1的位，该数的对应位为1，其余位为零。此数与X相或可使X中的某些位置1。<br>
   例：将X=10100000的低4位置1 ，用 X | 0000 1111 = 1010 1111即可得到。<br>

取反运算符
----

(1)参加运算的一个数据，按二进制位进行“取反”运算。<br>
   运算规则：~1=0；   ~0=1；<br>
   即：对一个二进制数按位取反，即将0变1，1变0。<br>
(2)使一个数的最低位为零，可以表示为：a&~1。<br>