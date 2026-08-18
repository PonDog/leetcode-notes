# Solution 2 ⭐

[← 回到 L189: Rotate Array](README.md)

用到algorithm的reverse，也可自己寫reverse

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        k = k % nums.size();
        
        reverse(nums.begin(),nums.end());
        reverse(nums.begin(),nums.begin() + k );
        reverse(nums.begin() + k ,nums.end());
    }
};
```

</details>
