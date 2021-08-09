# 118. 杨辉三角

[来源](https://leetcode-cn.com/problems/pascals-triangle/)

## 题目

给定一个非负整数 *`numRows`，*生成「杨辉三角」的前 *`numRows`* 行。

在「杨辉三角」中，每个数是它左上方和右上方的数的和。

![img](images/1626927345-DZmfxB-PascalTriangleAnimated2.gif)

 

**示例 1:**

```
输入: numRows = 5
输出: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```

**示例 2:**

```
输入: numRows = 1
输出: [[1]]
```

**提示:**

- `1 <= numRows <= 30`

## 解题

```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        triangle = []
        for i in range(1, numRows + 1):
            if i == 1:
                triangle.append([1])
                continue
            row = [1]
            for j in range(1, i - 1):
                row.append(triangle[i - 2][j - 1] + triangle[i - 2][j])
            row.append(1)
            triangle.append(row)
        return triangle
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205054158/) | 32 ms    | 14.9 MB  | Python3 | 2021/08/09 19:08 | 添加备注 |