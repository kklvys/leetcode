# 653. 两数之和 IV - 输入 BST

[来源](https://leetcode-cn.com/problems/two-sum-iv-input-is-a-bst/)

## 题目

给定一个二叉搜索树 `root` 和一个目标结果 `k`，如果 BST 中存在两个元素且它们的和等于给定的目标结果，则返回 `true`。

**示例 1：**

![img](images/normal-0653-1.jpg)

```
输入: root = [5,3,6,2,4,null,7], k = 9
输出: true
```

**示例 2：**

![img](images/normal-0653-2.jpg)

```
输入: root = [5,3,6,2,4,null,7], k = 28
输出: false
```

**示例 3：**

```
输入: root = [2,1,3], k = 4
输出: true
```

**示例 4：**

```
输入: root = [2,1,3], k = 1
输出: false
```

**示例 5：**

```
输入: root = [2,1,3], k = 3
输出: true
```

**提示:**

- 二叉树的节点个数的范围是 `[1, 104]`.
- `-104 <= Node.val <= 104`
- `root` 为二叉搜索树
- `-105 <= k <= 105`

## 解题

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def findTarget(self, root: TreeNode, k: int) -> bool:
        sorts = []
        def traverse(node: TreeNode):
            if node is None:
                return
            traverse(node.left)
            sorts.append(node.val)
            traverse(node.right)
        traverse(root)
        i, j = 0, len(sorts) - 1
        while i < j:
            if sorts[i] + sorts[j] == k:
                return True
            elif sorts[i] + sorts[j] > k:
                j -= 1
            else:
                i += 1
        return False
```

| 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
| :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
| [通过](https://leetcode-cn.com/submissions/detail/206381717/) | 80 ms    | 21.1 MB  | Python3 | 2021/08/13 08:49 | 添加备注 |