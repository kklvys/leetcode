# 面试题 01.01. 判定字符是否唯一

## 题目

[来源](https://leetcode-cn.com/problems/is-unique-lcci/)

实现一个算法，确定一个字符串 `s` 的所有字符是否全都不同。

**示例 1：**

```
输入: s = "leetcode"
输出: false 
```

**示例 2：**

```
输入: s = "abc"
输出: true
```

**限制：**

- `0 <= len(s) <= 100`
- 如果你不使用额外的数据结构，会很加分。

## 解题

#### Python

1. 遍历字符串，从字典中查询并将每个字符记录到字典里

   ```python
   class Solution:
       def isUnique(self, astr: str) -> bool:
           char_map = {}
           for char in astr:
               if char in char_map:
                   return False
               char_map[char] = 1
           return True
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184179045/) | 44 ms    | 14.9 MB  | Python3 | 2021/06/05 16:37 | 添加备注 |

2. 

