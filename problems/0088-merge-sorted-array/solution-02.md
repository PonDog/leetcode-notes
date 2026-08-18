# Solution 2 ⭐

[← 回到 L88: Merge Sorted Array](README.md)

three pointers，從最大的開始比，大的放nums1

`Time: O(m+n)`

`Space: O(1)`

<details>
<summary>展開程式碼</summary>

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n){
        int i = m-1;
        int j = n-1;
        int p = m+n-1;

        while(i>=0 && j>=0){
            if(nums1[i] > nums2[j]){
                nums1[p--] = nums1[i--];
            }
            else if(nums1[i] <= nums2[j]){
                nums1[p--] = nums2[j--];
            }
        }
        while(j>=0){
            nums1[p--] = nums2[j--];
        }
    }
};

//另一種超精簡寫法
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int index = m + n - 1;
        int i = m - 1;
        int j = n - 1;
        while(i>=0 && j>=0){
           nums1[index--] = nums1[i] >= nums2[j]? nums1[i--] : nums2[j--]; 
        }
        while(j>=0){
            nums1[index--] = nums2[j--];    
        }  
    }
};
```

</details>
