# Solution 1 ⭐

[← 回到 L209: Minimum Size Subarray Sum](README.md)

這邊的重要前提是所有數都是正數，因此j越往右，sum越大;i越往右，sum越小
遍歷所有右標j的可能，且sum >= target停下來，代表目前是合法的j，
停下來後開始縮左標i，縮到sum < target為止，並在過程中維護min_length，
這裡的關鍵是每次j往右，i不用重頭考慮，可以直接接續上一輪的i，因為考慮更左邊的i只會比過去紀錄更長。
遍歷次數<=2n

`Time:O(n)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums){
        int min_length = INT_MAX;
        int sum = 0;
        int n = nums.size();
        int i = 0;
        int j = 0;
        while(j < n){
            sum += nums[j];
            while(sum >= target){
                min_length = min(min_length, j-i+1);
                sum -= nums[i]; 
                i++;     
            }
            j++;    
        }
        return min_length == INT_MAX? 0 : min_length;
    }    
}; 
```

</details>
