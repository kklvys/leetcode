# 面试题 02.03. 删除中间节点

## 题目

[来源](https://leetcode-cn.com/problems/delete-middle-node-lcci/)

若链表中的某个节点，既不是链表头节点，也不是链表尾节点，则称其为该链表的「中间节点」。

假定已知链表的某一个中间节点，请实现一种算法，将该节点从链表中删除。

例如，传入节点 `c`（位于单向链表 `a->b->c->d->e->f` 中），将其删除后，剩余链表为 `a->b->d->e->f`

**示例：**

```
输入：节点 5 （位于单向链表 4->5->1->9 中）
输出：不返回任何数据，从链表中删除传入的节点 5，使链表变为 4->1->9
```

## 解题

#### Python

1. 直接在当前节点上修改即可

   ```python
   # Definition for singly-linked list.
   # class ListNode:
   #     def __init__(self, x):
   #         self.val = x
   #         self.next = None
   
   class Solution:
       def deleteNode(self, node):
           """
           :type node: ListNode
           :rtype: void Do not return anything, modify node in-place instead.
           """
           node.val = node.next.val
           node.next = node.next.next
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184383619/) | 44 ms    | 15 MB    | Python3 | 2021/06/06 11:08 | 添加备注 |

