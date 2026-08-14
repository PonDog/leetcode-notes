# Solution 1 ⭐

[← 回到 L82: Remove Duplicates from Sorted List II](README.md)

`Time:O(n)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode dummy(0,head);
        ListNode* current = head; 
        ListNode* before = &dummy;
        while(current){
            if(current->next && current->val == current->next->val){
                while(current->next && current->val == current->next->val){
                    current = current->next;
                }
                current = current->next; //這裡因為會停在最後一個重覆節點，所以再跳一次。
                before->next = current;  
            }
            else{
                before = before->next;
                current = current->next;
            }
        }
        return dummy.next;
    }
};
```

</details>
