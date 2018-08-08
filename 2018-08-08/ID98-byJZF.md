>create by jzf@2018/08/08
## 98.验证二叉搜索树@2018/08/08
### jzf
* 第一版
```c++
class Solution {
public:
     struct checkdata
        {
            TreeNode * node;
             long long max;
             long long min;
        };
        
    bool checkNode(TreeNode* node,long long max,long long min)
    {
         if(node->val >min &&node->val <max)
        {
                return true;
        }
        else
        {
                return false;
        }
        return true;
   }
    bool fun(checkdata data,vector<checkdata> &vecdata)
    {
        TreeNode* node=data.node;
        long long max =data.max;
        long long min =data.min;
        if(node->left!=NULL)
        {
           bool ret= checkNode(node->left,node->val,min);
            if(!ret)
            {
               return false; 
            }
            else
            {
                 checkdata tmp;
                 tmp.node =node->left;
                 tmp.max=node->val;
                 tmp.min =min;
                vecdata.push_back(tmp);
            }
        }
        if(node->right!=NULL)
        {
             bool ret= checkNode(node->right,max,node->val);
            if(!ret)
            {
               return false; 
            }
            else
            {
                 checkdata tmp;
                 tmp.node =node->right;
                 tmp.max=max;
                 tmp.min =node->val;
                vecdata.push_back(tmp);
            }
        }
        return true;
    }
   
    bool isValidBST(TreeNode* root) {
        if(root ==NULL) return true;
        vector<checkdata> vec;
        checkdata tmp;
        tmp.node =root;
        tmp.max=INT_MAX+1ll;
        tmp.min =INT_MIN-1ll;
        vec.push_back(tmp);
        while(!vec.empty())
        {
             vector<checkdata> vecdata;
            for(size_t i=0;i<vec.size();i++)
            {
                if(!fun(vec[i],vecdata))
                {
                    return false;
                }
            }
            vec =vecdata;
        }
        return true;
    }
};
```
### 优解
```c++
class Solution {
public:
    bool isValidBST(TreeNode* root, long mn = LONG_MIN, long mx = LONG_MAX) {
        if (!root) return true;
        if (root->val >= mx || root->val <= mn) return false;
        return isValidBST(root->left, mn, root->val) && isValidBST(root->right, root->val, mx);
    }
};
```
### 总结
1, 边界问题
    最近遇到了不少的边界问题，各种数值的极限形式。
    本次需要注意的一点，
```c++
    //max和min是long long
    //如果你不加字面量的修饰，他会默认为int，这就很慌。
    tmp.max=INT_MAX+1ll;
    tmp.min =INT_MIN-1ll;
```