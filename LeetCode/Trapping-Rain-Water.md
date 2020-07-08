# Trapping Rain Water

Given *n* non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

![img](https://assets.leetcode.com/uploads/2018/10/22/rainwatertrap.png)
The above elevation map is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped. **Thanks Marcos** for contributing this image!

**Example:**

```
Input: [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
```



### Leetcode

https://leetcode.com/problems/trapping-rain-water/



### Optimal Solution

#### Approach 1 - Left max and Right max

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} height
 * @return {number}
 */
var trap = function(height) {
    let totalWater = 0;
    const leftMax = [];
    const rightMax = [];
    
    // generate the current max at index i while iterating left to right
    let max = 0;
    for(let i=0; i<height.length; i++) {
        max = Math.max(max, height[i]);
        leftMax[i] = max;
    }
    
    // generate the current max at index i while iterating right to left
    max = 0;
    for(let i=height.length - 1; i>=0; i--) {
        max = Math.max(max, height[i]);
        rightMax[i] = max;
    }
    
    // get the min of the left and right max at index i
    // then use the min and subtract it by height at index i
    for(let i=0; i<height.length; i++) {
        const waterAndBuilding = Math.min(leftMax[i], rightMax[i]);
        const water = waterAndBuilding - height[i];
        totalWater = totalWater + water;
    }
    
    return totalWater;
};
```

#### Approach 2 - Two Pointers

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} height
 * @return {number}
 */
var trap = function(height) {
    let totalWater = 0;
    let leftMax = 0;
    let rightMax = 0;
    let i = 0;
    let j = height.length - 1;
    
    while(i < j) {
        // if left value is less than right value
        if(height[i] < height[j]) {
            
            // if current hegiht is increasing w.r.t leftMax 
            // then continue calculation leftMax
            if(height[i] >= leftMax) {
                leftMax = height[i];
            } else {
                // if current height is < leftMax then
                // subtract current height from leftMax and add it to total
                totalWater = totalWater + (leftMax - height[i]);
            }
            i++;
        } else {
            // if current height is increasing w.r.t rightMax 
            // then continue calculating rightMax
            if(height[j] >= rightMax) {
                rightMax = height[j]
            } else {
                // if current heght is < rightMax then
                // subtract current height from rightMax and add it to total
                totalWater = totalWater + (rightMax - height[j]);
            }
            j--;
        }
    }
    
    
    return totalWater;
};
```



### Explanation

https://www.youtube.com/watch?v=HmBbcDiJapY

