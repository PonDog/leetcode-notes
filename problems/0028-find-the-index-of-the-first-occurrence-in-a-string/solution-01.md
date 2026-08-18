# Solution 1 ⭐

[← 回到 L28: Find the Index of the First Occurrence in a String](README.md)

先確保haystack還有足夠長度可和needle比的同時，haystack從頭依序當index和needle比是否相同，直到找到就return index。

`Time: O(n*h)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int index = 0;
    int strStr(string haystack, string needle) {
        int n = needle.size(); 
        int h = haystack.size();  
        while(h-index >= n){
            int count = 0;
            while(haystack[index + count] == needle[count] && count < n){
                count++;    
            }
            if(count == n) return index;
            else index++;    
        }
        return -1;    
    }
};
```

</details>
