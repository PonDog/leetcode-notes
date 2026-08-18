# Solution 1 ⭐

[← 回到 L86: Partition List](README.md)

分成左半和右半兩個Link List，最後再合併。

`Time: O(n)`

`Space: O(1)`

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
    ListNode* partition(ListNode* head, int x) {
        ListNode small_dummy;
        ListNode* small_tail = &small_dummy;
        ListNode large_dummy;
        ListNode* large_tail = &large_dummy;
        ListNode* current = head;
        while(current){
            if(current->val < x){
                small_tail->next = current;
                small_tail = small_tail->next;
            }
            else{
                large_tail->next = current;
                large_tail = large_tail->next;
            }
            current = current->next; 
        }
        small_tail->next = large_dummy.next;
        large_tail->next = nullptr;
        return small_dummy.next;
    }
};
```

</details>
