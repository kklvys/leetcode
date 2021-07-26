# 1893. 检查是否区域内所有整数都被覆盖

[来源](https://leetcode-cn.com/problems/check-if-all-the-integers-in-a-range-are-covered/)

## 题目

给你一个二维整数数组 `ranges` 和两个整数 `left` 和 `right` 。每个 `ranges[i] = [starti, endi]` 表示一个从 `starti` 到 `endi` 的 闭区间 。

如果闭区间 `[left, right]` 内每个整数都被 `ranges` 中 至少一个 区间覆盖，那么请你返回 `true` ，否则返回 `false` 。

已知区间 `ranges[i] = [starti, endi]` ，如果整数 `x` 满足 `starti <= x <= endi` ，那么我们称整数 `x` 被覆盖了。

**示例 1：**

```
输入：ranges = [[1,2],[3,4],[5,6]], left = 2, right = 5
输出：true
解释：2 到 5 的每个整数都被覆盖了：
- 2 被第一个区间覆盖。
- 3 和 4 被第二个区间覆盖。
- 5 被第三个区间覆盖。
```

**示例 2：**

```
输入：ranges = [[1,10],[10,20]], left = 21, right = 21
输出：false
解释：21 没有被任何一个区间覆盖。
```

**提示：**

- `1 <= ranges.length <= 50`
- `1 <= starti <= endi <= 50`
- `1 <= left <= right <= 50`

## 解题

```python
class Solution:
    def isCovered(self, ranges: List[List[int]], left: int, right: int) -> bool:
        covered = [not (left <= i <= right) for i in range(51)]
        for r in ranges:
            for i in range(r[0], r[1] + 1):
                covered[i] = True
        return all(covered)
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/200096944/) | 28 ms    | 15.1 MB  | Python3 | 2021/07/26 22:29 | 添加备注 |