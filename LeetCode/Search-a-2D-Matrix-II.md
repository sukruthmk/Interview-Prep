# Search a 2D Matrix II

Write an efficient algorithm that searches for a value in an *m* x *n* matrix. This matrix has the following properties:

- Integers in each row are sorted in ascending from left to right.
- Integers in each column are sorted in ascending from top to bottom.

**Example:**

Consider the following matrix:

```
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
```

Given target = `5`, return `true`.

Given target = `20`, return `false`.



### Leetcode

https://leetcode.com/problems/search-a-2d-matrix-ii/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var searchMatrix = function(matrix, target) {
    if(matrix.length === 0) return false;
    let m = matrix.length;
    let n = matrix[0].length;
    
    let row = 0;
    let col = n - 1;
    
    while(row < m && col >= 0) {
        const num = matrix[row][col];
        if(num === target) {
            return true;
        }
        if(target > num) {
            // if target is greater
            row++;
        } else {
            // if target is lesser
            col--;
        }
    }
    
    return false;
};
```



### Explanation

https://www.youtube.com/watch?v=_j_LxpiftkU