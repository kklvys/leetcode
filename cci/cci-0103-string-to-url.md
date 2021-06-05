# 面试题 01.03. URL化

## 题目

[来源](https://leetcode-cn.com/problems/string-to-url-lcci/)

URL化。编写一种方法，将字符串中的空格全部替换为 `%20` 。假定该字符串尾部有足够的空间存放新增字符，并且知道字符串的“真实”长度。（注：用 `Java` 实现的话，请使用字符数组实现，以便直接在数组上操作。）

 **示例 1：**

```
输入："Mr John Smith    ", 13
输出："Mr%20John%20Smith"
```

**示例 2：**

```
输入："               ", 5
输出："%20%20%20%20%20"
```

**提示：**

- 字符串长度在 `[0, 500000]` 范围内。

## 解题

#### Python

1. 新建一个字符串，遍历，如果是空格就进行替换，否则仍使用原来的字符。如果真实字符串长度更大，则在末尾补上URL化后的空格

   ```python
   class Solution:
       def replaceSpaces(self, S: str, length: int) -> str:
           i = 0
           result = ""
           while i < length:
               if i < len(S):
                   result += S[i] if S[i] != " " else "%20"
               else:
                   result += "%20"
               i += 1
           return result
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184190856/) | 240 ms   | 20.3 MB  | Python3 | 2021/06/05 16:49 | 添加备注 |