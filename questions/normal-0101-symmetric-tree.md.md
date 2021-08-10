# 101. 对称二叉树

[来源](https://leetcode-cn.com/problems/symmetric-tree/)

## 题目

给定一个二叉树，检查它是否是镜像对称的。

例如，二叉树 `[1,2,2,3,4,4,3]` 是对称的。

```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

但是下面这个 `[1,2,2,null,3,null,3]` 则不是镜像对称的:

```
    1
   / \
  2   2
   \   \
   3    3
```

**进阶：**

你可以运用递归和迭代两种方法解决这个问题吗？

## 解题

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        nodes = [root]
        while len(nodes) > 0:
            temp_nodes = []
            for node in nodes:
                if node is not None:
                    temp_nodes.extend([node.left, node.right])
                else:
                    temp_nodes.extend([None, None])
            for i in range(len(temp_nodes) // 2):
                if temp_nodes[i] is not None and \
                    temp_nodes[-(i+1)] is not None and \
                    temp_nodes[i].val == temp_nodes[-(i+1)].val:
                    continue
                if temp_nodes[i] is None and \
                    temp_nodes[-(i+1)] is None:
                    continue
                return False
            if any(temp_nodes):
                nodes = temp_nodes
            else:
                nodes = []
        return True
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205167145/) | 872 ms   | 77.2 MB  | Python3 | 2021/08/10 04:04 | 添加备注 |