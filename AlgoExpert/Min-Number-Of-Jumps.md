# Min Number Of Jumps

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

**Example:**

```
Input: [2,3,1,1,4]
Output: 2
Explanation: The minimum number of jumps to reach the last index is 2.
    Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

**Note:**

You can assume that you can always reach the last index.



### Leetcode

https://leetcode.com/problems/jump-game-ii/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var jump = function(nums) {
    let max = 0;
    let oldMax = 0;
    let jump = 0;
    
    // Since we are asked to assume that the last index is always reachable
    // We can just keep track of the old and new max values
    for(let i=0; i<nums.length-1; i++) {
        // record what is the maximum distance we can jump from this position.
        max = Math.max(max, i+nums[i]);
        
        // if we have reached the previous max position. 
        // Then we know we can move upto this max value from current position. 
        // So we can simply update the oldmax and consider this as a jump
        if(i === oldMax) {
            oldMax = max;
            jump++;
        }
    }
    
    return jump;
};
```

