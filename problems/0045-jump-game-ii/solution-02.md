# Solution 2 ⭐

[← 回到 L45: Jump Game II](README.md)

核心想法：只記範圍，不記實際落點，挺抽象的，還沒很懂。
同一層內的所有位置，本來就是同樣跳數可達，
所以在這一層裡，選能讓下一層最遠的那個方向，一定不吃虧。
同樣跳數可到達的所有位置，可以視為同一層；而求最少跳數，就是看要擴幾層才能碰到終點。
>[!Tip]由BFS簡化成Greedy
>

`Time: O(n^2)`

`Space: O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int jump(vector<int>& nums) {
        int jumps = 0, currentEnd = 0, farthest = 0;
        //jumps為總跳數
        //currentEnd為當前最遠能跳到哪個index
        //farthest紀錄以index到currentEnd的範圍內做跳板，最遠能跳到哪，用來更新currentEnd
        for (int i = 0; i <= nums.size() - 2; i++) { //last element不需算
            farthest = max(farthest, i + nums[i]);
            if (i == currentEnd) { //評估範圍從i到currentEnd
                jumps++;
                currentEnd = farthest;
            }
        }
        return jumps;
    }
};
```

</details>
