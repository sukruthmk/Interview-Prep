# Maximal Square

Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

**Example:**

```
Input: 

1 0 1 0 0
1 0 1 1 1
1 1 1 1 1
1 0 0 1 0

Output: 4
```



### Leetcode

https://leetcode.com/problems/maximal-square/



### Optimal Solution

Time Complexity: *O*(*m**n*)

Space Complexity: *O*(*m**n*)

```js
/**
 * @param {character[][]} matrix
 * @return {number}
 */
var maximalSquare = function(matrix) {
    if(matrix.length === 0) return 0;
    const m = matrix.length;
    const n = matrix[0].length;
    const dp = new Array(m+1).fill(0).map(() => new Array(n+1).fill(0))
    
    let max = 0;
    for(let i=1; i<=m; i++) {
        for(let j=1; j<=n; j++) {
            if(matrix[i-1][j-1] == 1) {
                // get the minimum of left, up and diagonal backwards
                const min = Math.min(dp[i-1][j-1], dp[i-1][j], dp[i][j-1]);
                dp[i][j] = min + 1;
                // keep track of max square size
                max = Math.max(max, dp[i][j]);
            }
        }
    }
    
    // return area of square of size max which max^2
    // since all the values in a square is 1
    return max * max;
};
```



### Explanation

https://www.youtube.com/watch?v=KZQCvq2dUY8&feature=youtu.be