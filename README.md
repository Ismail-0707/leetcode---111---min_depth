# LeetCode 111 — Minimum Depth of Binary Tree

## Problem
Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

A leaf node is a node with no left and right children.

---

## Example

Input:
```text
root = [3,9,20,null,null,15,7]
```

Output:
```text
2
```

---

## Approach
Use Breadth First Search (BFS):

- Traverse the tree level by level
- The first leaf node encountered gives the minimum depth
- Return the current depth immediately

---

## Java Solution

```java
class Solution {
    public int minDepth(TreeNode root) 
    {
        Queue<TreeNode> q = new LinkedList<>();
        int depth = 0;

        if(root == null)
        {
            return depth;
        }

        q.add(root);

        while(!q.isEmpty())
        {
            int size = q.size();
            depth++;

            for(int i = 0; i < size; i++)
            {
                TreeNode root1 = q.poll();

                if(root1.left == null && root1.right == null)
                {
                    return depth;
                }

                if(root1.left != null)
                {
                    q.add(root1.left);
                }

                if(root1.right != null)
                {
                    q.add(root1.right);
                }
            }
        }

        return depth;
    }
}
```

---

## Time Complexity
```text
O(n)
```

Each node is visited once.

---

## Space Complexity
```text
O(n)
```

Queue stores nodes level by level.

---

## Key Concepts
- Binary Tree
- Breadth First Search (BFS)
- Queue
- Level Order Traversal
