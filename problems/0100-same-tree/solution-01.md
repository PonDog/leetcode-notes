# Solution 1 ⭐

[← 回到 L100: Same Tree](README.md)

遞迴DFS，early return，亦可使用非遞迴的BFS queue或DFS stack來解

`Time: O(n)`

`Space: skewed :O(n) balanced:O(logn)`

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
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(!p && !q) return true;
        if(!p || !q) return false;
        if(p->val != q->val) return false;
        if(!isSameTree(p->left, q->left)) return false;
        if(!isSameTree(p->right, q->right)) return false;
        return true;  
    }
};
```

</details>
