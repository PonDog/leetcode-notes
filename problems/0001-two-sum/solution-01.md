# Solution 1

[← 回到 L1: Two Sum](README.md)

暴力法

`Time: O(n^2)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size();
        for(int i = 0; i < n; i++){
            for(int j = i+1; j < n; j++){
                if(nums[i] + nums[j] == target){
                    return {i,j};
                } 
            }
        }
        return {};  
    }
};
```

</details>
