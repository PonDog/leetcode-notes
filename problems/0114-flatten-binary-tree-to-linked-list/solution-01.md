# Solution 1

[← 回到 L114: Flatten Binary Tree to Linked List](README.md)

DFS stack，要注意的是因為要照preorder順序，在壓入stack時，要先push右節點，左節點才會先pop。

`Time: O(n)`

`Space: O(stack最大長度)`

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
    void flatten(TreeNode* root) {
        stack<TreeNode*> s;

        if(root) s.push(root);
        TreeNode dummy;
        TreeNode* prev = &dummy;
        while(!s.empty()){
            TreeNode* cur = s.top();
            s.pop();

            prev->right = cur;
            prev->left = nullptr;
            prev = cur; 

            if(cur->right) s.push(cur->right);
            if(cur->left) s.push(cur->left);
        }
    }
};
```
