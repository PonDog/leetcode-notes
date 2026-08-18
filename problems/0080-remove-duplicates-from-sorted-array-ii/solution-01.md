# Solution 1

[← 回到 L80: Remove Duplicates from Sorted Array II](README.md)

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int index = 2;
        int j = 2;
        if(j <= nums.size() - 1) {
            for(int i = 2; i <= nums.size() - 1; i++){
                if(nums[index-2] != nums[i]){
                    nums[index++] = nums[i];
                }
            }
            return index; 
        }
        else if( nums.size() == 1) {
            return index-1;
        }
        else if( nums.size() == 2) {
            return index;
        }
        else return 0;
    }
};    
```

</details>
