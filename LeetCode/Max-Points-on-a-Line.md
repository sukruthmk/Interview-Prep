# Max Points on a Line

Given *n* points on a 2D plane, find the maximum number of points that lie on the same straight line.

**Example 1:**

```
Input: [[1,1],[2,2],[3,3]]
Output: 3
Explanation:
^
|
|        o
|     o
|  o  
+------------->
0  1  2  3  4
```

**Example 2:**

```
Input: [[1,1],[3,2],[5,3],[4,1],[2,3],[1,4]]
Output: 4
Explanation:
^
|
|  o
|     o        o
|        o
|  o        o
+------------------->
0  1  2  3  4  5  6
```

**NOTE:** input types have been changed on April 15, 2019. Please reset to default code definition to get new method signature.



### Leetcode

https://leetcode.com/problems/max-points-on-a-line/



### Optimal Solution

Time Complexity: O(n^2)

Space Complexity: O(n)

```js
/**
 * @param {number[][]} points
 * @return {number}
 */
var maxPoints = function(points) {
  if (points.length<=2) return points.length;
  let result = 2;
  
  // 1. iterate through each points with a two for loops
  for(let i=0; i<points.length; i++) {
    let samePoints = 1;
    let localMax = 0;
    const map = {};
    
    for(let j=i+1; j<points.length; j++) {
      const pointA = points[i];
      const pointB = points[j];
      // 2. calculate same points or duplicates if any
      if(isPointsEqual(pointA, pointB)) {
        samePoints++;
        continue;
      }
      
      // 3. get the slope of two points
      let slope = getSlope(pointA, pointB);
      map[slope] = map[slope] + 1 || 1;
      // 4. keep track of local maximum
      localMax = Math.max(localMax, map[slope]);
    }
    
    // 5. Max points on same line = Maximum points on same slope + duplicates.
    result = Math.max(result, localMax + samePoints);
  }
  
  return result;
};

const isPointsEqual = (a, b) => {
  const [x1, y1] = a;
  const [x2, y2] = b;
  return x1 === x2 && y1 === y2;
}

const getSlope = (a, b) => {
  const [x1, y1] = a;
  const [x2, y2] = b;
  
  // Edge cases where the points can be on same plane i.e only on x-axis or only on y-axis
  let xDiff = x2 - x1;
  let yDiff = y2 - y1;
  if(xDiff === 0) return "y";
  if(yDiff === 0) return "x";
  
  // Get the gcd so that we can represent the slope in string format
  const gcd = getGCD(xDiff, yDiff);
  xDiff = xDiff / gcd;
  yDiff = yDiff / gcd;
  
  // storing it as a string with value like 91231/932411 instead of float to fix failing test cases.
  return `${xDiff}/${yDiff}`;
}

// helper function to get the gcd of two numbers
const getGCD = (a, b) => {
  if(b === 0) {
    return a;
  }
  return getGCD(b, a % b);
}
```



### Explanation

https://www.youtube.com/watch?v=KqZV0XfKQks