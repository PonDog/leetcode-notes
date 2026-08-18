# Solution 1

[← 回到 L169: Majority Element](README.md)

`Time: O(nlogn)`

`Space: O(logn)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        return nums[nums.size()/2];
    }
};
```

</details>
