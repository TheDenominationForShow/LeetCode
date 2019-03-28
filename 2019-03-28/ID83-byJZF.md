
>create by jzf@2019/03/28
## 83. 删除排序链表中的重复元素
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
        ListNode* curP1 = head;
        if(curP1 == NULL) return head;
        
        while(curP1->next != NULL)
        {
            ListNode* curP2 = curP1->next;
            ListNode* curP3 = curP1;
            while(curP2->next != NULL)
            {
                if(curP2->val == curP1->val)
                {   
                    ListNode* tmp = curP2->next;
                    curP2->val = tmp->val;
                    curP2->next = tmp->next;
                    delete tmp;
                    continue;
                }
                curP2 = curP2->next;
                curP3 = curP2;
            }
            if(curP2 == curP1)
            {
                break;
            }
            else if(curP2->val == curP1->val)
            {
                curP3->next = NULL;
                delete curP2;
            }
            
            if(curP1->next==NULL) break;
            else curP1 = curP1->next;
        }
        return head;
    }
};
```
### 优解
```c++
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if (!head || !head->next)
            return head;
        
        ListNode * phead = head;
        
        while (phead->next)
        {
            if (phead->val == phead->next->val)
            {
                phead->next = phead->next->next;
            }
            else
                phead = phead->next;
        }
        
        return head;
    }
};
```
### 总结
1，可能是有点发烧，我没注意到是已经排序好的链表，按照没排序的来做的
2，总结两个有效的处理问题方式，
    1) 从少到多，1 ， 2， 3， 4,5
    2）动手测试