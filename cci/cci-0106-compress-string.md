# 面试题 01.06. 字符串压缩

## 题目

[来源](https://leetcode-cn.com/problems/compress-string-lcci/)

字符串压缩。利用字符重复出现的次数，编写一种方法，实现基本的字符串压缩功能。比如，字符串 `aabcccccaaa` 会变为 `a2b1c5a3` 。若“压缩”后的字符串没有变短，则返回原先的字符串。你可以假设字符串中只包含大小写英文字母（a至z）。

**示例1:**

```
 输入："aabcccccaaa"
 输出："a2b1c5a3"
```

**示例2:**

```
 输入："abbccd"
 输出："abbccd"
 解释："abbccd"压缩后为"a1b2c2d1"，比原字符串长度更长。
```

**提示：**

1. 字符串长度在 `[0, 50000]` 范围内。

## 解题

#### Python

1. 直接遍历统计即可

   ```python
   class Solution:
       def compressString(self, S: str) -> str:
           result, count = "", 0
           for char in S:
               if result == "":
                   result += char
                   count = 1
               else:
                   if char == result[-1]:
                       count += 1
                   else:
                       result += str(count)
                       result += char
                       count = 1
           if count != 0:
               result += str(count)
           return result if len(result) < len(S) else S
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184315743/) | 64 ms    | 14.8 MB  | Python3 | 2021/06/05 23:00 | 添加备注 |

