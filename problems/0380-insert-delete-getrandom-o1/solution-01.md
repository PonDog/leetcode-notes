# Solution 1 ⭐

[← 回到 L380: Insert Delete GetRandom O(1)](README.md)

`Time:O(1)
Space:O(n)`
unordered_map底層透過hash table操作，搜尋/插入/刪除平均O(1)，最壞O(n)(collision)。
unordered_set亦同。
set和map則是平衡BST，搜尋/插入/刪除平均O(logn)。

1.這邊用unordered_map存{val, vector_index}，並用vector存val，沒法單用unordered_set，因為需要getRandom()，unordered_set無法隨機存取
2.另外有小細節是刪除時，搬vector最後一個補空缺，才不會花O(n)移動element
3.unordered_map的key沒辦法直接改，因為hash會變動，要直接重insert一筆並erase舊的

<details>
<summary>展開程式碼</summary>

```cpp
class RandomizedSet {
private:
    vector<int> v;
    unordered_map<int,int> m;
public:
    RandomizedSet() {
    }
    bool insert(int val) {
        if(m.find(val) == m.end()){
            v.push_back(val);
            m.insert({val,v.size()-1});
            return true;    
        }
        else return false;
    }
    
    bool remove(int val) {
        if(m.find(val) != m.end()){
            v[m[val]] = v.back();
            m[v.back()] = m[val];
            v.pop_back();
            m.erase(val);
            return true;    
        }
        else return false;
    }
    
    int getRandom() {
        return v[rand()%v.size()];    
    }
};
```

</details>
