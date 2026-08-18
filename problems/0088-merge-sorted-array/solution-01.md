# Solution 1

[← 回到 L88: Merge Sorted Array](README.md)

`Time: O(m+n)`

`Space: O(m+n)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n){
        int i = 0;
        int j = 0;
        vector<int> temp;
        
        while(i<m && j<n){
            if(nums1[i] <= nums2[j]){
                temp.push_back(nums1[i++]);
            }
            else if(nums1[i] > nums2[j]){
                temp.push_back(nums2[j++]);
            }
        }
        
        while(j<n){
            temp.push_back(nums2[j++]);
        }
    
        while(i<m){
            temp.push_back(nums1[i++]);
        }
        nums1 = temp;
    }
};
```

</details>
