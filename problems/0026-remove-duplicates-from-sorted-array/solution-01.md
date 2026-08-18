# Solution 1

[← 回到 L26: Remove Duplicates from Sorted Array](README.md)

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int index = 1;
        for(int i = 1; i <= nums.size()-1; i++){
           if(nums[i] != nums[index-1]){
               nums[index++] = nums[i];
           }
        }
        return index;
    }
};
```

</details>
