# Surrounded Regions

Given a 2D board containing `'X'` and `'O'` (**the letter O**), capture all regions surrounded by `'X'`.

A region is captured by flipping all `'O'`s into `'X'`s in that surrounded region.

**Example:**

```
X X X X
X O O X
X X O X
X O X X
```

After running your function, the board should be:

```
X X X X
X X X X
X X X X
X O X X
```

**Explanation:**

Surrounded regions shouldn’t be on the border, which means that any `'O'` on the border of the board are not flipped to `'X'`. Any `'O'` that is not on the border and it is not connected to an `'O'` on the border will be flipped to `'X'`. Two cells are connected if they are adjacent cells connected horizontally or vertically.



### Leetcode

https://leetcode.com/problems/surrounded-regions/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {character[][]} board
 * @return {void} Do not return anything, modify board in-place instead.
 */
var solve = function(board) {
  if(board.length === 0 || board[0].length === 0) return board;
  const row = board.length;
  const col = board[0].length;
  
  // do boundry dfs i.e only iterate through 'O' in boundry
  // left and right boundry
  for(let i=0; i<row; i++) {
    dfs(board, i, 0);
    dfs(board, i, col-1);
  }
  
  // top and bottom boundry
  for(let j=0; j<col; j++) {
    dfs(board, 0, j);
    dfs(board, row-1, j);
  }
  
  // convert all remaining 'O' to x since we couldn't reach them with dfs
  // convert all '*' to 'O' since those are connected to boundry
  for (let i = 0; i < row; i++) {
    for (let j = 0; j < col; j++) {
      if(board[i][j] === "O") {
        board[i][j] = "X";
      }
      if(board[i][j] === "*") {
        board[i][j] = "O";
      }
    }
  }
};


const dfs = (board, i, j) => {
  // ignore '*' since it is already visited
  if (i > board.length - 1 || i < 0 || j > board[0].length - 1 || j < 0 || board[i][j] === "*" || board[i][j] === "X") {
    return;
  }
  board[i][j] = "*";
  dfs(board, i + 1, j);
  dfs(board, i - 1, j);
  dfs(board, i, j + 1);
  dfs(board, i, j - 1);
}
```



### Explanation

https://www.youtube.com/watch?v=ztTLGMeleco