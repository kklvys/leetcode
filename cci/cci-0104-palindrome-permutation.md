# 面试题 01.04. 回文排列

## 题目

[来源](https://leetcode-cn.com/problems/palindrome-permutation-lcci/)

给定一个字符串，编写一个函数判定其是否为某个回文串的排列之一。

回文串是指正反两个方向都一样的单词或短语。排列是指字母的重新排列。

回文串不一定是字典当中的单词。 

**示例1：**

```
输入："tactcoa"
输出：true（排列有"tacocat"、"atcocta"，等等）
```

## 解题

#### Python

1. 遍历并记录每个字母出现的次数，奇次出现的字母最多只能有一个。

   ```python
   class Solution:
       def canPermutePalindrome(self, s: str) -> bool:
           char_map = {}
           for char in s:
               char_map[char] = char_map.get(char, 0) + 1
           has_singular = False
           for value in char_map.values():
               if value % 2 != 0:
                   if has_singular:
                       return False
                   else:
                       has_singular = True
           return True
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184197002/) | 36 ms    | 14.8 MB  | Python3 | 2021/06/05 16:52 | 添加备注 |

