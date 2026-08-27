# Solution 2 ⭐

[← 回到 L117: Populating Next Right Pointers in Each Node II](README.md)

主要是透過遍歷上一層的連接資訊，去判斷下一層依序要連接哪些點，等於說上一層就可以記住下一層要連接哪些點的資訊，因此不用額外的queue去記。

`Time: O(n)`

`Space: O(1)`

```cpp
class Solution {
public:
    Node* connect(Node* root) {
        
        Node* cur = root;

        // 一層一層處理
        while (cur != nullptr) {

            // dummy 是下一層的假頭節點
            Node dummy(0);
            Node* tail = &dummy;

            // 走目前這一層
            while (cur != nullptr) {

                // 有 left child 就接到下一層
                if (cur->left != nullptr) {
                    tail->next = cur->left;
                    tail = tail->next;
                }

                // 有 right child 就接到下一層
                if (cur->right != nullptr) {
                    tail->next = cur->right;
                    tail = tail->next;
                }

                // 沿著目前這一層往右走
                cur = cur->next;
            }

            // dummy.next 就是下一層第一個節點
            cur = dummy.next;
        }

        return root;
    }
};
```
