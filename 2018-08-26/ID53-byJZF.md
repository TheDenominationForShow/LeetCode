>create by jzf@2018/08/26
## 53. 最大子序和@2018/08/08
### jzf
* 第一版
```c++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        vector<int> vec(nums.size(),0);
        for(size_t i=0;i<nums.size();i++)
        {
            if(i==0)
            {
                vec[i]=nums[0];
            }
            if(i>0)
            {
                if(vec[i-1]<0)
                {
                    vec[i] =nums[i];
                }
                else
                {
                    vec[i] = (vec[i-1]+nums[i])<0?nums[i]:(vec[i-1]+nums[i]);
                }
            }
        }
        sort(vec.begin(),vec.end());
        return vec[nums.size()-1];
    }
};
```
### 优解
```C++
static const auto _ = []()
{
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return nullptr;
}();

class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int maxsum = INT_MIN, sum=0;
        if(nums.size()==1)return nums[0];
        for(int i = 0;i<nums.size();i++){
            sum+=nums[i];
            if(sum>maxsum){
                maxsum=sum;
            }
            if(sum<0){
                sum=0;
            } 
        }
        return maxsum;
    }
};
```
### 总结
* 1 ，状态很影响做题。
    昨天状态不好，做题的水平不给力，这么简单的今天才做出来
* 2， 重新整理动态的一些感受。
    * 减少重复运算
    * 对数据的直观表达真的很重要
        一个列表啪啪啪，瞬间总结出规律
        一个树形图啪啪，瞬间明白步骤。
        美滴很美滴很。