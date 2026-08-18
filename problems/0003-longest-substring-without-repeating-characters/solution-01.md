# Solution 1

[← 回到 L3: Longest Substring Without Repeating Characters](README.md)

這個解法的思路是以i從左到右遍歷s，每輪固定從i開始以j往右檢查直到有重複為止，
因為ascii範圍0~127，while迴圈檢查時，最多只可能檢查到長度為128，
因此不會到O(n^2)。

`Time: O(n*128)`

`Space: O(128)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int n = s.size();
        int max_length = 0;
        for(int i = 0; i < n; i++){
            vector <int> seen(128,0);
            int j = i;
            while(j < n && !seen[s[j]]){
                max_length = max(max_length,j-i+1);
                seen[s[j++]]++;
            }
        }
        return max_length;        
    }
};
```

</details>
