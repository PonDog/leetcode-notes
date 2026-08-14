# Solution 1 ⭐

[← 回到 L205: Isomorphic Strings](README.md)

`Time:O(n)
Space:O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        int n = s.size();
        vector<char> st(128, ' ');
        vector<char> ts(128, ' ');

        for(int i = 0; i < n; i++){
            if(st[s[i]] == ' ' && ts[t[i]] == ' '){
                st[s[i]] = t[i];
                ts[t[i]] = s[i];
            }
            else{
                if(st[s[i]] != t[i]){
                    return false;
                }
            }
        }
        return true;   
```

</details>
