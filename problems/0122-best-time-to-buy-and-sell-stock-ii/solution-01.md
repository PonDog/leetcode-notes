# Solution 1

[← 回到 L122: Best Time to Buy and Sell Stock II](README.md)

`can sell and buy the stock multiple times on the same day`是關鍵，
觀察[7,1,5,3,6,4]，只要從左到右遍歷相鄰兩元素能拿到的profit都能加到max_profit中。
>[!Tip]Greedy
>
`Time:O(n)
Space:O(1)`
<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices){
        int buy = prices[0]; 
        //其實可以不用維護buy，用price[i-1]當buy和price[i]比就行
        int max_profit = 0;
        
        for(int element: prices){
            if(element > buy){
                max_profit += element - buy;
            }
            buy = element;    
        }
        return max_profit;  
    }
};
```

</details>
