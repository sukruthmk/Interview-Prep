# Largest Rectangle in Histogram

Given *n* non-negative integers representing the histogram's bar height where the width of each bar is 1, find the area of largest rectangle in the histogram.

 

![img](https://assets.leetcode.com/uploads/2018/10/12/histogram.png)
Above is a histogram where width of each bar is 1, given height = `[2,1,5,6,2,3]`.

 

![img](https://assets.leetcode.com/uploads/2018/10/12/histogram_area.png)
The largest rectangle is shown in the shaded area, which has area = `10` unit.

 

**Example:**

```
Input: [2,1,5,6,2,3]
Output: 10
```



### Leetcode

https://leetcode.com/problems/largest-rectangle-in-histogram/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} heights
 * @return {number}
 */
var largestRectangleArea = function(heights) {
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

https://www.youtube.com/watch?v=ZmnqCZp9bBs