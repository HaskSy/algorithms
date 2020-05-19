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

'''python
    
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
'''

## Symmetric Tree

https://leetcode.com/problems/symmetric-tree/

'''python

    def isSymmetric(self, root: TreeNode) -> bool:
        if not root:
            return True

        def rec_sym(left_branch: TreeNode, right_branch: TreeNode) -> bool:
            if not left_branch and not right_branch:
                return True
            if not (left_branch and right_branch):
                return False
            return (left_branch.val == right_branch.val and rec_sym(left_branch.left, right_branch.right) and
                    rec_sym(left_branch.right, right_branch.left))

        return rec_sym(root.left, root.right)

'''

## Maximum Depth Of Binary Tree

https://leetcode.com/problems/maximum-depth-of-binary-tree/

'''python

    def maxDepth(self, root: TreeNode) -> int:
        if root is None:
            return 0
        return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1

'''

## Same Tree

https://leetcode.com/problems/same-tree/

'''python

    def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        if not p and not q:
            return True
        if not (p and q):
            return False
        return (p.val == q.val) and self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)

'''

## Invert Binary Tree

https://leetcode.com/problems/invert-binary-tree/

'''python

    def invertTree(self, root: TreeNode) -> TreeNode:
        if root is None:
            return root
        root.right, root.left = root.left, root.right
        self.invertTree(root.right)
        self.invertTree(root.left)
        return root

'''

## Path Sum

https://leetcode.com/problems/path-sum/

'''python

    def hasPathSum(self, root: TreeNode, sum: int) -> bool:
        if root is None:
            return False
        substract = sum - root.val
        if not root.left and not root.right and root.val == sum:
            return True
        result = (self.hasPathSum(root.left, substract) or self.hasPathSum(root.right, substract))
        return result

'''

## Binary Tree Level Order Traversal

https://leetcode.com/problems/binary-tree-level-order-traversal/

'''python

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

'''

## Subtree Of Another Tree

https://leetcode.com/problems/subtree-of-another-tree/

'''python

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

'''

## Kth Smallest Element In a BST

https://leetcode.com/problems/kth-smallest-element-in-a-bst/

'''python

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

'''

## Validate Binary Search Tree

https://leetcode.com/problems/validate-binary-search-tree/

'''python

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

'''

## Binary Search Tree Iterator

https://leetcode.com/problems/binary-search-tree-iterator/

'''python

    class BSTIterator:

        def __init__(self, root: TreeNode):
            self.stack = []
            while root:
                self.stack.append(root)
                root = root.left

        def next(self) -> int:
            root_pop = self.stack.pop()
            if root_pop:
                root_pop_copy = root_pop.right
                while root_pop_copy:
                    self.stack.append(root_pop_copy)
                    root_pop_copy = root_pop_copy.left
            return root_pop.val

        def hasNext(self) -> bool:
            if self.stack:
                return True
            return False

'''