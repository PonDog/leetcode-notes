# Solution 1

[← 回到 L141: Linked List Cycle](README.md)

`Time: O(n)`

`Space: O(n)`

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
