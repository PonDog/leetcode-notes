# Solution 3 ⭐

[← 回到 L14: Longest Common Prefix](README.md)

拿第一個字串依序和後面比，每次把不一樣的字元扣掉，留共同prefix繼續和下一個string比。

`Time: O(n*m)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        string prefix = strs[0];

        for (int i = 1; i < strs.size(); i++) {
            int j = 0;

            while (j < prefix.size() && j < strs[i].size()
                   && prefix[j] == strs[i][j]) {
                j++;
            }

            prefix = prefix.substr(0, j);

            if (prefix.empty()) return "";
        }
        return prefix;
    }
};
```

</details>
