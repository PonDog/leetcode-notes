# Solution 1 ⭐

[← 回到 L226: Invert Binary Tree](README.md)

遞迴DFS

`Time: O(n)`

`Space: skewed:O(n) balanced:O(logn)`

<details>
<summary>展開程式碼</summary>

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if(!root) return root;
        TreeNode* left = invertTree(root->right);
        TreeNode* right = invertTree(root->left);
        root->left = left;
        root->right = right;
        return root;
    }
};
```

</details>
