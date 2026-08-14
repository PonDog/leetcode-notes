# Solution 3

[← 回到 L169: Majority Element](README.md)

`Time:O(n)
Space:O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int n = nums.size();
        unordered_map<int, int> m;
        
        for(int element:nums){
            if(++m[element] > n/2) {
                return element;
            }
        }
        return 0;
    }
};
```

</details>
