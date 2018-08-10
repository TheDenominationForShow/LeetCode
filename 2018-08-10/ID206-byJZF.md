>create by jzf@2018/08/10
## 206. 反转链表@2018/08/10
### jzf
* 第一版
```c++
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode *node =head;
        ListNode *pret =NULL;
        while (node!=NULL){
        
        ListNode *tmp =node;
        node=node->next;
        tmp->next=pret;
        pret =tmp;
        }
   
        return pret;
    }
};
```