# Pascal's Triangle

Given a non-negative integer *numRows*, generate the first *numRows* of Pascal's triangle.

![img](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)
In Pascal's triangle, each number is the sum of the two numbers directly above it.

**Example:**

```
Input: 5
Output:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```



### Leetcode

https://leetcode.com/problems/pascals-triangle/



### Optimal Solution

Time Complexity: O(n^2)

Space Complexity: O(n^2)

```js
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
    // corner case
    if(numRows === 0) return [];
    
    // base initialization
    const pascalMatrix = [[1]];
    
    let i = 1;
    while (i < numRows) {
        // get the last matrix that was inserted
        const lastMatrix = pascalMatrix[pascalMatrix.length - 1];
        // find the boundry points
        const start = 0;
        const end = lastMatrix.length;
        const currRow = [];
        
        for(let j=0; j<=i; j++) {
            let sum = 1;
            // if we are able to find the top two numbers for a position
            // then take the sum of them
            // or else add 1
            if(j-1 >= start && j < end) {
                const first = lastMatrix[j-1];
                const second = lastMatrix[j];
                sum = first+second;
            }
            currRow.push(sum);
        }
        
        pascalMatrix.push(currRow);
        i++;
    }
    
    return pascalMatrix;
};
```
