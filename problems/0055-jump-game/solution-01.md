# Solution 1 ⭐

[← 回到 L55: Jump Game](README.md)

每一輪都先檢查上一輪跳的距離能不能到當前index。

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    bool canJump(vector<int>& nums){
        int max_index = 0;  
        //統計到當前index所能到達的最遠index
        for(int i = 0; i <= nums.size()-1; i++){
            if(max_index < i) return false; 
            max_index = max(max_index,i+nums[i]); 
            //當前index能到的最遠距離＝max(index-1能到的最遠距離,以當前index走最大步)
            if(max_index >= nums.size()-1) return true;
        }
        return true;
    }
}; 
```

</details>
