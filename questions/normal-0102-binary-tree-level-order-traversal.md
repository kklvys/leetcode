# 102. 二叉树的层序遍历

[来源](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/)

## 题目

给你一个二叉树，请你返回其按 **层序遍历** 得到的节点值。 （即逐层地，从左到右访问所有节点）。

**示例：**
二叉树：`[3,9,20,null,null,15,7]`,

```
    3
   / \
  9  20
    /  \
   15   7
```

返回其层序遍历结果：

```
[
  [3],
  [9,20],
  [15,7]
]
```

## 解题

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        if root is None:
            return []
        nodes, orders = [root], [[root.val]]
        while len(nodes) > 0:
            temp_nodes, row_orders = [], []
            for node in nodes:
                if node.left is not None:
                    temp_nodes.append(node.left)
                    row_orders.append(node.left.val)
                if node.right is not None:
                    temp_nodes.append(node.right)
                    row_orders.append(node.right.val)
            nodes = temp_nodes
            if len(row_orders) > 0:
                orders.append(row_orders)
        return orders
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205167227/) | 32 ms    | 15.3 MB  | Python3 | 2021/08/10 04:10 | 添加备注 |