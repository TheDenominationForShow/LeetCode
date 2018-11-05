>create by jzf@2018/11/05
## 104. 二叉树的最大深度@2018/11/05

```c++
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root == nullptr)
        {
            return 0;
        }
        return 1+max(maxDepth(root->left),maxDepth(root->right));
    }
};
```
### 总结
1，我觉得有必要自己做一个堆栈来处理呀，依靠编译器递归，容易溢出
