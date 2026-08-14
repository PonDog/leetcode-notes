# Solution 1 ⭐

[← 回到 L27: Remove Element](README.md)

雙指針，i遍歷找!=val的值，找到符合條件就丟到index位置放好，
index和count(k)剛好可共用。

`Time:O(n)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int index = 0;
        for(int i = 0; i< nums.size(); i++){
            if(nums[i] != val){
                nums[index] = nums[i];
                index++;
            }
        }
        return index;
    }
};
```

</details>
