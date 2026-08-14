# Solution 1 ⭐

[← 回到 L20: Valid Parentheses](README.md)

`Time:O(n)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        for(char c : s){
            if(c == '{' || c == '[' || c == '('){
                st.push(c);
            }
            else{
                if(st.empty()) return false;
                char top = st.top();
                if(c == '}' && top != '{') return false;
                if(c == ']' && top != '[') return false;
                if(c == ')' && top != '(') return false;
                st.pop();                
            } 
        }
        return st.empty();
    }
};
```

</details>
