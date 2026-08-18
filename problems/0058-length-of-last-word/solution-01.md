# Solution 1 ⭐

[← 回到 L58: Length of Last Word](README.md)

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int max = 0;
        int i = s.size() - 1;
        while(i >= 0 && s[i] == ' ') i--;
        while(i >= 0 && s[i] != ' ') {
            i--;
            max++;
        }  
        return max;                              
    }
};
```

</details>
