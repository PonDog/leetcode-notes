# Solution 1 ⭐

[← 回到 L101: Symmetric Tree](README.md)

遞迴 DFS。\
  原本的 `isSymmetric(root)` 用來判斷一棵樹本身是否對稱，但拆分後的子問題並不是「左右子樹各自是否對稱」，因為兩棵各自對稱的樹不一定互為鏡像。因此，另外定義 `isMirror(root1, root2)`，判斷兩棵樹是否互為鏡像。判斷方式與 Same Tree 類似，但子節點需要交叉比較：`root1->left` 對應 `root2->right`，`root1->right` 對應 `root2->left`。

`Time: O(n)`

`Space: skewed\:O(n) balanced\:O(logn)`

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
        if(!root1 && !root2) return true;
        if(!root1 || !root2) return false;
        if(root1->val != root2->val) return false;
        if(!isMirror(root1->left, root2->right)) return false;
        if(!isMirror(root1->right, root2->left)) return false;
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
