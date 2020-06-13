# Invert Binary Tree

Invert a binary tree.

**Example:**

Input:

```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```

Output:

```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

**Trivia:**
This problem was inspired by [this original tweet](https://twitter.com/mxcl/status/608682016205344768) by [Max Howell](https://twitter.com/mxcl):

> Google: 90% of our engineers use the software you wrote (Homebrew), but you can’t invert a binary tree on a whiteboard so f*** off.

#### Leetcode

https://leetcode.com/problems/invert-binary-tree/

#### Optimal Solution

Time Complexity: O(n)

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {TreeNode}
 */
var invertTree = function(root) {
    helper(root);
    return root;
};

const helper = (root) => {
    // base case
    if(root === null) {
        return;
    }
    
    // swap left child with right child and viceversa
    swapChildrens(root);
    
    // recurse on child nodes
    helper(root.left);
    helper(root.right);
}

const swapChildrens = (root) => {
    const left = root.left;
    const right = root.right;
    root.left = right;
    root.right = left;
}
```

