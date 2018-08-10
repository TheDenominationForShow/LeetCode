>create by jzf@2018/08/10
## 19. 删除链表的倒数第N个节点@2018/08/10
### jzf
* 第一版
```c++
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode * EndNode=head;
        ListNode * Node=head;
        ListNode * Node2=head;
        long count =1;
        if(head==NULL){return head;}
        if(head->next==NULL){return NULL;}
        while(EndNode!=NULL)
        {
            
            EndNode=EndNode->next;
            
            if(count>n)
            {
                Node2=Node;
                Node=Node->next;
            }   
            else
            {
                
            }
            count++;
            
        }
        if(Node->next!=NULL)
        {
            Node->val =Node->next->val;
            Node->next=Node->next->next;
        }
        else
        {
            Node2->next=Node->next;
        }
      
        return head;
    }
};
```
### 总结
1，没有注释的代码是耍流氓
2，要体现一定的步骤和模块性