# Unique Paths

A robot is located at the top-left corner of a `m x n` grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

 

**Example 1:**

![img](https://assets.leetcode.com/uploads/2018/10/22/robot_maze.png)

```
Input: m = 3, n = 7
Output: 28
```

**Example 2:**

```
Input: m = 3, n = 2
Output: 3
Explanation:
From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down
```

**Example 3:**

```
Input: m = 7, n = 3
Output: 28
```

**Example 4:**

```
Input: m = 3, n = 3
Output: 6
```

 

**Constraints:**

- `1 <= m, n <= 100`
- It's guaranteed that the answer will be less than or equal to `2 * 109`.



### Leetcode

https://leetcode.com/problems/unique-paths/



### Optimal Solution

Time Complexity: *O(MxN)*

Space Complexity: *O(MxN)*

```js
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
var uniquePaths = function(m, n) {
  const dp = new Array(m).fill(0).map(() => new Array(n).fill(0));
  
  for(let row = 0; row < m; row++) {
    dp[row][0] = 1;
  }
  
  for(let col = 0; col < n; col++) {
    dp[0][col] = 1;
  }
  
  for(let row = 1; row < m; row++) {
    for(let col = 1; col < n; col++) {
      dp[row][col] = dp[row-1][col] + dp[row][col-1];
    }
  }
  
  return dp[m-1][n-1];
};
```
