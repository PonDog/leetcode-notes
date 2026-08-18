# Solution 1 ⭐

[← 回到 L146: LRU Cache](README.md)

利用hashmap來達成O(1)搜尋
利用雙向鏈結串列維護新舊節點關係

`Time: O(1)`

`Space: O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class LRUCache {
private:
    struct Node {
        int key;   //這裡要另外存key才能在hashmap裡利用key刪除對應的map對
        int value;
        Node* prev;
        Node* next;

        Node(int key = 0, int value = 0)
            : key(key), value(value), prev(nullptr), next(nullptr) {}
    };

    int capacity;
    unordered_map<int, Node*> cache;

    // head->next：最近使用
    // tail->prev：最久未使用
    Node* head;
    Node* tail;

    // 從鏈結串列移除 node
    void removeNode(Node* node) {   //只是暫時拆下來，之後可能還會addToFront，所以先不用delete
        Node* previous = node->prev;
        Node* following = node->next;

        previous->next = following;
        following->prev = previous;
    }

    // 把 node 放到最前面，也就是 head 後面
    void addToFront(Node* node) {
        Node* first = head->next;

        head->next = node;
        node->prev = head;

        node->next = first;
        first->prev = node;
    }

    // 將既有節點移到最前面
    void moveToFront(Node* node) {
        removeNode(node);
        addToFront(node);
    }

public:
    LRUCache(int capacity) {
        this->capacity = capacity;  //this指標指向當前物件
 
        // Dummy nodes
        head = new Node();
        tail = new Node();

        head->next = tail;
        tail->prev = head;
    }

    int get(int key) {
        // 找不到
        if (cache.find(key) == cache.end()) {
            return -1;
        }

        Node* node = cache[key];

        // 剛被使用，移到最前面
        moveToFront(node);

        return node->value;
    }

    void put(int key, int value) {
        // key 已經存在
        if (cache.find(key) != cache.end()) {
            Node* node = cache[key];

            node->value = value;
            moveToFront(node);

            return;
        }

        // 建立新節點
        Node* newNode = new Node(key, value);

        cache[key] = newNode;
        addToFront(newNode);

        // 超過容量，淘汰最久未使用的節點
        if (cache.size() > capacity) {
            Node* lruNode = tail->prev;

            removeNode(lruNode);
            cache.erase(lruNode->key);
            delete lruNode;
        }
    }

    ~LRUCache() {     //destructor，在物件生命週期結束時會自動執行，釋放記憶體
        Node* current = head;

        while (current != nullptr) {
            Node* nextNode = current->next;
            delete current;
            current = nextNode;
        }
    }
};
```

</details>
