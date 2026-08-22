# Solution 1 ⭐

[← 回到 L106: Construct Binary Tree from Inorder and Postorder Traversal](README.md)

遞迴DFS，和L105概念相同。另外程式設計上，以較好的 C++ 設計來說，推薦在 buildTree() 建立 map，再用 const reference 傳入 build()。這樣每次呼叫 buildTree() 都會建立新的 map，較不易受到前次呼叫的資料殘留影響。這裡是為了方便放在private。

`Time: O(n)`

`Space: O(n)`

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
    unordered_map<int, int> inorderindex;

    TreeNode* build(vector<int>& inorder, int inorderleft, int inorderright,
                    vector<int>& postorder, int postorderleft, int postorderright){
        if(inorderleft > inorderright) return nullptr;

        int rootvalue = postorder[postorderright];
        TreeNode* node = new TreeNode(rootvalue);

        int rootindex = inorderindex[rootvalue]; 
        int leftsize = rootindex - inorderleft;        

        node->left = build(inorder, inorderleft, rootindex-1,
                           postorder, postorderleft, postorderleft+leftsize-1);
        node->right = build(inorder, rootindex+1 , inorderright,
                            postorder, postorderleft+leftsize, postorderright-1);
        return node;
    }
public:
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        for(int i = 0; i < inorder.size(); i++){
            inorderindex[inorder[i]] = i;
        }
        return build(inorder, 0, inorder.size()-1,
                      postorder, 0, postorder.size()-1);
        
    }
};
```
