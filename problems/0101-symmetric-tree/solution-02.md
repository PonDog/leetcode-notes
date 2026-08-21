# Solution 2

[← 回到 L101: Symmetric Tree](README.md)

BFS queue

`Time: O(n)`

`Space: O(queue最大長度，即樹的最大寬度)`

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
private:
    bool isMirror(TreeNode* root1, TreeNode* root2){
        queue<pair<TreeNode*, TreeNode*>> q;
        q.push({root1, root2});
        while(!q.empty()){
            TreeNode* node1 = q.front().first;
            TreeNode* node2 = q.front().second;
            q.pop();
            if(!node1 && !node2) continue;
            if(!node1 || !node2) return false; //這裡以前處理node1和node2可能為空的情況，之後才能確定兩個node都有val可以比較
            if(node1->val != node2->val) return false; //不等於就early return，等於則繼續push之後要判斷的node pair
            q.push({node1->left, node2->right});
            q.push({node1->right, node2->left});
        }
        return true;
    }
public:
    bool isSymmetric(TreeNode* root) {
        if(!root) return true; //預防root = nullptr
        return isMirror(root->left, root->right);
    }
};
```

</details>
