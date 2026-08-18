# Solution 2 ⭐

[← 回到 L61: Rotate List](README.md)

推薦的解法，把尾巴連到頭，再從頭找新尾巴，然後切斷。

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        if (!head || !head->next) return head;

        int count = 1;
        ListNode* tail = head;

        while (tail->next) {
            tail = tail->next;
            count++;
        }

        k %= count;
        if (k == 0) return head;

        tail->next = head;

        ListNode* newTail = head;
        for (int i = 0; i < count - k - 1; i++) {
            newTail = newTail->next;
        }

        ListNode* newHead = newTail->next;
        newTail->next = nullptr;

        return newHead;
    }
};
```

</details>
