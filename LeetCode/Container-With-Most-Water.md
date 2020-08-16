# Container With Most Water

Given *n* non-negative integers *a1*, *a2*, ..., *an* , where each represents a point at coordinate (*i*, *ai*). *n* vertical lines are drawn such that the two endpoints of line *i* is at (*i*, *ai*) and (*i*, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

**Note:** You may not slant the container and *n* is at least 2.

 

![img](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)

The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49. 

 

**Example:**

```
Input: [1,8,6,2,5,4,8,3,7]
Output: 49
```



### Leetcode

https://leetcode.com/problems/container-with-most-water/



### Optimal Solution

#### Approach 1 - Brute force

Time Complexity: *O*(*n*2)

Space Complexity: *O*(1)

```js
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function(height) {
    let max = -Number.MAX_VALUE;
    for(let i=height.length - 1; i>0; i--) {
        for(let j=0; j<i; j++) {
          	// find the min height for which we can hold water
            const minHeight = Math.min(height[i], height[j]);
          	// area is minHeight * positions difference
            max = Math.max(max, minHeight * (i-j));
        }
    }
    return max;
};
```



#### Approach 2 - Two pass

Time Complexity: *O*(*n*)

Space Complexity: *O*(1)

```js
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function(height) {
    let max = -Number.MAX_VALUE;
    let i = 0;
    let j = height.length - 1;
    
    while (i < j) {
        // find min height which can hold the water
        const min = Math.min(height[i], height[j]);
        // area = minHeight * position difference
        max = Math.max(max, min * (j-i));
        // if height[i] is less than height[j]
        // then increment i
        // else decrement j
        if(height[i] < height[j]) {
            i++;
        } else {
            j--;
        }
    }
    
    return max;
};
```



### Explanation

https://www.youtube.com/watch?v=TI3e-17YAlc