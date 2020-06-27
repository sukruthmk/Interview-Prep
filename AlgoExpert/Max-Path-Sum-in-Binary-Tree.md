# Max Path Sum in Binary Tree

Given a **non-empty** binary tree, find the maximum path sum.

For this problem, a path is defined as any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The path must contain **at least one node** and does not need to go through the root.

**Example 1:**

```
Input: [1,2,3]

       1
      / \
     2   3

Output: 6
```

**Example 2:**

```
Input: [-10,9,20,null,null,15,7]

   -10
   / \
  9  20
    /  \
   15   7

Output: 42
```



### Leetcode

https://leetcode.com/problems/binary-tree-maximum-path-sum/



### Optimal Solution

Time Complexity:

Space Complexity:

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
 * @return {number}
 */
var maxPathSum = function(root) {
    let result = -Number.MAX_VALUE;
    
    const pathSum = (root) => {
        if(root === null) {
            return 0;
        }
        
        // get the max of left node
        const left = Math.max(0, pathSum(root.left));
        // get the max of right node
        const right = Math.max(0, pathSum(root.right));
        const val = root.val;
        
        // keep track of global max
        result = Math.max(result, left+right+val);
        
        return Math.max(left, right) + root.val;
    }
    
    pathSum(root);
    
    return result;
};
```



### Explanation

https://www.youtube.com/watch?v=mOdetMWwtoI