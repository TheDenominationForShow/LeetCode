>create by jzf@2018/08/09
## 125. 验证回文串@2018/08/09
### jzf
```c++
class Solution {
public:
    bool isPalindrome(string s) {
    
        vector<char> vecChr;
        for(size_t i=0;i<s.size();i++)
        {
            if(isalpha(s[i]))
            {
                vecChr.push_back(tolower(s[i]));
            }
             if(isdigit(s[i]))
            {
                vecChr.push_back(s[i]);
            }
        }
        if(0==vecChr.size())
        {
            return true;
        }
        size_t n=vecChr.size();
        for(size_t i=0;i<vecChr.size()/2;i++)
        {
            
            if(n>2*i+1 &&vecChr[i]==vecChr[n-i-1])
            {
                
            }
            else
            {
                return false;
            }
            
        }
        return true;
    }
};
```