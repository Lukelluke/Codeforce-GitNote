Codeforce 593-C

```cpp
目前我想到的方法，就是，先对(n^2)个数据进行组合，分成n组，每组各有n个元素。

然后，再进行第二步骤，每一小组分别和其他(n-1)组去进行求函数 f() 的运算，再找出当前分类中，最小的经过 f 函数运算的值；

以此类推，把所有组合各自的最小值拿出来比较，用最大的哪一个组合；

题目说了，重复结果的，随机打印一种组合分类方法即可；

```
```cpp
//应该是有潜在规律可依循的：
#include<algorithm>

#include<iostream>
using namespace std;


int a[400][400];

int main() {
	int n;
	cin >> n;

	int val = 1;
	for(int i = 1; i <= n; i++) {
		if(i & 1) {
			for(int j = 1; j <= n; j++)
				a[j][i] = val++;
		} else {
			for(int j = n; j > 0; j--)
				a[j][i] = val++;
		}
	}

	for(int i = 1; i <= n; i++) {
		for(int j = 1; j <= n; j++)
			cout << a[i][j] << ' ';
		cout << endl;
	}
}

```
