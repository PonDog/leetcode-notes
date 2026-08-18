# Solution 1 ⭐

[← 回到 L128: Longest Consecutive Sequence](README.md)

`Time: O(n)`

`Space: O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_set<int> s(nums.begin(),nums.end());
        int result = 0;
        for(auto ele : s){
            if(!s.count(ele - 1)){    //找到Consecutive Sequence的左邊界
                int l = 1;
                while(s.count(++ele)) l++;
                result = max(result, l);
            }
        }
        return result; 
    }
};
```

</details>
