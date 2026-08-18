# Solution 1

[← 回到 L392: Is Subsequence](README.md)

`Time: O(m)，m = t.size();`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    bool isSubsequence(string s, string t) {
        int count = 0;
        int n = s.size();
        int m = t.size();
        int j = 0;
        for(int i = 0; i < n; i++){
            if(s[j] == t[i]){ 
                count++;
                j++;
            }
            if(count == m) return true;
        }
        if(n == 0 && m ==0 )return true;
        return false;    
    }
};
```

</details>
