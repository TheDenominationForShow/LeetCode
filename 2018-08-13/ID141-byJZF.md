>create by jzf@2018/08/13
## 141. 环形链表@2018/08/13
### jzf
* 第一版
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
    //node->next!=NULL node->next!=node
    bool isCyclenode(ListNode *node,ListNode *head)
    {
        while (head!=node)
        {
            if(node->next==head)
            {
                return true;
            }
            head=head->next;
        }
        return false; 
    }
    bool hasCycle(ListNode *head) {
        ListNode  *node =head;
        ListNode  *tmp =head;
        if(head==NULL) return false;
        while(node->next!=NULL)
        {
            if(node->next==node)
            {
                return true;
            }
            if(isCyclenode(node,head))
            {
                return true;
            }
            node=node->next;
        }
        return false;
        
    }
};

```
### 优解
```c++
class Solution {
public:
    bool hasCycle(ListNode *head) {
        //如果空或者单
        if (head == nullptr || head->next == nullptr) {
            return false;
        }

        ListNode *p = head;
        ListNode *q = head->next;
        
        //
        while (q && q != p && q->next != nullptr) {
            p = p->next;
            q = q->next->next;
        }
        if (q == p) {
            return true;
        }
        return false;
    }
};
```
### 总结
1，我的解法是暴力的，不过很好贯彻了我的那个分步骤的想法。
2，优解的那个，一时间没想明白，北河说一个走一步一个走两步，是环总会碰到
  但是如何想到这一步，以及如何估算他的复杂度呢
  暴力复杂度 n2
  追击问题，复杂度n
 > https://www.jianshu.com/p/ef71e04241e4