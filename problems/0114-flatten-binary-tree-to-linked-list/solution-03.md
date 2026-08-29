# Solution 3 ⭐

[← 回到 L114: Flatten Binary Tree to Linked List](README.md)

Morris-like解法，利用左子樹的最右下節點原本沒用到的的right來記住原本的右子樹，以免除使用外空間。

`Time: O(n)`

`Space: O(1)`

```cpp
/*
如果 current 有左子樹：
1. 找左子樹最右邊
2. 最右邊接上原本右子樹
3. 左子樹搬到右邊
4. left 清空
5. current 往右走
*/

class Solution {
public:
    void flatten(TreeNode* root) {
        TreeNode* current = root;

        while (current != nullptr) {

            if (current->left != nullptr) {

                // 找左子樹最右邊的節點
                TreeNode* predecessor = current->left;

                while (predecessor->right != nullptr) {
                    predecessor = predecessor->right;
                }

                // 原本右子樹接到左子樹最後面
                predecessor->right = current->right;

                // 左子樹搬到右邊
                current->right = current->left;

                // left 必須清空
                current->left = nullptr;
            }

            current = current->right;
        }
    }
};
```
