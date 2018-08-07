>create by jzf@2018/08/07
## 701. Insert into a Binary Search Tree@2018/08/07
### jzf
* 第一版
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

bool fun(TreeNode* inOut_node,TreeNode* InsertNode)
{
        if(InsertNode->val>inOut_node->val)
    {
        if(inOut_node->right==NULL)
        {
            inOut_node->right =InsertNode;
            return true;
        }
        else
        {
           return fun(inOut_node->right,InsertNode);
        }
    }
    else
    {
        if(inOut_node->left==NULL)
        {
            inOut_node->left =InsertNode;
            return true;
        }
        else
        {
            return  fun(inOut_node->left,InsertNode);
        }
    }
}
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        
        TreeNode* InsertNode =new TreeNode(val);
        TreeNode* node =root;
        fun(node,InsertNode);
        return root;
    }
};
```