# 二叉树（1）


# 二叉树知识点梳理

如果你正在学习算法与数据结构，那么二叉树肯定是一个非常重要的知识点。在这篇文章中，我将为你梳理二叉树相关的知识点，并提供使用Python3语言解答的示例题目。

## 什么是二叉树？

二叉树是一种树状结构，每个节点最多只有两个子节点，分别为左子节点和右子节点。二叉树有很多种形态，包括平衡二叉树、完全二叉树、满二叉树等等。

## 二叉树的遍历方式

遍历二叉树的方式有三种：前序遍历、中序遍历和后序遍历。其中，前序遍历的顺序是先遍历根节点，然后遍历左子树，最后遍历右子树；中序遍历的顺序是先遍历左子树，然后遍历根节点，最后遍历右子树；后序遍历的顺序是先遍历左子树，然后遍历右子树，最后遍历根节点。

## 二叉树的应用场景

二叉树在很多领域都有着广泛的应用，比如计算机网络中的路由表、文件系统中的文件目录结构、数据库中的索引结构等等。

## 使用Python3解答二叉树相关题目

下面提供两个使用Python3语言解答的二叉树相关题目：

### 题目一：二叉树的最大深度

给定一个二叉树，找出其最大深度。最大深度指的是从根节点到最远叶子节点的最长路径上的节点数。

**示例：**

输入：`root = [3,9,20,null,null,15,7]`
输出：3
<!--more-->
解释：二叉树如下所示：
```markdown
    3
   / \
  9  20
      /  \
   15   7
```

最长路径为 3 → 20 → 7，因此最大深度为 3。

Python3代码如下：
```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1
```

### 题目二：判断二叉树是否对称
给定一个二叉树，检查它是否是镜像对称的。
例如，二叉树 `[1,2,2,3,4,4,3]` 是对称的。
```markdown
      1
     / \
    2   2
   / \ / \
  3  4 4  3
```

但是下面这个 `[1,2,2,null,3,null,3]` 则不是镜像对称的:
```markdown
      1
     / \
    2   2
     \   \
      3   3
```

Python3代码如下：
```python
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        def isMirror(left: Optional[TreeNode], right: Optional[TreeNode]) -> bool:
            if not left and not right:
                return True
            if not left or not right:
                return False
            return (left.val == right.val) and isMirror(left.left, right.right) and isMirror(left.right, right.left)
        if not root:
            return True
        return isMirror(root.left, root.right)
```

## 总结

二叉树是算法与数据结构中非常重要的知识点，它有着广泛的应用场景。在本文中，我们梳理了二叉树的基本概念和遍历方式，并提供了两个使用Python3语言解答的二叉树相关题目。希望本文对大家学习二叉树有所帮助。

