# 145. 二叉树的后序遍历

[来源](https://leetcode-cn.com/problems/binary-tree-postorder-traversal/)

## 题目

给定一个二叉树，返回它的 *后序* 遍历。

**示例:**

```
输入: [1,null,2,3]  
   1
    \
     2
    /
   3 

输出: [3,2,1]
```

**进阶:** 递归算法很简单，你可以通过迭代算法完成吗？

## 解题

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        traversal = []
        if root is None:
            return traversal
        if root.left is not None:
            traversal.extend(self.postorderTraversal(root.left))
        if root.right is not None:
            traversal.extend(self.postorderTraversal(root.right))
        traversal.append(root.val)
        return traversal
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205166477/) | 28 ms    | 15.1 MB  | Python3 | 2021/08/10 03:27 | 添加备注 |