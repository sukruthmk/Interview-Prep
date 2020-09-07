# Sudoku Solver

Write a program to solve a Sudoku puzzle by filling the empty cells.

A sudoku solution must satisfy **all of the following rules**:

1. Each of the digits `1-9` must occur exactly once in each row.
2. Each of the digits `1-9` must occur exactly once in each column.
3. Each of the the digits `1-9` must occur exactly once in each of the 9 `3x3` sub-boxes of the grid.

Empty cells are indicated by the character `'.'`.

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)
A sudoku puzzle...

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Sudoku-by-L2G-20050714_solution.svg/250px-Sudoku-by-L2G-20050714_solution.svg.png)
...and its solution numbers marked in red.

**Note:**

- The given board contain only digits `1-9` and the character `'.'`.
- You may assume that the given Sudoku puzzle will have a single unique solution.
- The given board size is always `9x9`.



### Leetcode

https://leetcode.com/problems/sudoku-solver/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {character[][]} board
 * @return {void} Do not return anything, modify board in-place instead.
 */
var solveSudoku = function(board) {
  if(board == null || board.length == 0)
    return;
  backtrack(board);
};

const backtrack = (board) => {  
  for(let i=0; i<9; i++) {
    for(let j=0; j<9; j++) {
      if(board[i][j] === '.') {
        for(let num=1; num<=9; num++) { // try number 1 to 9
          const numString = String(num);
          if(isValid(board, i, j, numString)) {
            board[i][j] = numString
            
            if(backtrack(board)) {
              return true; // if this is the solution then return true
            }
            
            board[i][j] = '.'; // otherwise go back and try again
          }
        }
        return false;
      }
    }
  }
  return true;
}

const isValid = (board, row, col, num) => {
  for(let i=0; i<9; i++) {
    if(board[row][i] == num) return false; // check row
    if(board[i][col] == num) return false; // check column
    
    // ex:- board[4][4] sub-grid starts from board[3][3]
    // we need to add divisor i/3 to row i.e for every 3 moves we change the row
    const subRow = Math.floor(row/3)*3 + Math.floor(i/3);
    // we need to add the remainder i.e every 3 moves we reset the column to start
    const subCol = Math.floor(col/3)*3 + i%3;
    if(board[subRow][subCol] == num) return false;
  }
  return true;
}
```



### Explanation

https://www.youtube.com/watch?v=wWUDo2FkdMc