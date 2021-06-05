# 面试题 01.09. 字符串轮转

## 题目

[来源](https://leetcode-cn.com/problems/string-rotation-lcci/)

字符串轮转。给定两个字符串 `s1` 和 `s2`，请编写代码检查 `s2` 是否为 `s1` 旋转而成（比如， `waterbottle `是 `erbottlewat` 旋转后的字符串）。

**示例1:**

```
 输入：s1 = "waterbottle", s2 = "erbottlewat"
 输出：True
```

**示例2:**

```
输入：s1 = "aa", s2 = "aba"
输出：False
```

 **提示：**

1. 字符串长度在 `[0, 100000]` 范围内。

**说明:**

1. 你能只调用一次检查子串的方法吗？

## 解题

#### Python

1. 遍历两个字符串看是否匹配即可

   ```python
   class Solution:
       def isFlipedString(self, s1: str, s2: str) -> bool:
           if s1 == "" and s2 == "":
               return True
           if len(s1) != len(s2):
               return False
           i = 0
           while i < len(s2):
               j, k = i, 0
               while k < len(s1):
                   if s1[k] != s2[j]:
                       break
                   k += 1
                   j = 0 if j == len(s2) - 1 else j + 1
               if k == len(s1):
                   return True
               i += 1
           return False
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184331762/) | 60 ms    | 15 MB    | Python3 | 2021/06/06 00:20 | 添加备注 |

