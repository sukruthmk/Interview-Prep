# Youngest Common Ancestor

Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow **a node to be a descendant of itself**).”

Given binary search tree: root = [6,2,8,0,4,7,9,null,null,3,5]

![img](https://assets.leetcode.com/uploads/2018/12/14/binarysearchtree_improved.png)

**Example 1:**

```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
Output: 6
Explanation: The LCA of nodes 2 and 8 is 6.
```

**Example 2:**

```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
Output: 2
Explanation: The LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.
```

**Note:**

- All of the nodes' values will be unique.
- p and q are different and both values will exist in the BST.



### Leetcode

https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n) - if we consider the recursion stack

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */

/**
 * @param {TreeNode} root
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */
var lowestCommonAncestor = function(root, p, q) {
    const rootVal = root.val;
    const pVal = p.val;
    const qVal = q.val;
    
    // If both p and q are greater than parent
    if(pVal > rootVal && qVal > rootVal) {
        return lowestCommonAncestor(root.right, p, q);
    } 
    // If both p and q are lesser than parent
    if (pVal < rootVal && qVal < rootVal) {
        return lowestCommonAncestor(root.left, p, q);
    }
    
    // We have found the split point, i.e. the LCA node.
    return root;
}
```



