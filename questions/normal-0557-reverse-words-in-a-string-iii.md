# 557. 反转字符串中的单词 III

[来源](https://leetcode-cn.com/problems/reverse-words-in-a-string-iii/)

## 题目

给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。

**示例：**

```
输入："Let's take LeetCode contest"
输出："s'teL ekat edoCteeL tsetnoc"
```

**提示：**

- 在字符串中，每个单词由单个空格分隔，并且字符串中不会有任何额外的空格。

## 解题

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return " ".join([word[::-1] for word in s.split()])
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/203063840/) | 36 ms    | 15.5 MB  | Python3 | 2021/08/04 11:52 | 添加备注 |

