# Solution 2 ⭐

[← 回到 L71: Simplify Path](README.md)

使用雙指標
`Time:O(n)
Space:O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    string simplifyPath(string path) {
        stack<string> st;
        int i = 0;
        int n = path.size();
        string result;

        while(i < n){
            while(i < n && path[i] == '/'){
                i++;
            }
            string temp;
            while(i < n && path[i] != '/'){
                temp += path[i++];
            }
            if(temp == "." || temp.empty()){
                continue;
            }
            else if(temp == ".."){
                if(!st.empty()){
                    st.pop();
                }
            }
            else{
                st.push(temp);
            }
        }
        while(!st.empty()){
            result = '/' + st.top() + result;
            st.pop(); 
        }
        return result.empty()? "/" : result;  
    }
};
```

</details>
