# Solution 2

[← 回到 L226: Invert Binary Tree](README.md)

BFS queue

`Time: O(n)`

`Space: O(queue最大長度，即樹的層最大寬度)`

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
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty()){
            TreeNode* node = q.front();
            q.pop();
            if(!node) continue;
            TreeNode* temp = node->left;
            node->left = node->right;
            node->right = temp;
            q.push(node->left);
            q.push(node->right);
        }
        return root;
    }
};
```

</details>
