# Solution 2 ⭐

[← 回到 L26: Remove Duplicates from Sorted Array](README.md)

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int index = 0;
        for(int i = 0; i < nums.size(); i++){
            if(index == 0 || nums[index-1] != nums[i]){
                nums[index++] = nums[i];
            }
        }
        return index;
    }
};
```

</details>
