# Solution 1 ⭐

[← 回到 L48: Rotate Image](README.md)

`Time:O(n^2)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int n = matrix.size();
        // 1. 上下翻轉
        for (int i = 0; i < n / 2; i++) {
            swap(matrix[i], matrix[n - 1 - i]);
        }

        // 2. 沿主對角線翻轉
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                swap(matrix[i][j], matrix[j][i]);
            }
        }
    }
};
```


</details>
