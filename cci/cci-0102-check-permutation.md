# 面试题 01.02. 判定是否互为字符重排

## 题目

[来源](https://leetcode-cn.com/problems/check-permutation-lcci/)

给定两个字符串 `s1` 和 `s2`，请编写一个程序，确定其中一个字符串的字符重新排列后，能否变成另一个字符串。

**示例 1：**

```
输入: s1 = "abc", s2 = "bca"
输出: true 
```

**示例 2：**

```
输入: s1 = "abc", s2 = "bad"
输出: false
```

**说明：**

- `0 <= len(s1) <= 100`
- `0 <= len(s2) <= 100`

## 解题

#### Python

1. 遍历并记录每一个字符存在的次数，对比如果两个字典完全相同，则一个字符串重新排列后可以变成另一个字符串

   ```python
   class Solution:
       def CheckPermutation(self, s1: str, s2: str) -> bool:
           if len(s1) != len(s2):
               return False
           s1_map = {}
           for c1 in s1:
               s1_map[c1] = s1_map.get(c1, 0) + 1
           s2_map = {}
           for c2 in s2:
               s2_map[c2] = s2_map.get(c2, 0) + 1
           for key, value in s1_map.items():
               if s2_map.get(key, 0) != value:
                   return False
           return True
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184187736/) | 44 ms    | 15 MB    | Python3 | 2021/06/05 16:44 | 添加备注 |

2. 