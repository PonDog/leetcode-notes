# Solution 1 ⭐

[← 回到 L452: Minimum Number of Arrows to Burst Balloons](README.md)

`Time:O(nlogn)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int findMinArrowShots(vector<vector<int>>& points) {
        int n = points.size();
        int count = 0;
        sort(points.begin(), points.end(),[](const vector<int>& a, const vector<int>& b){
            return a[0] < b[0];
        });

        for(int i = 1; i < n; i++){
            if(points[i-1][1] >= points[i][0]){
                points[i][1] = min(points[i-1][1], points[i][1]);
            }
            else if(points[i-1][1] < points[i][0]){
                count++;
            }
        }
        count++;
        return count;
    }
};
```

</details>
