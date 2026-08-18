# Solution 1 ⭐

[← 回到 L138: Copy List with Random Pointer](README.md)

利用hashmap，對應新舊節點，新節點可以靠舊節點的next,random資訊，找到對應該連接的新節點的記憶體位置。

`Time: O(n)`

`Space: O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;
    
    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/

class Solution {
public:
    Node* copyRandomList(Node* head) {
        unordered_map<Node*,Node*> old_to_new;
        Node* current = head;
        while(current){
            old_to_new[current] = new Node(current -> val);
            current = current->next;
        }
        current = head;
        while(current){
            old_to_new[current]->next = old_to_new[current->next];
            old_to_new[current]->random = old_to_new[current->random];
            current = current->next;
        }
        return old_to_new[head];
    }
};
```

</details>
