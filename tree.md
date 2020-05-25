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

```

## Maximum Depth Of Binary Tree

https://leetcode.com/problems/maximum-depth-of-binary-tree/

```python

```

## Same Tree

https://leetcode.com/problems/same-tree/

```python

```

## Invert Binary Tree

https://leetcode.com/problems/invert-binary-tree/

```python

```

## Path Sum

https://leetcode.com/problems/path-sum/

```python

```

## Binary Tree Level Order Traversal

https://leetcode.com/problems/binary-tree-level-order-traversal/

```python

```

## Subtree Of Another Tree

https://leetcode.com/problems/subtree-of-another-tree/

```python
def isSubtree(self, s: TreeNode, t: TreeNode) -> bool:
    def tree_to_str(node):
        if not node:
            return "None"
        return "|" + str(node.val) + tree_to_str(node.left) + \
            tree_to_str(node.right)
    s_str = tree_to_str(s)
    t_str = tree_to_str(t)
    if t_str in s_str:
        return True
    return False


def isSubtree(self, s: TreeNode, t: TreeNode) -> bool:
    if not s and not t:
        return True
    if not s or not t:
        return False
    return self.helper(s, t) or self.isSubtree(s.left, t) or \
        self.isSubtree(s.right, t)


def helper(self, s, t):
    if not s and not t:
        return True
    if not (s and t):
        return False
    return s.val == t.val and self.helper(s.left, t.left) and \
        self.helper(s.right, t.right)

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
