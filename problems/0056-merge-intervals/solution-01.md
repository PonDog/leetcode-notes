# Solution 1 ⭐

[← 回到 L56: Merge Intervals](README.md)

`Time:O(nlogn)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        sort(intervals.begin(), intervals.end());
        int n = intervals.size(); 
        auto curr = intervals[0];
        vector<vector<int>> result;
        for(int i = 1; i < n; i++){
            auto next = intervals[i];
            if(curr[1] < next[0]){       //比較前一個元素的尾和後一個元素頭，尾<頭 代表不用合併，此時直接加進result並更新curr。
                result.push_back(curr);
                curr = next;
            }
            else if(curr[1] >= next[0]){ //尾>=頭 代表須合併，合併後的尾要取兩個尾的最大，合併後繼續下輪比較。
                curr[1] = max(curr[1], next[1]);
            }
        } 
        result.push_back(curr);
        return result;           
    }
};

```

</details>
