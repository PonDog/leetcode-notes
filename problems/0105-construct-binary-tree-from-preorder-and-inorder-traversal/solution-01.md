# Solution 1 ⭐

[← 回到 L105: Construct Binary Tree from Preorder and Inorder Traversal](README.md)

這題用遞迴拆解子問題：先取 Preorder 區間的第一個元素當作目前子樹的根節點，再利用 HashMap 使每次只花O(1)找到它在 Inorder 的index。根左邊的 Inorder 區間就是左子樹，根右邊的區間就是右子樹；根據左子樹的節點數量，再切出對應的 Preorder 區間，分別遞迴建立左右子樹。每次遞迴都把「建立一棵樹」拆成「建立左子樹」和「建立右子樹」兩個相同類型的小問題；終止條件為當區間為空時回傳 `nullptr`。

`Time: O(n)每個節點建立一次`

`Space: O(n)(hashmap) + O(n)(最歪的樹) = O(n)`

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
    unordered_map<int, int> inorderIndex;

    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        for (int i = 0; i < inorder.size(); i++) {
            inorderIndex[inorder[i]] = i;   //記錄每個node在inorder的index
        }

        return build(preorder, 0, preorder.size() - 1,
                     inorder, 0, inorder.size() - 1);
    }

private:
    TreeNode* build(vector<int>& preorder, int preorderLeft, int preorderRight,
                    vector<int>& inorder, int inorderLeft, int inorderRight) {

        // 沒有節點
        if (preorderLeft > preorderRight) { //也可以判斷inorderLeft > inorderRight，因為Preorder 和 Inorder 的區間一定包含相同數量的節點
            return nullptr;
        }

        // Preorder 第一個節點就是根
        int rootValue = preorder[preorderLeft];
        TreeNode* root = new TreeNode(rootValue);

        // 找根在 Inorder 的位置
        int rootIndex = inorderIndex[rootValue];

        // 靠 Inorder 算出左子樹節點數量（關鍵）
        int leftSize = rootIndex - inorderLeft;

        // 建立左子樹
        root->left = build(
            preorder,
            preorderLeft + 1,
            preorderLeft + leftSize,
            inorder,
            inorderLeft,
            rootIndex - 1
        );

        // 建立右子樹
        root->right = build(
            preorder,
            preorderLeft + leftSize + 1,
            preorderRight,
            inorder,
            rootIndex + 1,
            inorderRight
        );

        return root;
    }
};
```

</details>
