# Solution 1 ⭐

[← 回到 L151: Reverse Words in a String](README.md)

先反轉整個string，再將不是空格的字元依序從頭開始放，將放好的string反轉回來，加一個空格，繼續下一輪，最後再將尾巴resize去掉空格和舊字元。

`Time:O(n)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    string reverseWords(string s) {
        int i = 0;
        int left = 0;
        int right = 0;
        int n =  s.size();
        reverse(s.begin(), s.end());
        while(i < n){
            while(i < n && s[i] == ' ') i++;
            if(i >= n) break;
            while(i < n && s[i] != ' ') {
                s[right++] = s[i++];
            }
            reverse(s.begin()+left,s.begin()+right);
            s[right++] = ' '; 
            left = right; 
            i++;
        }
        s.resize(right - 1);
        return s;
    }
};


```

</details>
