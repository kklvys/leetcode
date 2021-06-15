# 852. 山脉数组的峰顶索引

## 题目

[来源](https://leetcode-cn.com/problems/peak-index-in-a-mountain-array/)

符合下列属性的数组 `arr` 称为 **山脉数组** ：

- `arr.length >= 3`
- 存在 `i`（`0 < i < arr.length - 1`）使得：
  - `arr[0] < arr[1] < ... arr[i-1] < arr[i]`
  - `arr[i] > arr[i+1] > ... > arr[arr.length - 1]`

给你由整数组成的山脉数组 `arr` ，返回任何满足 `arr[0] < arr[1] < ... arr[i - 1] < arr[i] > arr[i + 1] > ... > arr[arr.length - 1]` 的下标 `i` 。

**示例 1：**

```
输入：arr = [0,1,0]
输出：1
```

**示例 2：**

```
输入：arr = [0,2,1,0]
输出：1
```

**示例 3：**

```
输入：arr = [0,10,5,2]
输出：1
```

**示例 4：**

```
输入：arr = [3,4,5,1]
输出：2
```

**示例 5：**

```
输入：arr = [24,69,100,99,79,78,67,36,26,19]
输出：2
```

**提示：**

- `3 <= arr.length <= 10^4`
- `0 <= arr[i] <= 106`

- 题目数据保证 `arr` 是一个山脉数组

**进阶：**很容易想到时间复杂度 `O(n)` 的解决方案，你可以设计一个 `O(log(n))` 的解决方案吗？

## 解题

1. 二分查找

   ```python
   class Solution:
       def peakIndexInMountainArray(self, arr: List[int]) -> int:
           left, right = 1, len(arr) - 2
           i = (left + right) // 2
           while not arr[i - 1] < arr[i] > arr[i + 1]:
               if arr[i - 1] > arr[i]:
                   right = i - 1
               else:
                   left = i + 1
               i = (left + right) // 2
           return i
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注 |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :--- |
   | [通过](https://leetcode-cn.com/submissions/detail/186999359/) | 44 ms    | 15.7 MB  | Python3 | 2021/06/15 23:47 |      |

2. 从中间向两边遍历

   ```python
   class Solution:
       def peakIndexInMountainArray(self, arr: List[int]) -> int:
           i = (len(arr) - 1) // 2
           if arr[i] > arr[i - 1]:
               while i < len(arr) - 2:
                   if arr[i] > arr[i + 1]:
                       break
                   i += 1
           else:
               while i > 0:
                   if arr[i] > arr[i - 1]:
                       break
                   i -= 1
           return i
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/186994570/) | 48 ms    | 15.8 MB  | Python3 | 2021/06/15 23:28 | 添加备注 |

