# 242. 有效的字母异位词

[来源](https://leetcode-cn.com/problems/valid-anagram/)

## 题目

给定两个字符串 `s` 和 `t` ，编写一个函数来判断 `t` 是否是 `s` 的字母异位词。

**注意：**若 `s` 和 `t` 中每个字符出现的次数都相同，则称 `s` 和 `t` 互为字母异位词。

**示例 1:**

```
输入: s = "anagram", t = "nagaram"
输出: true
```

**示例 2:**

```
输入: s = "rat", t = "car"
输出: false
```

 **提示:**

- `1 <= s.length, t.length <= 5 * 104`
- `s` 和 `t` 仅包含小写字母

**进阶:** 如果输入字符串包含 unicode 字符怎么办？你能否调整你的解法来应对这种情况？

## 解题

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        letters = {}
        for letter in s:
            if letter not in letters:
                letters[letter] = 0
            letters[letter] += 1
        for letter in t:
            if letter not in letters:
                return False
            letters[letter] -= 1
            if letters[letter] == 0:
                letters.pop(letter)
        if len(letters) > 0:
            return False
        return True
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205122705/) | 48 ms    | 15.3 MB  | Python3 | 2021/08/09 23:04 | 添加备注 |