# Solution 1 ⭐

[← 回到 L290: Word Pattern](README.md)

`Time: O(m)`

`Space: O(n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {    //剛好矇對很不直覺的寫法
public:
    bool wordPattern(string pattern, string s) {
        int n = pattern.size();
        int m = s.size();
        unordered_map<string,string> ps;
        unordered_map<string,string> sp;
        vector<string> sv(n);
        int p = 0;
        int j = 0;

        for(int i = 0; i < n; i++){

            while(j < m && s[j] != ' '){
                j++;
            } 
            for(int k = p ; k < j; k++){
                sv[i] += s[k]; 
            }
            j++;
            p = j;
            string patterns = string(1,pattern[i]);
            if(!ps.count(patterns) && !sp.count(sv[i])){
                ps[patterns] = sv[i];
                sp[sv[i]] = patterns;
            }
            else{
                if(ps[patterns] != sv[i] || sp[sv[i]] != patterns){
                    return false;    
                }
            }
        }    
        return j == m+1;
    }
};

class Solution {
public:
    bool wordPattern(string pattern, string s) {

        // pattern 字元 -> 單字
        unordered_map<char, string> pToWord;

        // 單字 -> pattern 字元
        // 用來確保不同字元不會對應到同一個單字
        unordered_map<string, char> wordToP;

        // 將字串 s 轉成字串串流，方便用空白切割單字
        stringstream ss(s);

        string word;

        // 指向目前處理的 pattern 位置
        int i = 0;

        // 每次從 s 中取出一個單字
        while (ss >> word) {

            // 如果單字數量比 pattern 長度還多
            // 例如 pattern = "ab"
            // s = "dog cat fish"
            if (i == pattern.size()) {
                return false;
            }

            // 取得目前對應的 pattern 字元
            char c = pattern[i];

            if (!pToWord.count(c) && !wordToP.count(word)) {
                pToWord[c] = word;
                wordToP[word] = c;
            }

            else if(pToWord[c] != word || wordToP[word] != c) {
                return false;
            }
            // 處理下一個 pattern 字元
            i++;
        }
        // 檢查 pattern 是否也剛好用完
        // 若 pattern 還有剩餘字元，表示單字數量不足
        // 例如 pattern = "abba"
        // s = "dog cat cat"
        return i == pattern.size();
    }
};
```

</details>
