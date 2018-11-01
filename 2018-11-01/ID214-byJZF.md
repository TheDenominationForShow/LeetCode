>create by jzf@2018/11/01
## 214. 最短回文串@2018/11/01

```c++
class Solution {
public:
    string shortestPalindrome(string s) {
        
        size_t num = s.size();
        size_t half = (num+1)>>1;
        string retStr;
        
        for(;num >0;num--)
        {
            bool flag =true;
            size_t i = 0;
            for(; i < (num>>1); i++)
            {
                if(s[num-i-1]!=s[i])
                {
                    flag =false;
                    break;
                }
            }
            
            if(flag == true)
            {
                for(size_t j =s.size();j>num;j--)
                {
                    retStr+= s[j-1];
                }
                retStr+=s;
                return retStr;
            }
        }    
        return retStr;
    }
};
```