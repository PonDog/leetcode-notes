# Solution 1 ⭐

[← 回到 L219: Contains Duplicate II](README.md)

`Time: O(n)`

`Space: O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        unordered_map<int,int> seen;
        int n = nums.size();
        for(int i = 0; i < n; i++){
            int ele = nums[i];
            if(seen.count(ele)){
                if(i - seen[ele] <= k) return true;
            } 
            seen[ele] = i;
        } 
        return false;
    }
};
```

</details>
