# Search in Sorted Matrix

Write an efficient algorithm that searches for a value in an *m* x *n* matrix. This matrix has the following properties:

- Integers in each row are sorted from left to right.
- The first integer of each row is greater than the last integer of the previous row.

**Example 1:**

```
Input:
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 3
Output: true
```

**Example 2:**

```
Input:
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 13
Output: false
```



### Leetcode

https://leetcode.com/problems/search-a-2d-matrix/



### Optimal Solution

```js
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var searchMatrix = function(matrix, target) {
    if(matrix.length === 0) return false;
    const rows = matrix.length;
    const columns = matrix[0].length;
    
    // consider matrix like a big array and do binary search
    let left = 0;
    let right = rows*columns - 1;
    
    while(left <= right) {
        const mid = left + Math.floor((right-left)/2);
        // calculate midRow based on the mid point. 
        // Since midpoint is a single number we can divide 
        // it by number of columns to get the row number.
        const midRow = Math.floor(mid/columns);
        // midCol can be calculated by taking modulus of columns on mid point
        const midCol = mid%columns;
        const midValue = matrix[midRow][midCol];
        if(midValue === target) {
            return true;
        }
        if(target > midValue) {
            left = mid + 1;   
        } else {
            right = mid - 1;
        }
    }
    
    return false;
};
```

