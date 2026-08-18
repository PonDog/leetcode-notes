# Solution 2

[← 回到 L12: Integer to Roman](README.md)

有點不直覺，比第一種方法慢一點。

`Time: O(1)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    string intToRoman(int num) {
        vector<int> integer = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        vector<string> roman = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        string result;
        int i = 0;
        while(num > 0){
            if(integer[i] <= num){
                result += roman[i];
                num -= integer[i];
            }
            else i++;
        }
        return result;
    }
};
```

</details>
