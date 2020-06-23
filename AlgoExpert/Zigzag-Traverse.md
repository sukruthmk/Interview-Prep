# Zigzag Traverse

Given a matrix of M x N elements (M rows, N columns), return all elements of the matrix in diagonal order as shown in the below image.

**Example:**

```
Input:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]

Output:  [1,2,4,7,5,3,6,8,9]

Explanation:
```

**Note:**

The total number of elements of the given matrix will not exceed 10,000.



### Leetcode

https://leetcode.com/problems/diagonal-traverse/



### Optimal Solution

Time Complexity: O(m*n)

Space Complexity: O(m*n)

```js
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var findDiagonalOrder = function(matrix) {
    if (matrix === null || matrix.length === 0) return [];
    
    const m = matrix.length;
    const n = matrix[0].length;
    
    const result = new Array(m*n);
    const dirs = [[-1, 1], [1, -1]];
    let i = 0;
    let j = 0;
    let d = 0;
    
    for(let k=0; k<m*n; k++) {
        result[k] = matrix[i][j];
        i = i + dirs[d][0];
        j = j + dirs[d][1];
        if(i >= m) {
            i = m - 1;
            j += 2;
            d = 1 - d; 
        }
        if(j >= n) {
            i += 2;
            j = n - 1;
            d = 1 - d;
        }
        if(i < 0) {
            i = 0;
            d = 1 - d;
        }
        if(j < 0) {
            j = 0;
            d = 1 - d;
        }
    }
    
    return result;
};
```

