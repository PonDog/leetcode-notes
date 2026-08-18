# Solution 1 ⭐

[← 回到 L125: Valid Palindrome](README.md)

isalnum(string)會回傳boolean，alpha和num才回傳true
tolower(string)會轉小寫

`Time: O(n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        int start = 0;
        int end = s.size()-1;
        while(start <= end){
            if(!isalnum(s[start])){start++; continue;}
            if(!isalnum(s[end])){end--; continue;}
            if(tolower(s[start])!=tolower(s[end]))return false;
            else{
               start++;
               end--;
            }            
        }
        return true;                
    }
};
```

</details>
