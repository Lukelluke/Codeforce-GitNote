#Codeforce 593-A
http://codeforces.com/contest/1236/problem/A
    
	 选石头（实质是处理第二摞）


```
//方法一：

    #include <iostream>
	using namespace std;
 
	int N, a, b, c, ans, current, current1;
	int main()
	{
	    cin >> N;
	    while(N--)
	    {
	        ans = 0;
	        cin >> a >> b >> c;
	        while(c >= 2 && b)
	            ans += 3, c -= 2, b--;
	        while(b >= 2 && a)
	            ans += 3, b -= 2, a--;
	        cout << ans << '\n';
	    }
	}
	
```

```cpp
//方法二：

#include<stdio.h>

@(Codeforce)

#include<algorithm>
using namespace std;
 
 
int main()
{
    int T;
    scanf("%d",&T);
    while(T--)
    {
        int a,b,c;
        scanf("%d%d%d",&a,&b,&c);
        int ans=0;
        ans+=min(b,c/2);
        b-=ans;         //这里可以不用去管c了，省一些步骤；
        ans+=min(a,b/2);//包括这里，也不用去管理 a 和 b 的更新，省一些步骤；
        printf("%d\n",ans*3);
    }
}
```

```cpp

//自己写的还是不如上面的精简：

//codeforce 593 A
//2019/10/18

#include <bits/stdc++.h>
#include<algorithm>

using namespace std;

int main()
{
	int t,a,b,c;
	cin>>t;
	
	
	
	while(t--)
	{
		int total = 0;
		cin>>a>>b>>c;
		
		int tem;
		if(b>0 && c>1)
		{
			tem = min(b,c/2);
			
			b -= tem;
			c -= 2*tem;
			
			tem *= 3;
			total += tem;
		}
		if(a>0 && b>1)
		{
			tem = min(a,b/2);
			a -= tem;
			b -= 2*tem;
			tem *= 3;
			total += tem;
		}
		cout<<total<<endl;
	}
	
} 
```



