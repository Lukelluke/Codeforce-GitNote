Codeforce 593-B

```cpp
//593-B
//每个礼物至少被使用一次
//礼物盒子允许为空
//每个盒子中，每种礼物数量最多为一个，不能多
//最后的结果要对(10^9 + 7)取模

/*
最原始的思路：
礼物 n 种，盒子 m 个：
每个盒子有 n！ 种组合方案；
所以总共有(n!)^m种可能
再从其中去掉不合理的情况(没有把所有礼物都考虑上)(必须所有礼物都用上，而不能有没用过的礼物)
***************************************************************************
肯定得改进，不然绝对不合理；
题目提示用“哈希表”
*/
看一个很厉害的Python代码

```
```python

n, m = list(map(int, input().split()))

'''
礼物 n 种，盒子 m 个：
这句话的意思是：可以 一次性 输入多个元素，分别对应地赋值给前面的  n,m 等参数；
int是对输出的数据类型进行强制转换
(默认是输出字符串) n,m = input().split();
Python 2 里面用的是 raw_input();

然后还可以把输入保存到list里面，Python 3 需要在前面用list( )处理一下；如上一句代码所示；
参考1：https://blog.csdn.net/zhang_xiaomeng/article/details/71633235
参考2：https://blog.csdn.net/zheng_integer/article/details/54986762
'''


mod = 10 ** 9 + 7
print(pow(  (pow(2, m, mod) - 1)  , n, mod  ) )

'''
pow(x, y[, z])
函数是计算x的y次方，如果z在存在，则再对结果进行取模，其结果等效于pow(x,y) %z

里面 -1 减一表示的是，先对盒子做考虑，每个礼物对所有盒子来讲，要么有，要么没有，所以总共有(2^m)种情况，然后去掉一种不合理情况，(每个盒子都不包含这种礼物，不合理)；
再紧接着，对礼物做考虑，每种礼物都要做这么一个过程，所以再做指数运算；，最后结果记得取模；
*************************************

太牛逼了！！！
学习一个！！！
'''

```
```cpp
//c++方法；

#include<bits/stdc++.h>
using namespace std;
#define mod 1000000007
long long modularExponentiation(long long x,long long n,long long M)
{该函数作用是：求 x 的 n 次方，并将结果对 M 取模
    long long result=1;
    while(n>0)
    {
        if(n % 2 ==1)
            result=(result * x)%M;
        x=(x*x)%M;
        n=n/2;
    }
    return result;
}
int main()
{
	long long n,m,ans;
	cin>>n>>m;
	ans=modularExponentiation(2,m,mod);
	ans=(ans%mod-1+mod)%mod;
	ans=modularExponentiation(ans,n,mod);
	cout<<ans<<endl;
}
```
```cpp
//其他代码答案：
#include<bits/stdc++.h>
#define ll long long
using namespace std;
const ll M = 1e9 + 7;
 
 
ll power(ll x, ll y){
    x %= M;
    ll ans = 1;
    while(y){
        if(y & 1)
            ans = (ans * x) % M;
        y >>= 1LL;
        x = (x * x) % M;
    }
    return ans;
}

int main()
{ long long  n,m;
  cin>>n>>m;
  long long  a=power(2,m);
    a=(a%1000000007-1%1000000007+1000000007)%1000000007;
   long long  ans=power(a,n);
        cout<<ans;
return 0;
}
```
###注意点1：
![Alt text](./1571390112144.png)
###注意点2：
![Alt text](./1571390134965.png)
###注意点3：
![Alt text](./1571398419638.png)


###4.define 和 typedef 区别
https://blog.csdn.net/summer00072/article/details/80918483
```cpp

	https://blog.csdn.net/summer00072/article/details/80918483
常见形式：
	typedef int status;
	#define a 常量

codeforce上看到的用define，所以来查查区别：
	#define ll long long
	typedef long long ll;

区别：
	1.define是全局，typedef有作用域限制；
	2.对指针的操作不同：

		#define INTPTR1 int*

		typedef int* INTPTR2;

		INTPTR1 p1, p2;

		INTPTR2 p3, p4;

		含义分别为，

		声明一个指针变量p1和一个整型变量p2

		声明两个指针变量p3、p4
		//因为INTPTR1 是 int* 类型的，所以相当于int* a,b;
		//int* a,b; <=>等价于 int*a ;  int b ;
		//记住就行；
```


###指针常量和常量指针的区别
https://blog.csdn.net/qq_36132127/article/details/81940015
```cpp
https://blog.csdn.net/qq_36132127/article/details/81940015
1.指针常量：本质上是一个常量，指针用来说明常量的类型，表示该常量是一个指针类型的常量。
  在指针常量中，指针自身的值是一个常量，不可改变，始终指向同一个  地址  。在定义的同时必须初始化。
//指针常量本身是一个常量，指向一个固定地址，--->>>但是该地址的内容是可以改变的！！！


2.常量指针，实质上是一个指针，常量表示指针指向的内容，说明该指针指向一个“常量”。
  在常量指针中，指针指向的  内容  是不可改变的，指针看起来好像指向了一个常量。
//常量指针是一个指针，它指向一个常量，——->>>所指向的内容不能改变！！！

```
