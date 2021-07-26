# 1736. 替换隐藏数字得到的最晚时间

[来源](https://leetcode-cn.com/problems/latest-time-by-replacing-hidden-digits/)

## 题目

给你一个字符串 `time` ，格式为 `hh:mm`（小时：分钟），其中某几位数字被隐藏（用 `?` 表示）。

有效的时间为 `00:00` 到 `23:59` 之间的所有时间，包括 `00:00` 和 `23:59` 。

替换 `time` 中隐藏的数字，返回你可以得到的最晚有效时间。

**示例 1：**

```
输入：time = "2?:?0"
输出："23:50"
解释：以数字 '2' 开头的最晚一小时是 23 ，以 '0' 结尾的最晚一分钟是 50 。
```

**示例 2：**

```
输入：time = "0?:3?"
输出："09:39"
```

**示例 3：**

```
输入：time = "1?:22"
输出："19:22"
```

**提示：**

- `time` 的格式为 `hh:mm`
- 题目数据保证你可以由输入的字符串生成有效的时间

## 解题

```python
class Solution:
    def maximumTime(self, time: str) -> str:
        result = ['2', '3', '5', '9']
        hour, minute = time.split(':')
        if hour[0] == '?':
            if hour[1] != '?' and int(hour[1]) >= 4:
                result[0] = '1'
        else:
            result[0] = hour[0]
        if hour[1] == '?':
            if result[0] != '2':
                result[1] = '9'
        else:
            result[1] = hour[1]
        result[2] = result[2] if minute[0] == '?' else minute[0]
        result[3] = result[3] if minute[1] == '?' else minute[1]
        result = [result[i] + result[i+1] for i in range(0, len(result), 2)]
        return ':'.join(result)
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/200042393/) | 32 ms    | 15.1 MB  | Python3 | 2021/07/26 20:11 | 添加备注 |