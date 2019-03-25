>create by jzf@2019/03/25
## 27.移除元素@2019/03/25

```c++
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        if(nums.size() == 0)
        {
            return 0;
        }
        
        size_t begin = 0;
        size_t end = nums.size()-1;
        size_t half = begin+(end-begin)/2;
        while(half!=end)
        {
            if(half == begin)
            {
                if(nums[half]>=target)
                {
                    return half;
                }
                else
                {
                    half++;
                    break;
                }
            }
            if(nums[half] == target)
            {
                return half;
            }
            else if(nums[half] > target)
            {
                end = half -1;
                half = begin+(end-begin)/2;
            }
            else
            {
                begin = half+1;
                half = begin+(end-begin)/2;
                
            }
        }
        return nums[half]>=target?half:half+1;
    }
};

```
### 总结
我还是那么的菜，人家老北河秒写出来暴力，10分钟搞定二分法。
而我一开始就在写二分法，写了3个小时，愣是一堆bug

梳理下自己的思路
1，首先是觉得可以找出一个通用的二分递归函数，然后一层层调用就行了，一番操作似乎不给力，放弃之。

方案2，
在pad上手写从 0-5的二分查找
一开始觉得是3之后的二分都是一个步骤
之后又觉得2也是二分
然后就进入了书写代码的过程

在0 - 2 附近犯了许多的错误，直到最后也没能完全理清，全靠跑测试修改，爪爪

