# Solution 1

[← 回到 L13: Roman to Integer](README.md)

這邊題目沒提到的是位數越多的羅馬字組會出現在越前面
這邊一次看兩個elements時有兩種選擇，
1.操作左邊element:我第一直覺想到的方法，因為先看到右邊element，就能確定左邊element要＋還-。
2.操作右邊element:解答提供的另一種方法，有點像假設都先加，
但因為右邊element的右邊還沒看到，所以其實要下一回才能真的確認要＋還-，加的同時會需要補救上一回的＋(-兩遍)，
有點不直覺。

`Time:O(n)
Space:O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
private:
    vector<char> roman = {'I', 'V', 'X', 'L', 'C', 'D', 'M'};  
    vector<int> integer = {1, 5, 10, 50, 100, 500, 1000};
    unordered_map<char,int> m;    
public:
    int romanToInt(string s) {
        int sum = 0;
        for(int i = 0; i < roman.size(); i++){
            m[roman[i]] = integer[i];
        }  
        for(int i = 0; i < s.size()-1; i++){
            if(m[s[i]] >= m[s[i+1]]){
                sum += m[s[i]];    
            }
            else if(m[s[i]] < m[s[i+1]]){
            sum -= m[s[i]]; 
            }    
        }
        sum += m[s[s.size()-1]];
        return sum;            
    }
};
```

</details>
