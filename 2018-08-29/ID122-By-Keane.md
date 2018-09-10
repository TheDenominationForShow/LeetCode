>create by jzf@2018/08/29 北河大傻逼
## 122. 买卖股票的最佳时机@2018/08/29
```c++
static auto XXX = [] {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return nullptr;
}();
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if (prices.empty()) {
            return  0;
        }
        adjacent_difference(prices.begin(), prices.end(), prices.begin());
        prices[0] = 0;
        return accumulate(prices.begin(), remove_if(prices.begin(), prices.end(), [](auto &x) { return x <= 0; }), 0);
    }
};
```