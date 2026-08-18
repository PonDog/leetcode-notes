# Solution 1 ⭐

[← 回到 L49: Group Anagrams](README.md)

`Time: O(nklogk)`

`Space: O(nk)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string,vector<string>> m;
        vector<vector<string>>result; 
        for(string element : strs){
            string sorted_str = element;
            sort(sorted_str.begin(),sorted_str.end());
            m[sorted_str].push_back(element);
        }
        for(auto element : m){
            result.push_back(element.second);
        }
        return result;
    }
};
```

</details>
