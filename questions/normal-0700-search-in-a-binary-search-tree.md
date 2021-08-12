# 700. 二叉搜索树中的搜索

[来源](https://leetcode-cn.com/problems/search-in-a-binary-search-tree/)

## 题目

给定二叉搜索树（BST）的根节点和一个值。 你需要在BST中找到节点值等于给定值的节点。 返回以该节点为根的子树。 如果节点不存在，则返回 `NULL`。

例如，

```
给定二叉搜索树:

        4
       / \
      2   7
     / \
    1   3

和值: 2
```

你应该返回如下子树:

```
      2     
     / \   
    1   3
```

在上述示例中，如果要找的值是 `5`，但因为没有节点值为 `5`，我们应该返回 `NULL`。

## 解题

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def searchBST(self, root: TreeNode, val: int) -> TreeNode:
        p = root
        while p is not None:
            if val == p.val:
                return p
            elif val < p.val:
                p = p.left
            else:
                p = p.right
        return None
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/205803074/) | 68 ms    | 17 MB    | Python3 | 2021/08/11 17:32 | 添加备注 |
