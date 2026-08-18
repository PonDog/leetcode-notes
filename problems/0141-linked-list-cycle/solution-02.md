# Solution 2 ⭐

[← 回到 L141: Linked List Cycle](README.md)

想法是一個一次走一步，另一個一次走兩步，如有cycle，走兩步的會追上走一步的。

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
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        unordered_set<ListNode*> seen;
        while(head != nullptr){
            if(seen.count(head)){
                return true;
            }
            else{
                seen.insert(head);
                head = head->next;
            }
        }
        return false;
    }
};
```

</details>
