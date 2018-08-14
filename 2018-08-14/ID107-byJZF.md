>create by jzf@2018/08/14
## 107. 二叉树的层次遍历@2018/08/08
### jzf
* 第一版
```c++
class Solution {
public:
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        vector<vector<int>> retvec;
        vector<int> vec;
        vector<TreeNode*> vectmp;
        if(root ==nullptr)
        {
            return retvec;
        }
        else
        {
            vectmp.push_back(root);
            vec.push_back(root->val);
            retvec.push_back(vec);
            vec.clear();
        }
        
        while(vectmp.size()!=0)
        {
            vector<TreeNode*> vectmp1;
            for(size_t i=0;i<vectmp.size();i++)
            {
                if(vectmp[i]->left)
                {
                    vectmp1.push_back(vectmp[i]->left);
                    vec.push_back(vectmp[i]->left->val);
                    
                }
                if(vectmp[i]->right)
                {
                    vectmp1.push_back(vectmp[i]->right);
                    vec.push_back(vectmp[i]->right->val);
                }
            }
            if(vec.size()!=0)
            {
                retvec.push_back(vec);
                vec.clear();
            }
            
            vectmp =vectmp1;
        }
        reverse(retvec.begin(),retvec.end());
        return retvec;
    }
};
```