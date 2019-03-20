>create by jzf@2019/03/20
## 27.移除元素@2019/03/20

```c++
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        auto iter = nums.begin();
        while(iter != nums.end())
        {
            if(*iter == val)
            {
                iter = nums.erase(iter);
            }
            else
            {
                iter++;
            }
        }
        return nums.size();
    }
};
```
```python
class Solution:
    def removeElement(self, nums, val) -> int:
        if len(nums) == 0:
            return 0
        start = 0
        end = len(nums) -1
        while start < end:
            if nums[start]  == val:
                while nums[end] == val and end > start:
                    end -= 1
                    #print(end)
                nums[start] = nums[end]
                if end <= start+1:
                    break
                end -= 1
            start += 1
            #print(start)   
        if nums[start] == val :
            return start
        else:
            return start + 1
```
### 优解
```python
class Solution:
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        if len(nums)==0:
            return 0
        
        pointer = 0
        for i in range(len(nums)):
            if nums[i] == val:
                continue
            nums[pointer] = nums[i]
            pointer += 1
        return pointer
```
### 总结
我最开始的反应就是之前遇到的 erase 事件，所以直接stl erase
之后打算写python 然后他的函数注解把我难住了，这啥语法啊，没见过，然后看了下python
其中list的删除某个位置元素用pop我没注意到，事实证明我多菜

之后我想到了暴力删除和交换
但是看到别人写的，我觉得差距还是贼大的
对方的代码体现思路的清晰度和代码整洁性太牛逼了。

我思考了下，我的代码思路和最优解的思路

首先，我的想法是 脑子中有个移动箱子的动画
然后把他实现出来

实际上整个过程无非是 比较和移动

我的代码应该比最优解差在比较上

1，在大脑的模拟中，忽略了一些比较过程
2，再一个就是空间复杂度o1的提示，可能令人规避了最优解的方式，毕竟最优解有点新建一个数组的感觉

