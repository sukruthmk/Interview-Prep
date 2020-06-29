# Shortest Path in a Grid with Obstacles Elimination

Given a `m * n` grid, where each cell is either `0` (empty) or `1` (obstacle). In one step, you can move up, down, left or right from and to an empty cell.

Return the minimum number of steps to walk from the upper left corner `(0, 0)` to the lower right corner `(m-1, n-1)`given that you can eliminate **at most** `k` obstacles. If it is not possible to find such walk return -1.

 

**Example 1:**

```
Input: 
grid = 
[[0,0,0],
 [1,1,0],
 [0,0,0],
 [0,1,1],
 [0,0,0]], 
k = 1
Output: 6
Explanation: 
The shortest path without eliminating any obstacle is 10. 
The shortest path with one obstacle elimination at position (3,2) is 6. Such path is (0,0) -> (0,1) -> (0,2) -> (1,2) -> (2,2) -> (3,2) -> (4,2).
```

 

**Example 2:**

```
Input: 
grid = 
[[0,1,1],
 [1,1,1],
 [1,0,0]], 
k = 1
Output: -1
Explanation: 
We need to eliminate at least two obstacles to find such a walk.
```

 

**Constraints:**

- `grid.length == m`
- `grid[0].length == n`
- `1 <= m, n <= 40`
- `1 <= k <= m*n`
- `grid[i][j] == 0 **or** 1`
- `grid[0][0] == grid[m-1][n-1] == 0`





### Leetcode





### Optimal Solution

Time Complexity:

Space Complexity:

```js
/**
 * @param {number[][]} grid
 * @param {number} k
 * @return {number}
 */
var shortestPath = function(grid, k) {
    const m = grid.length;
    const n = grid[0].length;
    const dirs = [[0, 1], [0, -1], [1, 0], [-1, 0]];
    
    const visited = new Array(m).fill(0).map((arr) => new Array(n).fill(Number.MAX_VALUE))
    visited[0][0] = 0;
    const queue = [[0, 0, 0]];
    let steps = 0;
    
    while(queue.length > 0) {
        const size = queue.length;
        for(let i=0; i<size; i++) {
            const curr = queue.shift();
            const [currRow, currCol, currValue] = curr;
            if(currRow === m-1 && currCol === n-1) {
                return steps;
            }
            
            for(const dir of dirs) {
                const [i, j] = dir;
                const row = currRow + i;
                const col = currCol + j;            
                if(row >= 0 && row < m && col >=0 && col < n) {
                    const obstacle = currValue + grid[row][col];
                    if(obstacle > visited[row][col] || obstacle > k) continue;
                    visited[row][col] = obstacle;
                    queue.push([row, col, obstacle]);
                }
            }
        }
        steps++;
    }
    
    return -1;
};
```



### Explanation

https://www.youtube.com/watch?v=oxb9cJ4q2UU

https://www.youtube.com/watch?v=EmiGrlCQ-bM