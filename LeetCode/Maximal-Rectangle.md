# Maximal Rectangle

Given a `rows x cols` binary `matrix` filled with `0`'s and `1`'s, find the largest rectangle containing only `1`'s and return *its area*.

 

**Example 1:**

![img](https://assets.leetcode.com/uploads/2020/09/14/maximal.jpg)

```
Input: matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
Output: 6
Explanation: The maximal rectangle is shown in the above picture.
```

**Example 2:**

```
Input: matrix = []
Output: 0
```

**Example 3:**

```
Input: matrix = [["0"]]
Output: 0
```

**Example 4:**

```
Input: matrix = [["1"]]
Output: 1
```

**Example 5:**

```
Input: matrix = [["0","0"]]
Output: 0
```

 

**Constraints:**

- `rows == matrix.length`
- `cols == matrix.length`
- `0 <= row, cols <= 200`
- `matrix[i][j]` is `'0'` or `'1'`.



### Leetcode

https://leetcode.com/problems/maximal-rectangle/



### Optimal Solution

Time Complexity: *O(MxN)*

Space Complexity: *O(N)*

```js
/**
 * @param {character[][]} matrix
 * @return {number}
 */
var maximalRectangle = function(matrix) {
  if(matrix.length == 0) return 0;
  const m = matrix.length;
  const n = matrix[0].length;
  const dp = new Array(n).fill(0);
  let maxArea = 0;
  
  for(let row=0; row<m; row++) {
    addRowToDP(matrix, dp, row);
    const area = largestRectangleArea(dp);
    maxArea = Math.max(maxArea, area);
  }
  
  return maxArea;
};

const addRowToDP = (matrix, dp, row) => {
  for(let col=0; col<dp.length; col++) {
    if(matrix[row][col] == 0) {
      dp[col] = 0;
    } else {
      dp[col] = dp[col] + parseInt(matrix[row][col]);
    }
  }
}

const largestRectangleArea = function(heights) {
  const stack = [];
  let maxArea = 0;
  let i = 0;
  
  while(i < heights.length) {
    const topIndex = getTopOfStack(stack);
    // if stack is empty or top of stack value is less than current
    if(stack.length === 0 || heights[topIndex] <= heights[i]) {
      stack.push(i);
      i++;
    } else {
      // calculate area if top of the stack value is greater than current
      const area = getArea(heights, stack, i);
      maxArea = Math.max(maxArea, area);
    }
  }
  
  while(stack.length != 0) {
    const area = getArea(heights, stack, i);
    maxArea = Math.max(maxArea, area);
  }
  
  return maxArea;
};

const getTopOfStack = (stack) => {
  return stack[stack.length - 1];
}

const getArea = (heights, stack, i) => {
  const topIndex = stack.pop();
  let area = 0;
  
  if(stack.length === 0) {
    area = heights[topIndex] * i;
  } else {
    area = heights[topIndex]*(i - getTopOfStack(stack) - 1);
  }
  
  return area;
}
```



### Explanation

https://www.youtube.com/watch?v=g8bSdXCG-lA