# Solution 1 ⭐

[← 回到 L15: 3Sum](README.md)

排序後，遍歷nums每輪固定i，用頭尾i,j雙指針找，這邊比較麻煩的是換i時和換j,k要去重。
這邊有很多種寫法可以去重，但其實只要在tmp==0時，去重i或j其中一邊就可以讓另一邊也自動去重，因為固定了其中兩個值，可能的另一個值就是唯一值。
`Time:O(n^2)
Space:O(logn)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<vector<int>> result;
        for(int i = 0; i < nums.size(); i++){
            if(i > 0 && nums[i] == nums[i-1]) continue;
            int j = i + 1;
            int k = nums.size()-1;
            while(j < k){
                int tmp = nums[i] + nums[j] + nums[k];
                if(tmp == 0){
                    result.push_back({nums[i], nums[j], nums[k]});
                    
                    j++;
                    while(j < k && nums[j] == nums[j-1]) j++; 
                    k--;
                    while(j < k && nums[k] == nums[k+1]) k--;
                }
                else if (tmp < 0) j++;
                else if (tmp > 0) k--;
            }
        }
        return result;
    }
};
```

</details>
