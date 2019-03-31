>create by jzf@2019/03/30
## 101. 对称二叉树
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
    bool isSymmetric(TreeNode* root) {
        return func(root);
    }
    bool func(TreeNode* root){
        std::deque<TreeNode *>  dnode;
        dnode.push_back(root);
        while(!dnode.empty())
        {
            std::deque<TreeNode*>   tmpnode;
            
            dnode.swap(tmpnode);
            std::size_t len = tmpnode.size();
            for(std::size_t i = 0; i < len/2; i++)
            {
                if(!tmpnode[i] && !tmpnode[len-1-i]) continue;
                
                if(tmpnode[i] && tmpnode[len-1-i])
                {
                    
                  if(tmpnode[i]->val == tmpnode[len-1-i]->val)   
                  {
                      continue;
                  }
                    
                }
                 return false;
            }
            for(std::size_t i = 0; i < len; i++)
            {
                if(tmpnode[i]!=NULL)
                {
                    dnode.push_back(tmpnode[i]->left);
                    dnode.push_back(tmpnode[i]->right);
                }
            }
        }
        return true;
    }
};
```