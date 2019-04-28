>create by jzf@2019/04/28
## 343. 整数拆分
```c++  
class Solution {
public:
    int integerBreak(int n) {
        if(n == 2) return 1;
        if(n == 3) return 2;
        if(n == 4) return 4;
        int ret = 1;
        if(n%3 == 0)
        {
            for(int i = 0; i < n/3; i++)
            {
                ret *= 3;
            }
        }
        else if(n%3 == 1)
        {
            for(int i = 0; i < n/3-1; i++)
            {
                ret *= 3;
            }
            ret *= 4;
        }
        else
        {
            for(int i = 0; i < n/3; i++)
            {
                ret *= 3;
            }
            ret *= 2;
        }
        return ret;
    }
};
```

## 其他解

```
// 动态规划做法: dp[i] 代表可拆分可不拆分的情况下 两者的最大值
class Solution {
    public int integerBreak(int n) {
        if(n <= 3) return n-1;
        int[] dp = new int[n+1];
        dp[1] = 1;
        dp[2] = 2;
        dp[3] = 3;
        for(int i = 4; i <= n; i++) {
        	int max = Integer.MIN_VALUE;
        	for(int j = 1; j < i; j++) {
        		max = Math.max(dp[j]*dp[i-j], max);
        	}
        	dp[i] = max;
        }
        return dp[n];
    }
}
```

## 总结

还是之前的做法

2，总结两个有效的处理问题方式，
    1) 从少到多，1 ， 2， 3， 4,5
    2）动手测试
