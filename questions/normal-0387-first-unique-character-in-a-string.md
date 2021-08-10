# 387. 字符串中的第一个唯一字符

[来源](https://leetcode-cn.com/problems/first-unique-character-in-a-string/)

## 标题

给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。

 **示例：**

```
s = "leetcode"
返回 0

s = "loveleetcode"
返回 2
```

**提示：**你可以假定该字符串只包含小写字母。

## 解题

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        letters = {}
        for i in range(len(s)):
            if s[i] not in letters:
                letters[s[i]] = i
            else:
                letters[s[i]] = -1
        for index in letters.values():
            if index != -1:
                return index
        return -1
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205127564/) | 88 ms    | 15.1 MB  | Python3 | 2021/08/09 23:14 | 添加备注 |
