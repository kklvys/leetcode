# 235. 二叉搜索树的最近公共祖先

[来源](https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

## 题目

给定一个二叉搜索树, 找到该树中两个指定节点的最近公共祖先。

[百度百科](https://baike.baidu.com/item/最近公共祖先/8918834?fr=aladdin)中最近公共祖先的定义为：“对于有根树 T 的两个结点 p、q，最近公共祖先表示为一个结点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大（**一个节点也可以是它自己的祖先**）。”

例如，给定如下二叉搜索树: `root = [6,2,8,0,4,7,9,null,null,3,5]`

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/binarysearchtree_improved.png) 

**示例 1:**

```
输入: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
输出: 6 
解释: 节点 2 和节点 8 的最近公共祖先是 6。
```

**示例 2:**

```
输入: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
输出: 2
解释: 节点 2 和节点 4 的最近公共祖先是 2, 因为根据定义最近公共祖先节点可以为节点本身。
```

**说明:**

- 所有节点的值都是唯一的。
- p、q 为不同节点且均存在于给定的二叉搜索树中。

## 解题

1. 找到节点的所有祖先，再找第一个公共父节点。

   ```python
   # Definition for a binary tree node.
   # class TreeNode:
   #     def __init__(self, x):
   #         self.val = x
   #         self.left = None
   #         self.right = None
   
   class Solution:
       def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
           p_parents = [p]
           q_parents = [q]
           def children(node: 'TreeNode', target: 'TreeNode', parents):
               if node is None:
                   return None
               if node == target:
                   return node
               left = children(node.left, target, parents)
               if left is not None:
                   parents.append(node)
                   return node
               right = children(node.right, target, parents)
               if right is not None:
                   parents.append(node)
                   return node
               return None
           children(root, p, p_parents)
           children(root, q, q_parents)
           i = 1
           while i <= len(p_parents) and i <= len(q_parents):
               if p_parents[-i] != q_parents[-i]:
                   break
               i += 1
           return p_parents[-(i-1)]
   ```

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/206444111/) | 96 ms    | 18.9 MB  | Python3 | 2021/08/13 11:27 | 添加备注 |

2. 111