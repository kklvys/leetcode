# 面试题 02.02. 返回倒数第 k 个节点

## 题目

[来源](https://leetcode-cn.com/problems/kth-node-from-end-of-list-lcci/)

实现一种算法，找出单向链表中倒数第 `k` 个节点。返回该节点的值。

**注意：**本题相对原题稍作改动

**示例：**

```
输入： 1->2->3->4->5 和 k = 2
输出： 4
```

**说明：**

给定的 `k` 保证是有效的。

## 解题

#### Python

1. 先遍历生成反向链表，再反向从头查找

   ```python
   # Definition for singly-linked list.
   # class ListNode:
   #     def __init__(self, x):
   #         self.val = x
   #         self.next = None
   
   class Solution:
       def kthToLast(self, head: ListNode, k: int) -> int:
           reverse_head, temp_node = None, None
           pre_node, pointer = None, head
           while pointer is not None:
               temp_node = ListNode(pointer.val)
               temp_node.next = pre_node
               pre_node = temp_node
               pointer = pointer.next
           reverse_head = pre_node
           i = 1
           temp_node = reverse_head
           while i < k:
               temp_node = temp_node.next
               i += 1
           return temp_node.val
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184363098/) | 44 ms    | 14.8 MB  | Python3 | 2021/06/06 10:19 | 添加备注 |

2. 递归，使用全局变量 $i$ 计数，只将倒数第k个节点的值返回回来

   ```python
   # Definition for singly-linked list.
   # class ListNode:
   #     def __init__(self, x):
   #         self.val = x
   #         self.next = None
   
   class Solution:
       def kthToLast(self, head: ListNode, k: int) -> int:
           global i
           if head is None:
               i = 0
               return None
           result = self.kthToLast(head.next, k)
           i += 1
           return head.val if i == k else result
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184372411/) | 40 ms    | 14.9 MB  | Python3 | 2021/06/06 10:44 | 添加备注 |

    

