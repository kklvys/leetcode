# 21. 合并两个有序链表

[来源](https://leetcode-cn.com/problems/merge-two-sorted-lists/)

## 题目

将两个升序链表合并为一个新的 **升序** 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

**示例 1：**

![img](images/normal-0021-1.jpg)

```
输入：l1 = [1,2,4], l2 = [1,3,4]
输出：[1,1,2,3,4,4]
```

**示例 2：**

```
输入：l1 = [], l2 = []
输出：[]
```

**示例 3：**

```
输入：l1 = [], l2 = [0]
输出：[0]
```

**提示：**

- 两个链表的节点数目范围是 `[0, 50]`
- `-100 <= Node.val <= 100`
- `l1` 和 `l2` 均按 **非递减顺序** 排列

## 解题

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        p1, p2 = l1, l2
        head, p = None, None
        while any([p1, p2]):
            if head is None:
                if p1 is not None and p2 is not None:
                    if p1.val < p2.val:
                        head, p = p1, p1
                        p1 = p1.next
                    else:
                        head, p = p2, p2
                        p2 = p2.next
                elif p1 is not None:
                    head, p = p1, p1
                    p1 = p1.next
                else:
                    head, p = p2, p2
                    p2 = p2.next
            else:
                if p1 is not None and p2 is not None:
                    if p1.val < p2.val:
                        p.next = p1
                        p = p.next
                        p1 = p1.next
                    else:
                        p.next = p2
                        p = p.next
                        p2 = p2.next
                elif p1 is not None:
                    p.next = p1
                    p = p.next
                    p1 = p1.next
                else:
                    p.next = p2
                    p = p.next
                    p2 = p2.next
        return head
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205135219/) | 40 ms    | 15.1 MB  | Python3 | 2021/08/09 23:33 | 添加备注 |