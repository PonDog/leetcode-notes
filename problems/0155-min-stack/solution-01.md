# Solution 1 ⭐

[← 回到 L155: Min Stack](README.md)

`Time: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class MinStack {
private:
    stack<pair<int, int>> st;
public:
    MinStack() {
    }
    
    void push(int value) {
        if(st.empty()){
            st.push({value, value});
        }
        else{
            st.push({value, min(value, st.top().second)});
        }
    }
    
    void pop() {
        st.pop();
    }
    
    int top() {
        return st.top().first;
    }
    
    int getMin() {
        return st.top().second;
    }
};
```

</details>
