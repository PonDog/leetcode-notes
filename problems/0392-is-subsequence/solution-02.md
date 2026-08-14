# Solution 2 ⭐

[← 回到 L392: Is Subsequence](README.md)

`Time:O(n)，n = s.size();
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    bool isSubsequence(string s, string t) {
        int count = 0;
        int n = s.size();
        int m = t.size();
        int i = 0;
        int j = 0;

        if(n == 0 && m ==0) return true;
        while(i < n && j < m){
            if(s[i] == t[j]){ 
                i++;
            }
            j++;
        }
        if(i == n) return true;
        else return false;    
    }
};
```

</details>
