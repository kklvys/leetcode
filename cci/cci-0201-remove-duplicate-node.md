# 面试题 02.01. 移除重复节点

## 题目

[来源](https://leetcode-cn.com/problems/remove-duplicate-node-lcci/)

编写代码，移除未排序链表中的重复节点。保留最开始出现的节点。

**示例1:**

```
输入：[1, 2, 3, 3, 2, 1]
输出：[1, 2, 3]
```

**示例2:**

```
输入：[1, 1, 1, 1, 2]
 输出：[1, 2]
```

**提示：**

1. 链表长度在 `[0, 20000]` 范围内。
2. 链表元素在 `[0, 20000]` 范围内。

**进阶：**

- 如果不得使用临时缓冲区，该怎么解决？

## 解题

#### Python

1. 一边遍历一边存储查找字典

   ```python
   # Definition for singly-linked list.
   # class ListNode:
   #     def __init__(self, x):
   #         self.val = x
   #         self.next = None
   
   class Solution:
       def removeDuplicateNodes(self, head: ListNode) -> ListNode:
           if head == None:
               return head
           node_map = {head.val: True}
           pointer, pre_node = head.next, head
           while pointer != None:
               if pointer.val in node_map:
                   pre_node.next = pointer.next
                   pointer = pre_node.next
               else:
                   node_map[pointer.val] = True
                   pre_node, pointer = pointer, pointer.next
           return head
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184353231/) | 68 ms    | 20.3 MB  | Python3 | 2021/06/06 09:39 | 添加备注 |

