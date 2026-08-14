# Solution 1 ⭐

[← 回到 L383: Ransom Note](README.md)

`Time:O(max(m,n))
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {  //版本一
public:
    bool canConstruct(string ransomNote, string magazine) { 
        vector<int> count(26,0);

        for(auto element : magazine){
            count[element -'a']++; 
        }
        for(auto element : ransomNote){
            count[element -'a']--; 
        }
        for(auto element : count){
            if(element < 0) return false; 
        }
        return true;
    }
};

class Solution {  //版本二
public:
    bool canConstruct(string ransomNote, string magazine) { 
        unordered_map<char, int> count;

        for(auto element : magazine){
            count[element]++; 
        }
        for(auto element : ransomNote){
            count[element]--; 
        }
        for(auto element : count){
            if(element.second < 0) return false; 
        }
        return true;
    }
};
```

</details>
