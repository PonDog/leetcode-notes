# L238: Product of Array Except Self

[← 回到題庫首頁](../../README.md)

- 難度：Medium
- 題型：Array

## 原始題目筆記

核心想法：觀察每次取到的元素有一部份重複，以當前i分左右半邊，用紀錄prefix和postfix的方式讓每次取相乘元素從O(n)降到O(1)
，因為可以拿之前算過的prefix和postfix乘上一個新元素就能得到下一個prefix和postfix。
從左往右掃，先紀錄每個prefix到answer，再從右往左掃依序算出postfix紀錄在nums並和answer紀錄的prefix相乘出答案。

## Solutions

- [Solution 1 ⭐](solution-01.md)
