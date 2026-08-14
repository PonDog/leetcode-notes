# Solution 1 ⭐

[← 回到 L134: Gas Station](README.md)

核心想法：
>[!Tip]Greedy:局部選擇是一旦發現從starting_point走到i撐不住，就直接把starting_point改成i+1。
>Proof:
>當s到i這段發現<0，假設存在中間點k當新起點，s到k-1這段必>=0(因s已確認能到起點k，i是第一個發現到不了的點)，
>k到i也因假設而>=0，和s到i這段<0矛盾，因此不存在中間點k可以當新起點。
>或是另一種說法，當s到i這段發現<0，s到k-1這段必>=0，那k到i這段就<<0，油消耗更多更不可能到。
>1. 每次失敗都淘汰一整段不可能起點。
>2. 最後沒被淘汰的只剩下 starting_point 之後那段。
>3. total_gas >= 0 保證全體油量足夠繞一圈。

因此最後保留下來的候選點一定能成功繞完。
`Time:O(n)
Space:O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        int n = gas.size()-1;
        int starting_point = 0;
        int currend_gas = 0;
        int total_gas = 0; 
        for(int i = 0; i <= n; i++) {
            currend_gas += gas[i] - cost[i];
            if(currend_gas < 0){ //這邊會不斷去找相對當前起點的最低點，只要最後total_gas >= 0，就能確定從最低點後下一點當起點出發是最佳
                currend_gas = 0; 
                starting_point = i + 1;    
            }
            total_gas += gas[i] - cost[i];
        }
        return total_gas >= 0 ? starting_point : -1;            
    }
};
```

</details>
