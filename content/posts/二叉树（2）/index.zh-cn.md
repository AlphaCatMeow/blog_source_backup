---
title: "二叉树（2）"
subtitle: "从简单题目开始刷起"
date: 2023-03-12T10:53:12+08:00
lastmod: 2023-03-12T10:53:12+08:00
draft: false
author: "Jason"
authorLink: "https://alphacat.fun"
description: ""
license: ""
images: []

tags: ['算法与数据结构']
categories: ['算法与数据结构']

featuredImage: ""
featuredImagePreview: ""

hiddenFromHomePage: false
hiddenFromSearch: false
twemoji: false
lightgallery: true
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: true
rssFullText: false

toc:
  enable: true
  auto: true
code:
  copy: true
  maxShownLines: 50
math:
  enable: true
  # ...
mapbox:
  # ...
share:
  enable: true
  # ...
comment:
  enable: true
  # ...
library:
  css:
    # someCSS = "some.css"
    # located in "assets/"
    # Or
    # someCSS = "https://cdn.example.com/some.css"
  js:
    # someJS = "some.js"
    # located in "assets/"
    # Or
    # someJS = "https://cdn.example.com/some.js"
seo:
  images: []
  # ...
---
# 算法学习先从简单题目开始刷起
算法学习，我个人认为建立学习的兴趣和信心最重要，所以先从简单题开始刷起，而越是简单的题目就越能直戳算法题目的本质，直指核心要点，只有这样才能快速培养起来我们对于算法问题的本质的熟悉度，这样看到中等难度或者高难度的题目也能很快分析出这道题目的本质考点，才能有思路解决问题，当一道题有了思路，剩下的就是代码的编写和堆砌了，这一部分考验的是对编程语言的熟悉程度，因此也要求我们对于用来解答问题使用的编程语言也要非常熟悉才行，这就需要大量的使用和练习了。
## 简单题目先从二叉树开始刷起
为什么这么说，因为二叉树算是数据结构以及算法最基本的最容易解答的一类题目了，其他的N叉树，也是从二叉树基础上进行扩展而来，用来入门和练手一定是最适合的题目类型了。

### [第一题.力扣104.二叉树的最大深度](https://leetcode.cn/problems/maximum-depth-of-binary-tree/)
给定一个二叉树，找出其最大深度。
二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。
**说明:** 叶子节点是指没有子节点的节点。
**示例：**
给定二叉树 `[3,9,20,null,null,15,7]`，
```MarkDown
    3
   / \
  9  20
     /  \
   15   7
```
返回它的最大深度 3 。
**解题思路**
-   [深度优先搜索（Depth First Search）](http://data.biancheng.net/view/325.html)
-   找出终止条件：当前节点为空
-   找出返回值：节点为空时说明高度为0，所以返回0，节点不为空时则分别求左右子树的高度的最大值，同时加1表示当前节点的高度，返回该数值
-   某层的执行过程：在返回值部分基本已经描述清楚
-   时间复杂度：O(n)
<!--more-->
**题解(Python)：**
```Python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root: return 0
        L = self.maxDepth(root.left)
        R = self.maxDepth(root.right)
        
        return max(L, R) + 1
```

### [第二题.力扣144.二叉树的前序遍历](https://leetcode.cn/problems/binary-tree-preorder-traversal/)
输入：`root = [1,2]` 输出：`[1,2]`
**示例：**
![](https://assets.leetcode.com/uploads/2020/09/15/inorder_1.jpg)

输入：`root = [1,null,2]` 
输出：`[1,2]`
提示：
-   树中节点数目在范围 `[0, 100]` 内
-   -100 <= Node.val <= 100
**解题思路:**
	-    [广度优先搜索（Breadth First Search）](http://data.biancheng.net/view/326.html)
**题解(Python):**
```Python
# Definition for a binary tree node. 
# class TreeNode: 
	# def __init__(self, val=0, left=None, right=None): 
		# self.val = val 
		# self.left = left 
		# self.right = right 
class Solution:
    def inorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        res = []
        def helper(root):
            if not root:
                return 
            helper(root.left)
            res.append(root.val)
            helper(root.right)
        helper(root)
        return res
```
