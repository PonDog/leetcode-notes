# Solution 2 ⭐

[← 回到 L122: Best Time to Buy and Sell Stock II](README.md)

第二次寫出來的答案，想法相同，但更精簡一點。
`Time:O(n)
Space:O(1)`
<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
    int max_profit = 0;
        for(int buy = 0, sell = 1; sell < prices.size(); buy++, sell++){
            if(prices[buy] < prices[sell]){
                max_profit += prices[sell] - prices[buy];
            }
        }
        return max_profit;       
    }
};

```

</details>
