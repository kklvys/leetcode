# 566. 重塑矩阵

[来源](https://leetcode-cn.com/problems/reshape-the-matrix/)

## 题目

在 **MATLAB** 中，有一个非常有用的函数 `reshape` ，它可以将一个 `m x n` 矩阵重塑为另一个大小不同（`r x c`）的新矩阵，但保留其原始数据。

给你一个由二维数组 `mat` 表示的 `m x n` 矩阵，以及两个正整数 `r` 和 `c` ，分别表示想要的重构的矩阵的行数和列数。

重构后的矩阵需要将原始矩阵的所有元素以相同的 **行遍历顺序** 填充。

如果具有给定参数的 `reshape` 操作是可行且合理的，则输出新的重塑矩阵；否则，输出原始矩阵。 

**示例 1：**

![img](images/reshape1-grid.jpg)

```
输入：mat = [[1,2],[3,4]], r = 1, c = 4
输出：[[1,2,3,4]]
```

**示例 2：**

![img](images/reshape2-grid.jpg)

```
输入：mat = [[1,2],[3,4]], r = 2, c = 4
输出：[[1,2],[3,4]] 
```

**提示：**

- `m == mat.length`
- `n == mat[i].length`
- `1 <= m, n <= 100`
- `-1000 <= mat[i][j] <= 1000`
- `1 <= r, c <= 300`

## 解题

```python
class Solution:
    def matrixReshape(self, mat: List[List[int]], r: int, c: int) -> List[List[int]]:
        if len(mat) * len(mat[0]) != r * c:
            return mat
        i, j, m, n = 0, 0, 0, 0
        result = []
        while i < len(mat):
            if n == 0:
                result.append([mat[i][j]])
            else:
                result[m].append(mat[i][j])

            n += 1
            if n == c:
                m += 1
                n = 0

            if j == len(mat[0]) - 1:
                j = 0
                i += 1
            else:
                j += 1
        
        return result
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205050748/) | 36 ms    | 15.6 MB  | Python3 | 2021/08/09 18:56 | 添加备注 |