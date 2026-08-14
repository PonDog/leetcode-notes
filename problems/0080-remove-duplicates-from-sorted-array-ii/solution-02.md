# Solution 2 ⭐

[← 回到 L80: Remove Duplicates from Sorted Array II](README.md)

要考慮到長度為1和2的情況怎麼處理

`Time:O(n)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int index = 0;
        for(int i = 0; i <= nums.size()-1; i++){
            if( index == 0|| index == 1|| nums[index-2] != nums[i]){
                nums[index++] = nums[i];                
            }
        }
        return index; 
    }
};      
```

</details>
