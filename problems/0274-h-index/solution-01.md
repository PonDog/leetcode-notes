# Solution 1 ⭐

[← 回到 L274: H-Index](README.md)

`Time:O(nlogn)
Space:O(logn)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int h = 0;
        sort(citations.begin(), citations.end(), greater<int>());
        for(int i = 0; i <= citations.size()-1; i++){
            if(citations[i] >= i+1 ){
                 h = i+1;
            }
            else if(citations[i] < i+1 ){ //也可不另外判斷，讓迴圈跑完再return
                return h = i;
            }        
        }
        return h ;
    }
};

//以下是date2寫的
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int h = 0;
        int n = citations.size();
        sort(citations.begin(), citations.end(),greater<int>());
        while(h < n && citations[h] >= h+1){
            h++;
        }
        return h;
    }
};
```

</details>
