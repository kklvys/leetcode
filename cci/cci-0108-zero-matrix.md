# 面试题 01.08. 零矩阵

## 题目

[来源](https://leetcode-cn.com/problems/zero-matrix-lcci/)

编写一种算法，若 `M × N` 矩阵中某个元素为 `0`，则将其所在的行与列清零。

**示例 1：**

```
输入：
[
  [1,1,1],
  [1,0,1],
  [1,1,1]
]
输出：
[
  [1,0,1],
  [0,0,0],
  [1,0,1]
]
```

**示例 2：**

```
输入：
[
  [0,1,2,0],
  [3,4,5,2],
  [1,3,1,5]
]
输出：
[
  [0,0,0,0],
  [0,4,5,0],
  [0,3,1,0]
]
```

## 解题

#### Python

1. 先遍历找到需要设置为0的行和列，再遍历设置

   ```python
   class Solution:
       def setZeroes(self, matrix: List[List[int]]) -> None:
           """
           Do not return anything, modify matrix in-place instead.
           """
           zero_rows, zero_columns = {}, {}
           m, n = len(matrix), len(matrix[0])
           i, j = 0, 0
           while i < m:
               j = 0
               while j < n:
                   if matrix[i][j] == 0:
                       zero_rows[i] = True
                       zero_columns[j] = True
                   j += 1
               i += 1
           for row in zero_rows.keys():
               j = 0
               while j < n:
                   matrix[row][j] = 0
                   j += 1
           for column in zero_columns.keys():
               i = 0
               while i < m:
                   matrix[i][column] = 0
                   i += 1
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184340138/) | 48 ms    | 15.1 MB  | Python3 | 2021/06/06 01:55 | 添加备注 |

