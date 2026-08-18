# Solution 1 ⭐

[← 回到 L238: Product of Array Except Self](README.md)

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> answer(nums.size());
        answer[0] = 1;
        for(int i = 1; i <= nums.size()-1; i++){
            answer[i] = answer[i-1] * nums[i-1];
        }
        answer[nums.size()-1] = answer[nums.size()-1] * 1;
        for(int i = nums.size()-2; i >= 0; i--){
            answer[i] = answer[i] * nums[i+1];
            nums[i] = nums[i] * nums[i+1];
        } 
        return answer;   
    }
};
```

</details>
