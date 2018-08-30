>create by jzf@2018/08/29
## 121. 买卖股票的最佳时机@2018/08/29
```c++
class Solution {
public:
    int maxProfit(vector<int> &prices) {
        int max =0;
        for(size_t i = 0;i < prices.size();i++)
        {
            if(i==0)
            {
                continue;
            }
            
            for(size_t j =0; j<i ;j++)
            {
                int c=prices[i]-prices[j];
                if(c>max)
                {
                    max=c;
                }
            }
        }
        return max;
    }
};
```