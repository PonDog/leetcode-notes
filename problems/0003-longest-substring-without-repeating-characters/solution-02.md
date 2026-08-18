# Solution 2 ⭐

[← 回到 L3: Longest Substring Without Repeating Characters](README.md)

Sliding Window:
由左至右遍歷s，每輪對於固定的右端點j，始終維持「最靠左且合法的i」，且每次決定i只花O(1)。
任何比它更右的起點都只會得到更短的 substring，更左的不合法，因此不需要考慮。
這邊可以用vector或underored_map來存字母上次出現的index，但vector還是比較快。

`Time: O(n)`

`Space: O(128)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        vector<int> latest_index(128,-1);
        int max_length = 0;
        int n = s.size();
        for(int i = 0, j = 0; j < n; j++){
            i = max(i,latest_index[s[j]]+1);
            max_length = max(max_length, j-i+1);
            latest_index[s[j]] = j;             
        }
        return max_length;       
    }
};

class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<int,int> latest_index;
        int max_length = 0;
        int n = s.size();
        for(int i = 0, j = 0; j < n; j++){
            if(latest_index.find(s[j])!= latest_index.end()){
                i = max(i,latest_index[s[j]]+1); 
            } 
            max_length = max(max_length, j-i+1);
            latest_index[s[j]] = j;             
        }
        return max_length;       
    }
};
```

</details>
