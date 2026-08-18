# Solution 1

[← 回到 L167: Two Sum II - Input Array Is Sorted](README.md)

我的暴力TlE垃圾。

`Time: O(n^2)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target){
        vector<int> result(2,0);
        int i = 0;
        int j = i + 1;
        int n = numbers.size();
        bool found = false; 
            while(i < n && j < n){
                while(j < n && numbers[i] + numbers[j] <= target){
                    if(numbers[i] + numbers[j] == target){
                        result[0] = i + 1;
                        result[1] = j + 1;
                        found = true;
                        break;
                    }
                    j++;
                }
                if(found) break;
                i++;
                j = i + 1;
            }    
        return result;        
    }
};
```

</details>
