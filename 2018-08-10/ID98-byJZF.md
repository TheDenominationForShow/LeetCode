>create by jzf@2018/08/10
## 237. 删除链表中的节点@2018/08/10
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
    void deleteNode(ListNode* node) {
        ListNode * nextNode =node->next;
        node->val=nextNode->val;
        node->next=nextNode->next;
        return;
    }
};
```

### 总结
1，删除节点不一定是真的删除他的存储，换一换值也可以呀
