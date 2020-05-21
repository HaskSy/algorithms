# Tree

+ [Binary Tree Inorder Traversal](#binary-tree-inorder-traversal)
+ [Symmetric Tree](#symmetric-tree)
+ [Maximum Depth Of Binary Tree](#maximum-depth-of-binary-tree)
+ [Same Tree](#same-tree)
+ [Invert Binary Tree](#invert-binary-tree)
+ [Path Sum](#path-sum)
+ [Binary Tree Level Order Traversal](#binary-tree-level-order-traversal)
+ [Subtree Of Another Tree](#subtree-of-another-tree)
+ [Kth Smallest Element In a BST](#kth-smallest-element-in-a-bst)
+ [Validate Binary Search Tree](#validate-binary-search-tree)
+ [Binary Search Tree Iterator](#binary-search-tree-iterator)

## Binary Tree Inorder Traversal

https://leetcode.com/problems/binary-tree-inorder-traversal/

```python

```

## Symmetric Tree

https://leetcode.com/problems/symmetric-tree/

```python
def isSymmetric(self, root: TreeNode) -> bool:
    if not root:
        return True

    def rec_sym(left: TreeNode, right: TreeNode) -> bool:
        if not left and not right:
            return True
        if not left or not right:
            return False
        return left.val == right.val and rec_sym(left.left, right.right) and \
            rec_sym(left.right, right.left)

    return rec_sym(root.left, root.right)

```

## Maximum Depth Of Binary Tree

https://leetcode.com/problems/maximum-depth-of-binary-tree/

```python
def maxDepth(self, root: TreeNode) -> int:
    if root is None:
        return 0
    return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1

```

## Same Tree

https://leetcode.com/problems/same-tree/

```python
def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        if not p and not q:
            return True
        if not p or not q:
            return False
        return (p.val == q.val) and self.isSameTree(p.left, q.left) and \
            self.isSameTree(p.right, q.right)

```

## Invert Binary Tree

https://leetcode.com/problems/invert-binary-tree/

```python
def invertTree(self, root: TreeNode) -> TreeNode:
    if root is None:
        return root
    root.right, root.left = root.left, root.right
    self.invertTree(root.right)
    self.invertTree(root.left)
    return root

```

## Path Sum

https://leetcode.com/problems/path-sum/

```python

```

## Binary Tree Level Order Traversal

https://leetcode.com/problems/binary-tree-level-order-traversal/

```python
def levelOrder(self, root: TreeNode) -> List[List[int]]:
    result = []
    if root is None:
        return result
    queue = [root]
    while queue:
        level = []
        queue_size = len(queue)
        for _ in range(queue_size):
            node = queue.pop(0)
            if node is not None:
                level.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
        result.append(level)
    return result

```

## Subtree Of Another Tree

https://leetcode.com/problems/subtree-of-another-tree/

```python

```

## Kth Smallest Element In a BST

https://leetcode.com/problems/kth-smallest-element-in-a-bst/

```python

```

## Validate Binary Search Tree

https://leetcode.com/problems/validate-binary-search-tree/

```python

```

## Binary Search Tree Iterator

https://leetcode.com/problems/binary-search-tree-iterator/

```python

```
