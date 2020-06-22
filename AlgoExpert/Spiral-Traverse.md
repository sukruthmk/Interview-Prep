# Spiral Traverse

Given a matrix of *m* x *n* elements (*m* rows, *n* columns), return all elements of the matrix in spiral order.

**Example 1:**

```
Input:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
Output: [1,2,3,6,9,8,7,4,5]
```

**Example 2:**

```
Input:
[
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9,10,11,12]
]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
```



### Leetcode

https://leetcode.com/problems/spiral-matrix/



### Optimal Solution

Time Complexity:

Space Complexity:

```js
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var spiralOrder = function(matrix) {
    if(matrix.length === 0) return [];
    const nums = [];
    let left = 0;
    let right = matrix[0].length - 1;
    let bottom = matrix.length - 1;
    let top = 0;
    const size = matrix.length * matrix[0].length;
    while(nums.length < size) {
        for(let i=left; i<=right && nums.length < size; i++) {
            nums.push(matrix[top][i]);
        }
        top++;
        for(let i=top; i<=bottom && nums.length < size; i++) {
            nums.push(matrix[i][right]);
        }
        right--;
        for(let i=right; i>=left && nums.length < size; i--) {
            nums.push(matrix[bottom][i]);
        }
        bottom--;
        for(let i=bottom; i>=top && nums.length < size; i--) {
            nums.push(matrix[i][left]);
        }
        left++;
    }
    return nums;
};
```

