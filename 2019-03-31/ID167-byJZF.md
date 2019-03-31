>create by jzf@2019/03/31
## 167. 两数之和 II - 输入有序数组
```c++  
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        for(std::size_t i = 0; i < numbers.size(); i++)
        {
            int tmp = target - numbers[i];
            
            if(i!= 0 && numbers[i] == numbers[i-1]) continue;
            for(std::size_t j = i+1; j <numbers.size();j++)
            {
                if(numbers[j] == tmp)
                {
                    return vector<int>{i+1,j+1};
                }
                if(numbers[j] > tmp) break;
            }
        }
        return vector<int>{1,2};
    }
};
```
### 优解
```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        vector<int> res;
        int i = 0, j = numbers.size() - 1;
        while(i < j){
            if (numbers[i] + numbers[j] == target) {
                res.push_back(i + 1);
                res.push_back(j + 1);
                return res;
            } else if (numbers[i] + numbers[j] < target) {
                i++;
            } else {
                j--;
            }
        }

        return res;
    }
};
```
### 总结
还能说啥，学习了