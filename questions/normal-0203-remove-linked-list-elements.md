# 203. 移除链表元素
### 题目

[来源](https://leetcode-cn.com/problems/remove-linked-list-elements)

给你一个链表的头节点 `head` 和一个整数 `val` ，请你删除链表中所有满足 `Node.val == val` 的节点，并返回 **新的头节点** 。

![img](images/normal-0203-remove-linked-list-elements.jpg)

**示例 1：**

```
输入：head = [1,2,6,3,4,5,6], val = 6
输出：[1,2,3,4,5]
```

**示例 2：**

```
输入：head = [], val = 1
输出：[]
```

**示例 3：**

```
输入：head = [7,7,7,7], val = 7
输出：[]
```

**提示：**

- 列表中的节点在范围 `[0, 104]` 内
- `1 <= Node.val <= 50`
- `0 <= k <= 50`

### 解题

#### Python

1. 遍历并把每一个节点存入列表中，占用多余空间，但查找更快。

   ```python
   # Definition for singly-linked list.
   # class ListNode:
   #     def __init__(self, val=0, next=None):
   #         self.val = val
   #         self.next = next
   class Solution:
       def removeElements(self, head: ListNode, val: int) -> ListNode:
           if head is None:
               return None
   
           nodes = []
           next = head
           pre = None
   
           while next is not None:
               if next.val == val:
                   next = next.next
                   if pre is not None:
                       pre.next = next
               else:
                   nodes.append(next)
                   pre = next
                   next = next.next
           
           if len(nodes) == 0:
               return None
           
           return nodes[0]
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注 |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :--- |
   | [通过](https://leetcode-cn.com/submissions/detail/184100312/) | 72 ms    | 17.9 MB  | Python3 | 2021/06/05 02:16 |      |

2. 递归