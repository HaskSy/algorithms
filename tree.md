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
        def is_same(p: TreeNode, q: TreeNode) -> bool:
            if not p and not q:
                return True
            if not (p and q):
                return False
            return (p.val == q.val) and is_same(p.left, q.left) and is_same(p.right, q.right)

        queue = [s]

        while queue:
            queue_size = len(queue)
            for _ in range(queue_size):
                node = queue.pop(0)
                if is_same(node, t):
                    return True
                if node is not None:
                    if node.left:
                        queue.append(node.left)
                    if node.right:
                        queue.append(node.right)
        return False

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
