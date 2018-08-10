>create by jzf@2018/08/10
## 21. 合并两个有序链表@2018/08/10
### jzf
* 第一版
```c++
static auto x = []() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        
        ListNode * retnode=new ListNode(0);
        ListNode * node =retnode;
        while(l1!=NULL||l2!=NULL)
        {
            if(l1!=NULL&&l2!=NULL)
            {
                if(l1->val<l2->val)
                {
                    node->next=l1;
                    l1=l1->next;
                }
                else
                {
                    node->next=l2;  
                    l2=l2->next;
                }
                node =node->next;
            }
            else if(l1==NULL)
            {
                node->next=l2;  
                l2=l2->next;
                node =node->next;
            }
            else
            {
                node->next=l1;
                l1=l1->next;
                node =node->next;
            }
        }
        return retnode->next;
    }
};
```