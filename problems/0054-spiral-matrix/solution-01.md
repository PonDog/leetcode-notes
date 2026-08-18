# Solution 1 ⭐

[← 回到 L54: Spiral Matrix](README.md)

自己寫出來了，讚讚！

`Time: O(m*n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int row_start = -1;
        int column_start = -1;
        int row_end = matrix.size();
        int column_end = matrix[0].size();
        int total = row_end * column_end;
        vector<int> result;
        int i = 0;
        int j = 0;
        int count = 0;  
        while(count < total){
            while(count < total && j < column_end){
                result.push_back(matrix[i][j++]);
                count++;        
            }
            row_start++;
            i++;
            j--;
            while(count < total && i < row_end){
                result.push_back(matrix[i++][j]);
                count++;
            }
            column_end--;
            i--;
            j--;
            while(count < total && j > column_start){
                result.push_back(matrix[i][j--]); 
                count++;
            }
            row_end--;
            i--;
            j++;
            while(count < total && i > row_start){
                result.push_back(matrix[i--][j]);
                count++;
            }
            column_start++;
            i++;
            j++;
        }
        return result;    
    }
};
//下面是再簡化一點維護邊界的版本，差異不大
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int row_start = 0;
        int column_start = 0;
        int row_end = matrix.size()-1;
        int column_end = matrix[0].size()-1;
        int total = (row_end+1) * (column_end+1);
        vector<int> result;
        int i = 0;
        int j = 0;
        int count = 0;  
        while(count < total){
            while(count < total && j <= column_end){
                result.push_back(matrix[row_start][j++]);
                count++;        
            }
            i = ++row_start;
            while(count < total && i <= row_end){
                result.push_back(matrix[i++][column_end]);
                count++;
            }
            j = --column_end;
            while(count < total && j >= column_start){
                result.push_back(matrix[row_end][j--]); 
                count++;
            }
            i = --row_end;
            while(count < total && i >= row_start){
                result.push_back(matrix[i--][column_start]);
                count++;
            }
            j = ++column_start;
        }
        return result;    
    }
};
```

</details>
