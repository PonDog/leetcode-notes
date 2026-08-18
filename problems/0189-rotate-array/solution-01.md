# Solution 1

[← 回到 L189: Rotate Array](README.md)

我的垃圾方法，Time exceeded

`Time: O(n^2)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        for(int i = 1; i <= k; i++){
            nums.insert(nums.begin(),nums.back());
            nums.pop_back();
        }            
    }
};
```

</details>
