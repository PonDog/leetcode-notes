# Solution 1 ⭐

[← 回到 L73: Set Matrix Zeroes](README.md)

用原matrix的第一行和第一列紀錄該行列是否要變0，但因為只有一格(0,0)不夠拿來記第一行和第一列的情況，
所以額外開兩個變數，firstRowZero和firstColZero來記錄記第一列和第一行是否有0。

`Time:O(mn)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        int m = matrix.size();
        int n = matrix[0].size();

        bool firstRowZero = false;
        bool firstColZero = false;

        for (int j = 0; j < n; j++) { //找第一列是否出現0，用firstRowZero記錄
            if (matrix[0][j] == 0) {
                firstRowZero = true;
                break;
            }
        }

        for (int i = 0; i < m; i++) { //找第一行是否出現0，用firstColumnZero記錄
            if (matrix[i][0] == 0) {
                firstColZero = true;
                break;
            }
        }

        for (int i = 1; i < m; i++) {      //找其餘行列是否出現0，用matrix的第一列和第一行記錄
            for (int j = 1; j < n; j++) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = 0;
                    matrix[0][j] = 0;
                }
            }
        }

        for (int i = 1; i < m; i++) {      //正式把其餘行列出現0的改成0(第一列第一行所對應行列該改的有在記錄時改過了)
            for (int j = 1; j < n; j++) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) { 
                    matrix[i][j] = 0;
                }
            }
        }

        if (firstRowZero) {               //第一列該改的話，整列改成0
            for (int j = 0; j < n; j++) {
                matrix[0][j] = 0;
            }
        }

        if (firstColZero) {               //第一行該改的話，整行改成0
            for (int i = 0; i < m; i++) { 
                matrix[i][0] = 0;
            }
        }
    }
};
```

</details>
