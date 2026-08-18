# Solution 2 ⭐

[← 回到 L169: Majority Element](README.md)

伊朗戰爭，炮彈對轟抵銷，炮彈多的終會獲勝。

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int candidate = 0;
        int count = 0;
        for(int element:nums){
            if(count == 0){
                candidate = element;
            }
            if(candidate == element){
                count++;
            }
            else{
                count--;
            }
        }
        return candidate;
    }
};
```

</details>
