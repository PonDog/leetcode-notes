# Solution 1 ⭐

[← 回到 L12: Integer to Roman](README.md)

沒什麼竅門，全部組合都紀錄下來就對了。
可先用除10的次方，把要確認的位置變到個位上，再用mod取出實際數字來確認要換成哪個Roman。
另外因為是Integer轉Roman，就可以單純用一個陣列來存，不然就要用unordered_map。

`Time: O(1)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    string intToRoman(int num) {
        string A[] = {"","M","MM","MMM"};
        string B[] = {"","C","CC","CCC","CD","D","DC","DCC","DCCC","CM"};
        string C[] = {"","X","XX","XXX","XL","L","LX","LXX","LXXX","XC"};
        string D[] = {"","I","II","III","IV","V","VI","VII","VIII","IX"};
        return A[num/1000]+B[(num/100)%10]+C[(num/10)%10]+D[num%10];
    }
};
```

</details>
