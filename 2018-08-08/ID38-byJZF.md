>create by jzf@2018/08/08
## 38. 报数@2018/08/08
### jzf
* 第一版
```c++
class Solution {
public:
    string countAndSay(int n) {
        string retStr;
        if(n==1) 
        {
            retStr="1";
        }
        else
        {
            string strforword=countAndSay(n-1);
            char tmp =strforword[0];
            size_t cout=0;
            for(size_t i =0;i<strforword.size();i++)
            {
                if(tmp==strforword[i])
                {
                    cout++;
                }
                else
                {
                    retStr+=to_string(cout);
                    string str(1,tmp);
                    retStr+=str;
                    tmp =strforword[i];
                    cout =1;
                }
            }
            retStr+=to_string(cout);
            string str(1,tmp);
            retStr+=str;
        }
        return retStr;    
    }
};
```
