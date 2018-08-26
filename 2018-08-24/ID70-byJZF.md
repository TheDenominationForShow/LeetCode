>create by jzf@2018/08/26
## 70. 爬楼梯@2018/08/24
### jzf
* 第一版
```c++
static auto XXX = [] {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return nullptr;
}();
class Solution {
public:
    int climbStairs(int n) {
        int v[n+1]={0};
        for (int i = 1; i <= n; ++i) {
            if (i <= 2) {
                v[i] = i;
                continue;
            }
            v[i] = v[i - 1] + v[ i - 2];
        }
        return v[n];
    }
};
```
### 总结
1，完全是抄的北河的
2，这道题刺激蛮大的，我又重新疏理了动态规划。
我在做类似最长公共子序列的问题上，产生了惯性思维。觉得动态规划，
先要列个表，然后n会用到n-1的结果之类。
实际上片面了。