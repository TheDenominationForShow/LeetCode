>create by jzf@2019/05/11
## 32. 最长有效括号
### 未通过代码

```c++
#include <stack>
class Solution {
public:
    int longestValidParentheses(string s) {
        if(s.empty()) return 0;
        
        std::stack<int> stack0;
        std::size_t i = 0;
        int max = 0;
        int count = 0;
        int pre = 0;
        int preCount = 0;
        while(i < s.size())
        {
            if(s[i] == '(') 
            {
                stack0.push(i);
                i++;
                continue;
            }
            if(s[i] == ')')
            {
                if(!stack0.empty())
                {
                    int tmp = stack0.top();
                    stack0.pop();
                    count++;
                    if(stack0.empty())
                    {
                        if(pre+1 == tmp)
                        {
                             count += preCount;
                        }
                        pre = i;
                        preCount = count;
                        if(count > max)
                        {
                            max = count;
                        }
                        std::stack<int> tmp;
                        stack0.swap(tmp);
                        count = 0;
                    }
                }
                else
                {
                    if(count > max)
                    {
                        max = count;
                    }
                    std::stack<int> tmp;
                    stack0.swap(tmp);
                    count = 0;
                }

            }
            i++;
        }
        if(count > max)
        {
            max = count;
        }
        return 2*max;
    }
};
```


## 总结
这次还是依照之前的方式

从 1 2 3这样先看看样例分布
但是由于是指数级的，我列举到4就玩不下去了
只是想到用栈进行配对

代码的思路很简单，遇到 `)` 就进行闭合，计数，如果`)`无法闭合，那么就是下一轮
然后发现无法通过 `((()((()` 这种样例

之后想解决，但是没有成功

后来看了下群里大佬发的代码，理解了


在此反思自己的问题，
>eummm 先睡了，明天再说吧
