# Solution 1 ⭐

[← 回到 L92: Reverse Linked List II](README.md)

before:反轉區間前一個節點

current:尚未反轉的第一個節點（反轉結束後就是區間後面的節點）

previous:已經反轉好的串列頭（反轉完成後就是新的區間開頭）

tail:原本反轉區間第一個節點，反轉完成後變成尾巴

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

    ListNode* reverseBetween(ListNode* head, int left, int right) {

        ListNode* dummy = new ListNode();

        dummy->next = head;

        // before 指向反轉區間前一個節點

        ListNode* before = dummy;

        for (int i = 1; i < left; i++) {

            before = before->next;

        }

        // current 是反轉區間的第一個節點

        ListNode* current = before->next;

        ListNode* previous = nullptr;

        // 反轉 left 到 right，共 right - left + 1 個節點

        for (int i = 0; i < right - left + 1; i++) {

            ListNode* nextNode = current->next;

            current->next = previous;

            previous = current;

            current = nextNode;

        }

        // before->next 原本是反轉區間的第一個節點

        // 反轉後會變成區間最後一個節點

        ListNode* tail = before->next;

        // 區間尾巴連接後半段

        tail->next = current;

        // 區間前半段連接反轉後的新頭

        before->next = previous;

        ListNode* result = dummy->next;
        delete dummy;
        return result;
    }
};
```

</details>
