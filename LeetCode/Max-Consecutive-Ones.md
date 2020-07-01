# Max Consecutive Ones

Given a binary array, find the maximum number of consecutive 1s in this array.

**Example 1:**

```
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
```



**Note:**

- The input array will only contain `0` and `1`.
- The length of input array is a positive integer and will not exceed 10,000



### Leetcode

https://leetcode.com/problems/max-consecutive-ones/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {
    let max = 0;
    let sum = 0;
    
    for(let i=0; i<nums.length; i++) {
        if(nums[i] === 1) {
            sum++;
            max = Math.max(max, sum);
        } else  {
            sum = 0;
        }
    }
    
    return max;
};
```
