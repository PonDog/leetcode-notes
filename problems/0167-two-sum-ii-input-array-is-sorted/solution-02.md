# Solution 2

[← 回到 L167: Two Sum II - Input Array Is Sorted](README.md)

這題的關鍵是已排序過，如未排序，要先排序，才能binary＿search和lower_bound，且index會亂掉，建議先存pair再排
依序從頭遍歷numbers，對index j前的值binary＿search找target - numbers[j]
lower_bound回傳iterator，要扣掉numbers.begin()才會變index。
另外還有一種是邊遍歷檢查index j前的hashmap是否已有符合值，邊存hashmap。

`Time: O(nlogn)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int n = numbers.size();
        vector<int> result(2,0);
        for(int j = 1; j < n; j++){
            if(binary_search(numbers.begin(), numbers.begin() + j, target - numbers[j])){
                result[0] = lower_bound(numbers.begin(), numbers.begin() + j, target - numbers[j]) - numbers.begin() + 1;
                result[1] = j + 1;
                break;        
            }    
        }
        return result;    
    }
};
```

</details>
