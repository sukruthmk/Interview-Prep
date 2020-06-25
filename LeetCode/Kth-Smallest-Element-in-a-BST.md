# Kth Smallest Element in a BST

Given a binary search tree, write a function `kthSmallest` to find the **k**th smallest element in it.

**Example 1:**

```
Input: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
Output: 1
```

**Example 2:**

```
Input: root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
Output: 3
```

**Follow up:**
What if the BST is modified (insert/delete operations) often and you need to find the kth smallest frequently? How would you optimize the kthSmallest routine?

**Constraints:**

- The number of elements of the BST is between `1` to `10^4`.

- You may assume `k` is always valid, `1 ≤ k ≤ BST's total elements`.

  

### Leetcode

https://leetcode.com/problems/kth-smallest-element-in-a-bst/



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
 * @param {number} k
 * @return {number}
 */
var kthSmallest = function(root, k) {
    const result = [];
    
    // do inorder traversal
    inorder(root, k, result);
    
    return result[k-1];
};

const inorder = (root, k, result) => {
    if(root === null) {
        return;
    }
    
    // end if the result has reach kth value
    if(result.length > k) {
        return;
    }
    
    inorder(root.left, k, result);
    result.push(root.val);
    inorder(root.right, k, result);
}
```



### Explanation

https://www.youtube.com/watch?v=C6r1fDKAW_o