[toc]

# Atcoder library

### Floor sum

#### 1.$\sum_{i=0}^{ai+b}\lfloor \frac{ai+b}{m} \rfloor$

复杂度 $O(lg(n+m+a+b))$ 

```cpp
long long floor_sum(long long n, long long m, long long a, long long b) {
    long long ans = 0;
    if (a >= m) {
        ans += (n - 1) * n * (a / m) / 2;
        a %= m;
    }
    if (b >= m) {
        ans += n * (b / m);
        b %= m;
    }

    long long y_max = (a * n + b) / m, x_max = (y_max * m - b);
    if (y_max == 0) return ans;
    ans += (n - (x_max + a - 1) / a) * y_max;
    ans += floor_sum(y_max, a, m, (a - x_max % a) % a);
    return ans;
}
```

来源、证明：https://zhuanlan.zhihu.com/p/343777907

#### 2.$\sum_{i=1}^{N}\lfloor\frac Ni\rfloor$

复杂度$O(\sqrt N)$

```c++
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
int main()
{
	ll n, ans = 0;
	cin >> n;
	for (ll l = 1, r; l <= n; l = r + 1)
	{
		r = n / (n / l);
		ans += (r - l + 1) * (n / l);
	}
	cout << ans << endl;
	return 0;
}

```

来源、证明：https://blog.csdn.net/weixin_51159301/article/details/122499274

(原网页的"[]"是下取整)