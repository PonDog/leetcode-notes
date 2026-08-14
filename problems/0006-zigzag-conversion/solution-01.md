# Solution 1 ⭐

[← 回到 L6: Zigzag Conversion](README.md)

開numRows數的string vector，遍歷過程中，加到對應的string，最後把string合併。

`Time:O(n)
Space:O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    string convert(string s, int numRows) {
        vector<string> temp(numRows); 
        int index = 0;
        int n = s.size();
        
        while(index < n){
            for(int i = 0; i < numRows & index < n; i++){
            temp[i] += s[index++];
            }
            for(int i = numRows-2; i > 0 & index < n; i--){
            temp[i] += s[index++];
            }
        }
        for(int i = 1; i < numRows; i++){
            temp[0] += temp[i]; 
        }
        return temp[0];
    }
};
```

</details>
