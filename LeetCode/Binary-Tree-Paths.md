# Binary Tree Paths

Given a binary tree, return all root-to-leaf paths.

**Note:** A leaf is a node with no children.

**Example:**

```
Input:

   1
 /   \
2     3
 \
  5

Output: ["1->2->5", "1->3"]

Explanation: All root-to-leaf paths are: 1->2->5, 1->3
```



### Leetcode

https://leetcode.com/problems/binary-tree-paths/



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
 * @return {string[]}
 */
var binaryTreePaths = function(root) {
    if(root === null) return [];
    const paths = [];
    dfs(root, "", paths);
    return paths;
};

const dfs = (root, currPath, paths) => {
    currPath += root.val;
    // if the node is a leef then push it to paths
    if(root.left === null && root.right === null) {
        paths.push(currPath);
        return;
    }
    if(root.left != null) {
        dfs(root.left, currPath + "->", paths);
    }
    if(root.right != null) {
        dfs(root.right, currPath + "->", paths);
    }
}
```



### Explanation

https://www.youtube.com/watch?v=xqS8dyexaNM