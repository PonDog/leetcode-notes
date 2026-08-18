# Solution 1 ⭐

[← 回到 L289: Game of Life](README.md)

關鍵想法是把每個board裡的元素想成用二進制儲存，2^0 的位置儲存當前狀態，2^1 的位置儲存下一狀態，就能夠用一個元素同時紀錄所需的兩種狀態資訊
board[row][column] & 1 是轉成二進制做and運算，相當於％2，能夠取得2^0的位置的數字。

`Time: O(mn)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
private:

    int helper(int i, int j, vector<vector<int>>& board){   //判斷當前細胞周圍有幾個是live後，回傳count
        int m = board.size();
        int n = board[0].size();
        int count = 0;
        for(int row = max(0, i-1); row <= min(i+1, m-1); row++){
            for(int column = max(0, j-1); column <= min(j+1, n-1); column++){
                if(row == i && column == j) continue;
                if((board[row][column] & 1 ) == 1){
                    count++;
                }
            }
        }
        return count; 
    }   
public:
    void gameOfLife(vector<vector<int>>& board) {
        int m = board.size();
        int n = board[0].size();
        
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                int neighbor = helper(i, j, board);
                if(board[i][j] == 1){
                    if(neighbor == 2 || neighbor == 3){
                        board[i][j] += 2; 
                    }      
                }
                else if(board[i][j] == 0){
                    if(neighbor == 3){
                        board[i][j] += 2; 
                    } 
                }
            }
        }
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                board[i][j] >>= 1;      // 更新成2^1的位置的新狀態
            }
        }
    }
};
```

</details>
