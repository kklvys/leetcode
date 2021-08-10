# 144. 二叉树的前序遍历

[来源](https://leetcode-cn.com/problems/binary-tree-preorder-traversal/)

## 题目

给你二叉树的根节点 `root` ，返回它节点值的 **前序** 遍历。

**示例 1：**

![img](images/normal-0144-1.jpg)

```
输入：root = [1,null,2,3]
输出：[1,2,3]
```

**示例 2：**

```
输入：root = []
输出：[]
```

**示例 3：**

```
输入：root = [1]
输出：[1]
```

**示例 4：**

![img](images/normal-0144-2.jpg)

```
输入：root = [1,2]
输出：[1,2]
```

**示例 5：**

![img](images/normal-0144-3.jpg)

```
输入：root = [1,null,2]
输出：[1,2]
```

**提示：**

- 树中节点数目在范围 `[0, 100]` 内
- `-100 <= Node.val <= 100`

**进阶：**递归算法很简单，你可以通过迭代算法完成吗？

## 解题

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        traversal = []
        if root is None:
            return traversal
        traversal.append(root.val)
        if root.left is not None:
            traversal.extend(self.preorderTraversal(root.left))
        if root.right is not None:
            traversal.extend(self.preorderTraversal(root.right))
        return traversal
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205166447/) | 32 ms    | 14.9 MB  | Python3 | 2021/08/10 03:25 | 添加备注 |