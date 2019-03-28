
>create by jzf@2019/03/28
## 69. x 的平方根
```c++
class Solution {
public:
    int mySqrt(int x) {
   	int n = 0;
	while (x > (1 << n))
	{
        if(n >= 31)
        {
            n = 32;
            break;
        }
		n++;
	}

	if (n == 0) return x;
	n = (n & 1 ? n + 1 : n) >> 1;
	int begin = 1 << (n - 1);
	int end =  (n==16)?46340:1<<n;
	//二分法查找

	while (end - begin > 1)
	{
		int half = (begin + end) / 2;
		if (half*half == x)
		{
			return half;
		}
		else if (half*half > x)
		{
			end = half;
		}
		else
		{
			begin = half;
		}
	}
	return ((end*end) <= x) ? end : begin;
    }
};
```
### 另一种解法
```c++
class Solution {
public:
    int mySqrt(int x) {
        if (x == 1 || x == 0) return x;
		unsigned v = x / 2;
		while (true)
		{
			unsigned v2 = x / v;
			if (v2 >= v) return v;
			v = (v + v2) >> 1;
		}
    }
};
```
### 总结
1，下午也很适合刷题
2，我的代码流程有点复杂，需要精炼下。二分法还得多谢谢
3，关于最优解，小白有说，附链接
>https://github.com/MoeMod/BigDecimal-Calculator.git
>百度介绍 https://www.cnblogs.com/Matrix_Yao/archive/2009/07/28/1532883.html

