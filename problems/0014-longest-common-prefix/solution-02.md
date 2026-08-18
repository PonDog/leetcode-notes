# Solution 2

[← 回到 L14: Longest Common Prefix](README.md)

排序後，只要看最小字典序和最大字典序的字串。
它們的共同前綴，就是全部字串的共同前綴。

`Time: O(nlogn*m)`

`Space: O(logn)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        sort(strs.begin(), strs.end());
        string s = "";
        int i = 0, length = strs.size();
        while (i < strs[0].length()){
            if (strs[0][i] == strs[length-1][i]) s += strs[0][i];
            else break;
            i++;
        }
        return s;
    }
};
```

</details>
