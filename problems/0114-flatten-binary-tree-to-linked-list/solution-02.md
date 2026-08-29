# Solution 2

[← 回到 L114: Flatten Binary Tree to Linked List](README.md)

遞迴DFS，用preorder的反序(RLD)來依序從最右最底開始連接每個節點，並且這裡用prev這個全域變數來保存要連到哪個root來取代回傳值，則還會需要多額外判斷才能連接。

`Time: O(n)`

`Space: O(樹高)`

```cpp
class Solution {
private:
    TreeNode* prev = nullptr;

    void dfs(TreeNode* root) {
        if (root == nullptr) {
            return;
        }

        // 一定先右再左
        dfs(root->right);
        dfs(root->left);

        root->right = prev;
        root->left = nullptr;

        prev = root;
    }

public:
    void flatten(TreeNode* root) {
        dfs(root);
    }
};
```
