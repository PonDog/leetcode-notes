# Solution 2

[← 回到 L104: Maximum Depth of Binary Tree](README.md)

BFS

`Time: O(n)`

`Space: O(每層最大寬度，即過程中Queue的最大長度)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (root == nullptr) {
            return 0;
        }

        queue<TreeNode*> q;
        q.push(root);

        int depth = 0;

        while (!q.empty()) {
            int levelSize = q.size();

            for (int i = 0; i < levelSize; i++) {
                TreeNode* node = q.front();
                q.pop();

                if (node->left != nullptr) {
                    q.push(node->left);
                }

                if (node->right != nullptr) {
                    q.push(node->right);
                }
            }

            depth++;
        }

        return depth;
    }
};
```

</details>
