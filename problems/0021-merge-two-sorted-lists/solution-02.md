# Solution 2

[← 回到 L21: Merge Two Sorted Lists](README.md)

遞迴法

`Time: O(max(l1長度,l2長度))`

`Space: O(max(l1長度,l2長度))`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {

        // Base Case
        if (l1 == nullptr)
            return l2;

        if (l2 == nullptr)
            return l1;

        // l1 比較小
        if (l1->val <= l2->val) {
            l1->next = mergeTwoLists(l1->next, l2);
            return l1;
        }

        // l2 比較小
        else {
            l2->next = mergeTwoLists(l1, l2->next);
            return l2;
        }
    }
};
```

</details>
