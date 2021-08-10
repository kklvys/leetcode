# 19. 删除链表的倒数第 N 个结点

[来源](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/)

## 题目

给你一个链表，删除链表的倒数第 `n` 个结点，并且返回链表的头结点。

**进阶：**你能尝试使用一趟扫描实现吗？

**示例 1：**

![](images/normal-0019-1.jpg)

```
输入：head = [1,2,3,4,5], n = 2
输出：[1,2,3,5]
```

**示例 2：**

```
输入：head = [1], n = 1
输出：[]
```

**示例 3：**

```
输入：head = [1,2], n = 1
输出：[1]
```

**提示：**

- 链表中结点的数目为 `sz`
- `1 <= sz <= 30`
- `0 <= Node.val <= 100`
- `1 <= n <= sz`

## 解题

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        if n == 1 and head.next is None:
            return None

        def remove_node(node):
            if node is None:
                return 0
            num = remove_node(node.next) + 1
            if num == n + 1:
                if node.next is None:
                    node.next = None
                else:
                    node.next = node.next.next
            return num
        
        num = remove_node(head)
        if num == n:
            return head.next
        return head
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/203077186/) | 32 ms    | 15 MB    | Python3 | 2021/08/04 13:47 | 添加备注 |