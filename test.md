# Huangshengjie

```cpp
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
