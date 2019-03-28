>create by jzf@2019/03/28
## 82. 删除排序链表中的重复元素 II
```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if(!head|| !head->next) return head;
        ListNode* p1 = head;
        head = NULL;
        ListNode* p3 = NULL;
        
        
        while(p1 != NULL)
        {
            ListNode* p2 = p1->next;
            while(p2 != NULL)
            {
                if(p2->val != p1->val){
                   break;
                }
                 p2 = p2->next;
            }
            //
            if(p2 == p1->next){
                if(p3 == NULL)
                {
                    p3 = p1;
                    head = p1;
                }
                else
                {
                    p3->next = p1; 
                    p3 = p1;
                    
                }
                p3->next = NULL;
            }
            p1 = p2;
        }

        return head;
    }
};
```
### 总结

就目前而言，那种顺序分析的方法十分的好用