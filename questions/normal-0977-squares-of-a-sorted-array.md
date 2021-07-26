# 977. 有序数组的平方

[来源](https://leetcode-cn.com/problems/squares-of-a-sorted-array/)

## 题目

给你一个按 **非递减顺序** 排序的整数数组 `nums`，返回 **每个数字的平方** 组成的新数组，要求也按 **非递减顺序** 排序。

**示例 1：**

```
输入：nums = [-4,-1,0,3,10]
输出：[0,1,9,16,100]
解释：平方后，数组变为 [16,1,0,9,100]
排序后，数组变为 [0,1,9,16,100]
```

**示例 2：**

```
输入：nums = [-7,-3,2,3,11]
输出：[4,9,9,49,121]
```

**提示：**

- $1 <= nums.length <= 10^4$
- $-10^4 <= nums[i] <= 10^4$
- `nums` 已按 **非递减顺序** 排序

**进阶：**

- 请你设计时间复杂度为 `O(n)` 的算法解决本问题

## 解题

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        middle = -1
        for i in range(len(nums)):
            if nums[i] >= 0:
                middle = i
                break
        if middle == 0:
            return [num ** 2 for num in nums]
        if middle == -1:
            return [num ** 2 for num in nums][::-1]
        left, right = middle - 1, middle
        result = []
        while left >= 0 or right < len(nums):
            if left >= 0 and right < len(nums):
                left_square, right_square = nums[left] ** 2, nums[right] ** 2
                if left_square < right_square:
                    result.append(left_square)
                    left -= 1
                else:
                    result.append(right_square)
                    right += 1
            elif right < len(nums):
                result.append(nums[right] ** 2)
                right += 1
            else:
                result.append(nums[left] ** 2)
                left -= 1
        return result
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/200121008/) | 112 ms   | 16.4 MB  | Python3 | 2021/07/26 23:27 | 添加备注 |