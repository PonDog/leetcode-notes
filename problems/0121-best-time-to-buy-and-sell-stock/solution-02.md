# Solution 2 ⭐

[← 回到 L121: Best Time to Buy and Sell Stock](README.md)

更簡潔一點。

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        int buy = prices[0];
        int max_profit = 0;
        for(int i = 0; i < n; i++){
            buy = min(buy,prices[i]);
            max_profit = max(max_profit,prices[i]-buy);    
        }
        return max_profit;    
    }
};
```

</details>
