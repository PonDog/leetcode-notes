# Solution 1

[← 回到 L45: Jump Game II](README.md)

自己想的DP方法，雖然時間跟垃圾一樣，但能解出來已經有進步了。

`Time: O(n^2)`

`Space: O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int jump(vector<int>& nums) {
        vector<int> min_step(nums.size(),nums.size());
        min_step[0] = 0;
        //min_step[i]為由開頭到i所用最短步數
        //min_step[i]需考慮可到達i的min_step[0~i-1]+1哪個最小
        for(int i = 0; i <= nums.size()-1; i++){
            for(int j = 0; j < i; j++){  
                if(nums[j] >= i-j  && min_step[i] > min_step[j]+1){
                    min_step[i] =  min_step[j]+1;     
                }
            } 
        }
        return min_step[nums.size()-1];
    }
};
```

</details>
