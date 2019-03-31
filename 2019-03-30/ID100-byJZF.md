>create by jzf@2019/03/30
## 100. 相同的树
```c++  
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
         std::vector<TreeNode *> vctree1;
         std::vector<TreeNode *> vctree2;
         func(p,vctree1);
         func(q,vctree2);
         
        if(vctree1.size() != vctree2.size()) return false;
        
        for(size_t i = 0; i < vctree1.size(); i++)
        {
            if(!vctree1[i] && !vctree2[i]) continue;
            
            if(vctree1[i] && vctree2[i])
            {
                if(vctree1[i]->val == vctree2[i]->val)
                {
                    continue;
                }
            }
            return false;
        }
        
         return true;
        
    }
    void func(TreeNode * root,std::vector<TreeNode *>& vctree)
    {
        std::stack<TreeNode *> snode;
        snode.push(root);
        while(!snode.empty())
        {
            TreeNode *p = snode.top();
            snode.pop();
            vctree.push_back(p);
            if(p == NULL)
            {
                continue;
            }
            snode.push(p->left);
            snode.push(p->right);
        }
        
    }
};
```
### 另一种写法
```c++
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
    
        if (p==NULL && q==NULL) return true;
        if (p==NULL || q==NULL) return false;
        if (p->val!=q->val) return false;
        
        return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
};
```
### 总结