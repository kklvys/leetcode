# 83. 删除排序链表中的重复元素

[来源](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/)

## 题目

存在一个按升序排列的链表，给你这个链表的头节点 `head` ，请你删除所有重复的元素，使每个元素 **只出现一次** 。

返回同样按升序排列的结果链表。 

**示例 1：**

![img](images/normal-0083-1.jpg)

```
输入：head = [1,1,2]
输出：[1,2]
```

**示例 2：**

![img](images/normal-0083-2.jpg)

```
输入：head = [1,1,2,3,3]
输出：[1,2,3]
```

**提示：**

- 链表中节点数目在范围 `[0, 300]` 内
- `-100 <= Node.val <= 100`
- 题目数据保证链表已经按升序排列

## 解题

```python

添加备注


# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        pre, p, nums = None, head, set()
        while p is not None:
            if p.val in nums:
                pre.next, p = p.next, p.next
            else:
                nums.add(p.val)
                pre, p = p, p.next
        return head
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205162826/) | 36 ms    | 15 MB    | Python3 | 2021/08/10 01:50 | 添加备注 |