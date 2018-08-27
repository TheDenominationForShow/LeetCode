>create by jzf@2018/08/27
## 412. Fizz Buzz@2018/08/27
### jzf
* 第一版
```c++
class Solution {
public:
    vector<string> fizzBuzz(int n) {
        vector<string>  vecStr;
        for(int i=1;i<=n;i++)
        {
            if(i<3)
            {
                vecStr.push_back(to_string(i));
            }
            else
            {
                string str;
                if(i%3==0  &&i%5==0)
                {
                vecStr.push_back("FizzBuzz");
                }
                else if(i%3==0)
                {
                     vecStr.push_back("Fizz");
                }
                else if(i%5==0)
                {
                     vecStr.push_back("Buzz");
                }
                else
                {
                     vecStr.push_back(to_string(i));
                }
            }
        }
        return vecStr;
    }
};
```