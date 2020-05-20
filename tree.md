# Tree

+ [Binary Search Tree Iterator](#binary-search-tree-iterator)

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
