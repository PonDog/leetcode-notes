# Solution 1 ⭐

[← 回到 L228: Summary Ranges](README.md)

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        vector<string> result;
        int n = nums.size();
        int i = 0;
        int j = 0;

        while (i < n) {
            while (j + 1 < n && nums[j + 1] == nums[j] + 1) {
                j++;
            }
            if (i == j) {
                result.push_back(to_string(nums[i]));
            } 
            else {
                result.push_back(to_string(nums[i]) + "->" + to_string(nums[j]));
            }
            i = j = j + 1;
        }
        return result;
    }
};
```

</details>
