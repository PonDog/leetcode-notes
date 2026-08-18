# Solution 1 ⭐

[← 回到 L380: Insert Delete GetRandom O(1)](README.md)

`Time: O(1)`

`Space: O(n)`

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
