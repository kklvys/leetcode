# 383. 赎金信

[来源](https://leetcode-cn.com/problems/ransom-note/)

## 题目

给定一个赎金信 (`ransom`) 字符串和一个杂志(`magazine`)字符串，判断第一个字符串 `ransom` 能不能由第二个字符串 `magazines` 里面的字符构成。如果可以构成，返回 `true` ；否则返回 `false`。

(题目说明：为了不暴露赎金信字迹，要从杂志上搜索各个需要的字母，组成单词来表达意思。杂志字符串中的每个字符只能在赎金信字符串中使用一次。)

**示例 1：**

```
输入：ransomNote = "a", magazine = "b"
输出：false
```

**示例 2：**

```
输入：ransomNote = "aa", magazine = "ab"
输出：false
```

**示例 3：**

```
输入：ransomNote = "aa", magazine = "aab"
输出：true
```

**提示：**

- 你可以假设两个字符串均只含有小写字母。

## 解题

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        magazine_letters = {}
        for letter in magazine:
            if letter not in magazine_letters:
                magazine_letters[letter] = 0
            magazine_letters[letter] += 1
        for letter in ransomNote:
            if letter not in magazine_letters:
                return False
            magazine_letters[letter] -= 1
            if magazine_letters[letter] == 0:
                magazine_letters.pop(letter)
        return True
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205129413/) | 68 ms    | 15.1 MB  | Python3 | 2021/08/09 23:18 | 添加备注 |