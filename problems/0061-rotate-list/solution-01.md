# Solution 1

[← 回到 L61: Rotate List](README.md)

雙指標法，踩到的坑是當k%count為0的case，slow和fast最後會重疊，因此需要額外判斷。
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
    ListNode* rotateRight(ListNode* head, int k) {
        ListNode dummy(0,head);
        ListNode* current = &dummy;
        int count = 0;
        while(current->next){
            count++;
            current = current->next;
        }
        if(count == 0) return dummy.next;
        k %= count;
        if (k == 0) return dummy.next;
        ListNode* slow = &dummy;
        ListNode* fast = &dummy;
        for(int i = 1; i <= k; i++){
            fast = fast->next;
        }
        while(fast->next){
            slow = slow->next;
            fast = fast->next;
        }
        dummy.next = slow->next;
        slow->next = fast->next;
        fast->next = head;
        return dummy.next;
    }
};
```

</details>
