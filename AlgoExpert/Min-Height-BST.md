# Min Height BST

Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of *every*node never differ by more than 1.

**Example:**

```
Given the sorted array: [-10,-3,0,5,9],

One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:

      0
     / \
   -3   9
   /   /
 -10  5
```



### Leetcode

https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/



### Optimal Solution

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {number[]} nums
 * @return {TreeNode}
 */
var sortedArrayToBST = function(nums) {
    return createBST(nums, 0, nums.length - 1);
};

const createBST = (nums, left, right) => {
    if(left > right) {
        return null;
    }
    const mid  = left + Math.floor((right-left)/2);
    const tree = new TreeNode(nums[mid]);
    tree.left = createBST(nums, left, mid-1);
    tree.right = createBST(nums, mid+1, right);
    return tree;
}
```

