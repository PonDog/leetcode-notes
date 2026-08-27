# Solution 1

[← 回到 L117: Populating Next Right Pointers in Each Node II](README.md)

BFS queue，將節點連起來的處理順序就和level order traversal一樣

`Time: O(n)`

`Space: O(queue最大長度)`

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;
    Node* next;

    Node() : val(0), left(NULL), right(NULL), next(NULL) {}

    Node(int _val) : val(_val), left(NULL), right(NULL), next(NULL) {}

    Node(int _val, Node* _left, Node* _right, Node* _next)
        : val(_val), left(_left), right(_right), next(_next) {}
};
*/

class Solution {
public:
    Node* connect(Node* root) {
        queue<Node*> q;
        if(root) q.push(root);
        while(!q.empty()){
            int n = q.size();      //每一層的節點數
            Node dummy;
            Node* prev = &dummy;
            for(int i = 1; i <= n; i++){  //將每一層的節點連在一起
                Node* cur = q.front();
                q.pop();
                prev->next = cur;
                prev = cur;

                if(cur->left) q.push(cur->left);   //將下一層的節點依序塞進queue
                if(cur->right) q.push(cur->right);
            } 
        }
        return root;        
    }
};
```
