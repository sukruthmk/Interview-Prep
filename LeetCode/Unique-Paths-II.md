# Unique Paths II

A robot is located at the top-left corner of a *m* x *n* grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

Now consider if some obstacles are added to the grids. How many unique paths would there be?

![img](https://assets.leetcode.com/uploads/2018/10/22/robot_maze.png)

An obstacle and empty space is marked as `1` and `0` respectively in the grid.

**Note:** *m* and *n* will be at most 100.

**Example 1:**

```
Input:
[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
Output: 2
Explanation:
There is one obstacle in the middle of the 3x3 grid above.
There are two ways to reach the bottom-right corner:
1. Right -> Right -> Down -> Down
2. Down -> Down -> Right -> Right
```



### Leetcode

https://leetcode.com/problems/unique-paths-ii/



### Optimal Solution

Time Complexity: *O*(*M*×*N*)

Space Complexity: *O*(*M*×*N*)

```js
/**
 * @param {number[][]} obstacleGrid
 * @return {number}
 */
var uniquePathsWithObstacles = function(obstacleGrid) {
  if(obstacleGrid.length === 0 || obstacleGrid[0][0] === 1) return 0;
  
  const m = obstacleGrid.length;
  const n = obstacleGrid[0].length;
  const dp = new Array(m).fill(0).map(() => new Array(n).fill(0));
   
  for(let row=0; row<m; row++) {
    // if row obstacle is found, then we cannot go down
    const rowObstacleFound = obstacleGrid[row][0] == 1;
    if(rowObstacleFound) break;
    dp[row][0] = 1;
  }
  
  for(let col=0; col<n; col++) {
    // if col obstacle is found, then we cannot go right
    const colObstacleFound = obstacleGrid[0][col] == 1;
    if(colObstacleFound) break;
    dp[0][col] = 1;
  }
  
  for(let row=1; row<m; row++) {
    for(let col=1; col<n; col++) {
      // skip obstacles
      if(obstacleGrid[row][col] == 1) continue;
      // calculate the number of paths from left and top
      dp[row][col] = dp[row][col-1] + dp[row-1][col];
    }
  }
  
  return dp[m-1][n-1];
};
```
