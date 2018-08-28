>create by jzf@2018/08/28
## 268. 缺失数字@2018/08/28
```c++
static const auto _ = []()
{
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return nullptr;
}();

class Solution {
public:
    int missingNumber(vector<int>& nums) {
        size_t n =nums.size();
        long long sum =(n*(n+1))/2;
        for(auto i:nums)
        {
            sum-=i;
        }
        return sum;
    }
};
```