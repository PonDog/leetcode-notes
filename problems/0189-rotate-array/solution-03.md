# Solution 3

[← 回到 L189: Rotate Array](README.md)

先算出每個element移動完後的位置，移到額外陣列，再移回來。

`Time: O(n)`

`Space: O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k = k % n;
        vector<int> result(n);
        for(int i = 0; i < k; i++){
           result[i] = nums[n-k+i];   
        }
        for(int i = 0; i < n-k; i++){
           result[k+i] = nums[i];
        }
        for(int i = 0; i < n; i++){
           nums[i] = result[i];  
        }
    }
};
```

</details>
