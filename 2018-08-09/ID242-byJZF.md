>create by jzf@2018/08/09
## 242. 有效的字母异位词@2018/08/09
### jzf
```c++
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.size()!=t.size())
        {
            return false;
        }
        sort(s.begin(),s.end());
        sort(t.begin(),t.end());
        for(size_t i=0;i<s.size();i++)
        {
            if(s[i]!=t[i])
            {
                return false;
            }
        }
        return true;
    }
};
```
###优解
```c++

static auto x = []() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    bool isAnagram(string s, string t) {
                int ret = 0;
        // int s_sum = 0;
        // int t_sum = 0;
        int s_times = 1;
        int t_times = 1;

        for (int i = 0; i < s.length(); i++)
        {
            int c = int(s[i]);
            ret ^= c;
            // s_sum += c;
            s_times *= c;
        }

        for (int i = 0; i < t.length(); i++)
        {
            int c = int(t[i]);
            ret ^= c;
            // t_sum += c;
            t_times *= c;
        }
        // return ret == 0 && s_sum == t_sum && s_times == t_times;
        return ret == 0 && s_times == t_times;
    }
};
```