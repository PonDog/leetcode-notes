# Solution 2 ⭐

[← 回到 L13: Roman to Integer](README.md)

把unordered_map換成寫一個switch function，省O(n)。
語法提醒：switch編譯後會自動轉型整數type來比，可用char，不可用string
case 'I' (o)
case "I" (x) 


`Time:O(n)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
private:
    int integer_sum = 0;
    int map(char c){
        switch(c){
            case 'I' : return 1;
            case 'V' : return 5;
            case 'X' : return 10;
            case 'L' : return 50;
            case 'C' : return 100;
            case 'D' : return 500;
            case 'M' : return 1000;
            default :return 0;
        }
    }

public:
    int romanToInt(string s) {
        if(s.size() >= 2){
            for(int i = 0; i <= s.size()-2; i++){
                if(map(s[i]) >= map(s[i+1])){
                    integer_sum += map(s[i]);   
                }
                else if(map(s[i]) < map(s[i+1])){
                    integer_sum -= map(s[i]);
                }  
            }
        }    
        integer_sum += map(s[s.size()-1]);  
        return integer_sum;       
    }
};

```

</details>
