# Flatten Binary Tree to Linked List

Given a binary tree, flatten it to a linked list in-place.

For example, given the following tree:

```
    1
   / \
  2   5
 / \   \
3   4   6
```

The flattened tree should look like:

```
1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6
```



### Leetcode

https://leetcode.com/problems/flatten-binary-tree-to-linked-list/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n)

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
 * @return {void} Do not return anything, modify root in-place instead.
 */
var flatten = function(root) {
    if(root === null) return root;
    const stack = [root];
    
    while(stack.length > 0) {
        const node = stack.pop();
        if(node.right != null) {
            stack.push(node.right);
        }
        if(node.left != null) {
            stack.push(node.left);
        }
        if(stack.length > 0) {
            node.right = stack[stack.length - 1];
        }
        node.left = null;
    }
};
```



### Explanation

https://www.youtube.com/watch?v=vssbwPkarPQ