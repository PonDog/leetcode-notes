# Solution 1

[← 回到 L14: Longest Common Prefix](README.md)

`Time:O(nlogn+n*m)
Space:O(logn)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        string prefix =  "" ;
        int i = 0;
        sort(strs.begin(), strs.end(), [](string a, string b){
            return a.size() < b.size();
        });

        for(int i = 0; i < strs[0].size(); i++){
            int count = 0;
            for(int j = 0; j < strs.size(); j++){
                if(strs[0][i] == strs[j][i])
                count++;
            }
            if(count == strs.size()){
                prefix += strs[0][i];
            }
            else break;               
        }
        return prefix;
    }
};

```

</details>
