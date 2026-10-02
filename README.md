# Find-Mode-in-Binary-Search-Tree
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def findMode(self, root: TreeNode | None) -> list[int]:
        if root is None:
            return []
        r=[]
        def add(root,r):
            if root is None:
                return 
            r.append(root.val)
            add(root.left,r)
            add(root.right,r)
        add(root,r)
        count=Counter(r)
        m=max(count.values())
        a=[]
        for i,c in count.items():
            if c==m:
                a.append(i)
        return a
