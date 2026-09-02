# Solution 1 ⭐

[← 回到 L112: Path Sum](README.md)

遞迴DFS

`Time: O(n)`

`Space: O(樹高)`

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
    bool hasPathSum(TreeNode* root, int targetSum) {
        if(!root) return false;            //這邊是防止空節點
        if(!root->left && !root->right) {  //實際的終止條件是走到葉節點
            return targetSum == root->val;
        }
        targetSum = targetSum - root->val;
        return hasPathSum(root->left, targetSum) || hasPathSum(root->right, targetSum);
    }
};
```
