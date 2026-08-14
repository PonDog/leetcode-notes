# Solution 1 ⭐

[← 回到 L104: Maximum Depth of Binary Tree](README.md)

DFS遞迴法
`Time:O(n)每個節點拜訪一次
Space:skewed:O(n) balanced:O(logn)`

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
    int maxDepth(TreeNode* root) {
        if(!root){
            return 0;
        }
        return max(maxDepth(root->left), maxDepth(root->right))+1;
    }
};
```

</details>
