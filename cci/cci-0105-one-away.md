# 面试题 01.05. 一次编辑

## 题目

[来源](https://leetcode-cn.com/problems/one-away-lcci/)

字符串有三种编辑操作:插入一个字符、删除一个字符或者替换一个字符。 给定两个字符串，编写一个函数判定它们是否只需要一次(或者零次)编辑。

**示例 1:**

```
输入: 
first = "pale"
second = "ple"
输出: True
```

**示例 2:**

```
输入: 
first = "pales"
second = "pal"
输出: False
```

## 解题

#### Python

1. 一次完成只能有三种情况：

   1. 第一个字符串比第二个字符串长，需要插入一个字符
   2. 第一个字符串比第二个字符串短，需要删除一个字符
   3. 第一个字符串与第二个字符串长度相等，需要替换一个字符

   如果字符串长度相差较大，或处理过程中仍有其他字符不同，则不能一次完成

   ```python
   class Solution:
       def oneEditAway(self, first: str, second: str) -> bool:
           # Too long to edit once.
           if abs(len(first) - len(second)) > 1:
               return False
   
           if len(first) > len(second):
               # delete
               i = 0
               deleted = False
               while i < len(first):
                   if deleted:
                       if first[i] != second[i - 1]:
                           return False
                   else:
                       if i < len(second) and first[i] != second[i]:
                           deleted = True
                   i += 1
           elif len(first) < len(second):
               # insert
               i = 0
               inserted = False
               while i < len(second):
                   if inserted:
                       if first[i - 1] != second[i]:
                           return False
                   else:
                       if i < len(first) and first[i] != second[i]:
                           inserted = True
                   i += 1
           else:   
               # replace
               i = 0
               replaced = False
               while i < len(first):
                   if first[i] != second[i]:
                       if replaced:
                           return False
                       else:
                           replaced = True
                   i += 1
           return True
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184219162/) | 44 ms    | 14.6 MB  | Python3 | 2021/06/05 17:00 | 添加备注 |