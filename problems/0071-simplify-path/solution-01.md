# Solution 1

[← 回到 L71: Simplify Path](README.md)

使用stringstream
`Time:O(n)
Space:O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    string simplifyPath(string path) {
        stringstream ss(path);
        string dir;
        vector<string> stk;     //亦可用stack

        while (getline(ss, dir, '/')) {
            if (dir.empty() || dir == ".") {
                continue;
            }
            else if (dir == "..") {
                if (!stk.empty())
                    stk.pop_back();
            } 
            else {
                stk.push_back(dir);
            }
        }

        string ans;
        for (string& s : stk) {
            ans += "/" + s;
        }

        return ans.empty() ? "/" : ans;
    }
};
```

</details>
