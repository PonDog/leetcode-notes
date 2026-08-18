# Solution 1 ⭐

[← 回到 L2: Add Two Numbers](README.md)

一開始先建一個dummy的原因是希望可以不要每次都要判斷當前Linked List有無節點，兩種後續需要的串接流程不同，有dummy就可以統一當成有節點的情況。

`Time: O(max(l1長度,l2長度))`

`Space: O(max(l1長度,l2長度))`

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        int carry = 0;
        ListNode* dummy = new ListNode();
        ListNode* current = dummy;
        while(l1 != nullptr || l2 != nullptr || carry == 1){
            int num1 = l1 != nullptr? l1 -> val : 0;
            int num2 = l2 != nullptr? l2 -> val : 0;
            int sum = num1 + num2 + carry;
            carry = sum / 10;
            current -> next = new ListNode(sum % 10);
            current = current -> next;
            if(l1 != nullptr) l1 = l1 -> next;
            if(l2 != nullptr) l2 = l2 -> next;  
        }
        return dummy -> next;
    }
};
```

</details>
