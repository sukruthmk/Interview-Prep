# River Sizes

Given a 2d grid map of `'1'`s (land) and `'0'`s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**

```
Input:
11110
11010
11000
00000

Output: 1
```

**Example 2:**

```
Input:
11000
11000
00100
00011

Output: 3
```



### Leetcode

https://leetcode.com/problems/number-of-islands/



### Optimal Solution

Time Complexity:

Space Complexity:

```js
/**
 * @param {character[][]} grid
 * @return {number}
 */
var numIslands = function(grid) {
  if(grid == null || grid.length === 0) {
      return 0;
  }
  const row = grid.length;
  const col = grid[0].length;
  let islands = 0;

  // iterate to find all land areas
  for (let i = 0; i < row; i++) {
    for (let j = 0; j < col; j++) {
      const value = grid[i][j];
      if (isLand(value)) {
        // do dfs search for connected islands
        islands += dfs(grid, i, j);
      }
    }
  }

  return islands;
};

const dfs = (grid, i, j) => {
  // assume outside grid is water
  if (i < 0 || i > grid.length - 1 || j < 0 || j > grid[0].length - 1 || isWater(grid[i][j])) {
    return 0;
  }
  // mark the current position as visited
  grid[i][j] = '0';
  // bottom
  dfs(grid, i + 1, j);
  // top
  dfs(grid, i - 1, j);
  // right
  dfs(grid, i, j + 1);
  // left
  dfs(grid, i, j - 1);
  return 1;
}

const isLand = (value) => {
  return value === '1';
}

const isWater = (value) => {
  return value === '0';
}
```

