# Solution 2 ⭐

[← 回到 L1: Two Sum](README.md)

用hashmap紀錄一次element和index的對應關係，之後就可以每次都只花O(1)確認第二個element。

`Time: O(n)`

`Space: O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size();
        unordered_map<int, int> m; 
        for(int i = 0; i < n; i++){
            m[nums[i]] = i; 
        }
        for(int i = 0; i < n; i++){
            int ele2 = target - nums[i];
            if(m.count(ele2) && m[ele2] != i){
                return {i,m[ele2]}; 
            }
        }
        return {};  
    }
};
```

</details>
