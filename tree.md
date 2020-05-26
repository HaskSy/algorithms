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
def inorderTraversal(self, root: TreeNode) -> List[int]:
    stack = []
    result = []
    while stack or root:
        while root:
            stack.append(root)
            root = root.left
        root = stack.pop()
        result.append(root.val)
        root = root.right
    return result

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
def hasPathSum(self, root: TreeNode, sum: int) -> bool:
    if not root:
        return False
    if not root.left and not root.right and root.val == sum:
        return True
    return self.hasPathSum(root.left, sum - root.val) or \
        self.hasPathSum(root.right, sum - root.val)

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
def kthSmallest(self, root: TreeNode, k: int) -> int:
    stack = []
    while root or stack:
        while root:
            stack.append(root)
            root = root.left
        root = stack.pop()
        k -= 1
        if k == 0:
            return root.val
        root = root.right

```

## Validate Binary Search Tree

https://leetcode.com/problems/validate-binary-search-tree/

```python
def isValidBST(self, root: TreeNode) -> bool:
    stack = []
    data = float('-inf')
    while stack or root:
        while root:
            stack.append(root)
            root = root.left
        root = stack.pop()
        if root.val <= data:
            return False
        data = root.val
        root = root.right
    return True


def helper(self, root, left=float('-inf'), right=float('inf')):
    """
    :type root: TreeNode
    :rtype: bool
    """
    if root is None:
        return True
    if not left < root.val < right:
        return False
    return self.helper(root.left, left, root.val) and \
        self.helper(root.right, root.val, right)


def isValidBST(self, root: TreeNode) -> bool:
    return self.helper(root)

```

## Binary Search Tree Iterator

https://leetcode.com/problems/binary-search-tree-iterator/

```python
class BSTIterator:
    def __init__(self, root: TreeNode):
        self.stack = []
        while root:
            self.stack.append(root)
            root = root.left

    def next(self) -> int:
        next = self.stack.pop()
        if next:
            current = next.right
            while current:
                self.stack.append(current)
                current = current.left
        return next.val
    
    def hasNext(self) -> bool:
        return len(self.stack) > 0

```
