# Solution 1 ⭐

[← 回到 L202: Happy Number](README.md)

`Time: O(logn) 位數＊會出現的值可能有幾個（會有一個固定最大範圍）`

`Space: O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    bool isHappy(int n) {
        unordered_set<int> s;
        while(!s.count(n)){
            s.insert(n);
            int sum = 0;
            while(n != 0){
                int num = n % 10;
                n = n / 10;
                sum += num * num;         
            }
            if(sum == 1) return true;
            n = sum;
        }
        return false;
    }
};



```

</details>
