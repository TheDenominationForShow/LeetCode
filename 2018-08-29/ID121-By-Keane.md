>create by jzf@2018/08/29 北河大傻逼
## 121. 买卖股票的最佳时机@2018/08/29
```c++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if (prices.empty()) {
            return 0;
        }        
        int max_num = 0;
        vector<int> v(prices.size());
        adjacent_difference(prices.begin(), prices.end(), v.begin());
        v[0] = 0;
        vector<int>::iterator it = find_if(v.begin(), v.end(), [](auto &x) { return x > 0; });
        if (it == v.end()) {
            return 0;
        }
        int total = 0;
        while (it != v.end()) {    
            for (; it != v.end(); ++it) {
                total += *it;
                if (total > max_num) { 
                    max_num = total;
                }
                if (total <= 0) {
                    total = 0;
                }
            }
        }
        return max_num;
    }
}
```