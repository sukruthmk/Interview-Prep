# Longest Consecutive Sequence

Given an unsorted array of integers, find the length of the longest consecutive elements sequence.

Your algorithm should run in O(*n*) complexity.

**Example:**

```
Input: [100, 4, 200, 1, 3, 2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. 
Therefore its length is 4.
```



### Leetcode

https://leetcode.com/problems/longest-consecutive-sequence/



### Optimal Solution

##### Approach 1 - Sorting

Time Complexity: O(nlogn)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var longestConsecutive = function(nums) {
    if(nums.length === 0) return 0;
    
    // sort the array first
    nums.sort((a, b) => a - b);
    let count = 1;
    let max = 1;
    
    for(let i =0; i<nums.length-1; i++) {
        // ignore duplicates
        if(nums[i] === nums[i+1]) {
            continue;
        }
        if(nums[i] === nums[i+1]-1) {
            count++;
            max = Math.max(max, count);
        } else {
            count = 1;
        }
    }
    
    return max;
};
```



##### Approach 2 - HashMap

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var longestConsecutive = function(nums) {
    const set = new Set();
    let max = 0;
    
    // create a hash map of numbers
    for(const num of nums) {
        set.add(num);
    }
    
    for(const num of nums) {
        // Optimization - if there is a previous value 
        // then we don't need to iterate through the current number
        // we can do it with the least value number in the
        // increasing sequence
        if(set.has(num - 1)) {
            continue;
        }
        let count = 1;
        let next = num+1;
        while(set.has(next)) {
            ++count;
            next++;
        }
        max = Math.max(count, max);
    }
    
    return max;
};
```

