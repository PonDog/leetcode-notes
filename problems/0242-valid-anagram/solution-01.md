# Solution 1 ⭐

[← 回到 L242: Valid Anagram](README.md)

如果改成用Unicode，改用u32string和char32_t。
`Time:O(n)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        int n = s.size();
        int m = t.size();
        vector<int> count(26,0);
        int k = count.size();
        if(n != m) return false;
        for(int i = 0; i < n; i++){
            count[s[i] - 'a']++;
            count[t[i] - 'a']--;
        }
        for(int i = 0; i < k; i++){
            if(count[i] != 0) return false;
        }
        return true;
    }
};
```

</details>
