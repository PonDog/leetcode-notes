# Solution 1

[← 回到 L121: Best Time to Buy and Sell Stock](README.md)

觀察[7,1,5,3,6,4]發現對陣列中每個值當賣出點來算max_profit，最佳的賣出點一定是該值左邊的min，因此左到右遍歷並維護min，每個算出的profit都可能當max_profit。
補充：因為每輪會先維護min，所以每個值當賣出點的當下，所減的buy必是該值左邊的min。
>[!Tip] 類似Kadane's Algorithm解Maxium Subarray Sum 但我覺得沒有很像


`Time:O(n)
Space:O(1)`
<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int buy = INT_MAX;      
        int max_profit = 0 ;
        for (int i = 0; i < prices.size(); i++){
            if(prices[i] < buy){
                buy = prices[i];
            }
            else if(prices[i]-buy > max_profit){  //因為不會和if同時發生
                max_profit = prices[i]-buy ;
            }
        }
        return max_profit;
    }
};
```

</details>
