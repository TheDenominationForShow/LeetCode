>create by jzf@2019/05/11
## 238. 除自身以外数组的乘积
### 未通过代码
```c++
//超时
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> retVec(nums.size(),1);
        for(size_t i=0; i < nums.size(); i++)
        {
            for(size_t j=0; j < nums.size(); j++)
            {
                if(j != i)
                {
                    retVec[j] *= nums[i];
                }
            }
        }
        return retVec;
    }
};

//除0
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        
        int a = 1;
        for(auto iter = nums.begin(); iter != nums.end(); iter++)
        {
            a *= *iter;
        }
        
        vector<int> retVec(nums.size(),a);
        for(size_t i = 0; i < nums.size(); i++)
        {
            retVec[i] = retVec[i]/nums[i];
        }
        return retVec;
    }
};
```
### 优解
```c++

class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int product=1,cnt=0;
        for(int n:nums)
            if (n!=0) product*=n;
            else cnt++;
        for(int i=0;i<nums.size();i++)
            if (cnt==0)
                nums[i]=product/nums[i];
            else if(cnt==1)
                nums[i]=nums[i]==0?product:0;
            else 
                nums[i]=0;
        return nums;
    }
};

class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        
        int n=nums.size();
        int left=1,right=1;     //left：从左边累乘，right：从右边累乘
        vector<int> res(n,1);
        
        for(int i=0;i<n;++i)    //最终每个元素其左右乘积进行相乘得出结果
        {
            res[i]*=left;       //乘以其左边的乘积
            left*=nums[i];
            
            res[n-1-i]*=right;  //乘以其右边的乘积
            right*=nums[n-1-i];
        }
        
        return res;
        
    }
};

class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int nl = nums.size();
		vector<long> L(vector<long>(nl + 2, 1));
		vector<long> R(vector<long>(nl + 2, 1));

		for (int i = 0; i < nl; i++) {
			L[i + 1] = L[i] * nums[i];
			R[nl - i] = R[nl - i + 1] * nums[nl-i-1];
        }
		for (int i = 0; i < nl; i++) {
			nums[i] = L[i] * R[i + 2];
		}
		return nums;



    }
};
```
## 总结

以前那种枚举递归的方式无法解决问题了。
