# 20. 有效的括号

[来源](https://leetcode-cn.com/problems/valid-parentheses/)

## 题目

给定一个只包括 `'('`，`')'`，`'{'`，`'}'`，`'['`，`']'` 的字符串 `s` ，判断字符串是否有效。

有效字符串需满足：

1. 左括号必须用相同类型的右括号闭合。
2. 左括号必须以正确的顺序闭合。

**示例 1：**

```
输入：s = "()"
输出：true
```

**示例 2：**

```
输入：s = "()[]{}"
输出：true
```

**示例 3：**

```
输入：s = "(]"
输出：false
```

**示例 4：**

```
输入：s = "([)]"
输出：false
```

**示例 5：**

```
输入：s = "{[]}"
输出：true
```

**提示：**

- `1 <= s.length <= 104`
- `s` 仅由括号 `'()[]{}'` 组成

## 解题

```python
class Solution:
    def isValid(self, s: str) -> bool:
        symbol_stack = []
        for symbol in s:
            if symbol in '({[':
                symbol_stack.append(symbol)
            else:
                if len(symbol_stack) > 0 and \
                    ((symbol_stack[-1] == '(' and symbol == ')') or \
                    (symbol_stack[-1] == '{' and symbol == '}') or \
                    (symbol_stack[-1] == '[' and symbol == ']')):
                    symbol_stack.pop()
                else:
                    return False
        return len(symbol_stack) == 0
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205163920/) | 36 ms    | 15.1 MB  | Python3 | 2021/08/10 02:06 | 添加备注 |