# Solution 1 ⭐

[← 回到 L150: Evaluate Reverse Polish Notation](README.md)

`Time:O(n)
Space:O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<string> st;
        for(string ele : tokens){
            if(ele == "+" || ele == "-" || ele == "*" || ele == "/"){
                int op2 = stoi(st.top());
                st.pop();
                int op1 = stoi(st.top());
                st.pop();
                int temp;
                if(ele == "+"){
                    temp = op1 + op2;
                }
                else if(ele == "-"){
                    temp = op1 - op2;
                }
                else if(ele == "*"){
                    temp = op1 * op2;
                }
                else if(ele == "/"){
                    temp = op1 / op2;
                }
                st.push(to_string(temp)); 
            }
            else{
                st.push(ele);
            }
        }
        return stoi(st.top());   
    }
};
```

</details>
