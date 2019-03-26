>create by jzf@2019/03/26
## 58. 最后一个单词的长度@2019/03/26
```c++
class Solution {
public:
    int lengthOfLastWord(string s) {
        if(s.empty())
        {
            return 0;
        }
    
        size_t end = s.size()-1;
        while(end!=0 && s[end]==' ')
        {
            end--;
        }
        if(end == 0)
        {
            return s[0] == ' '?0:1;
        }
        size_t begin = end;
        while(begin!=0 && s[begin]!=' ')
        {
            begin--;
        }
        
        return s[begin] == ' '?(end - begin):(end - begin)+1;
    }
};
```
### 种子哥的stl版本
```c++
static auto xxx=[]{
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return nullptr;
}();
class Solution {
public:
   int lengthOfLastWord(string s) 
{
	return find_if(
            find_if(s.rbegin(), s.rend(), [](char word) {return !isspace(word); }) + 1,
             s.rend(), 
             [](char word) 
                {return isspace(word); }) 
                - find_if(
                    s.rbegin(), 
                    s.rend(), 
                    [](char word) {return !isspace(word); });
}
};
```
### 总结
1,果然早上适合做费力气的活动
2，这个吸收昨晚的经验，不去考虑任何花式的东西，按照1,2,3,4这样的步骤来先重现一波
   然后分析特殊的节点操作。
   虽然还是有一些需要靠测试发现的bug，但是速度上要快很多了
3，我需要在补充下stl的知识了，感觉脑子里边有一些个成型的数据结构和算法，对于解决问题实在是太有帮助了，
可以极大地提升解决问题的思路
