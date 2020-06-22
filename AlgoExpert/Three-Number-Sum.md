# Three Number Sum

Given an array `nums` of *n* integers, are there elements *a*, *b*, *c*in `nums` such that *a* + *b* + *c* = 0? Find all unique triplets in the array which gives the sum of zero.

**Note:**

The solution set must not contain duplicate triplets.

**Example:**

```
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```



### Leetcode

https://leetcode.com/problems/3sum/



### Optimal Solution

Time Complexity:

Space Complexity:

```js
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    //  sort nums first in descending order
    // Time Complexity => O(nlogn)
    nums.sort((a, b) => a - b);

    // store the results in new array
    let output = [];

    // length of input array
    const n = nums.length;

    // iterate first element till n-2
    for (let i = 0; i < n - 2; i++) {
        // set j pointer to next value in the array
        let j = i + 1;
        // set k pointer to last value in the array
        let k = n - 1;

        const first = nums[i];

        // skip if previous number is same
        if (i > 0 && first === nums[i - 1]) continue;

        // check if the pointer has reached it's end
        while (j < k) {
            const second = nums[j];
            const third = nums[k];
            const sum = first + second + third;

            if (sum === 0) {
                output.push([first, second, third]);
                // skip next duplicate
                while (j < k && second === nums[j]) j++;
                // skip duplicate from last
                while (j < k && third === nums[k]) k--;
            }

            if (sum < 0) {
                // skip next duplicate
                while (j < k && second === nums[j]) j++;
            }

            if (sum > 0) {
                // skip duplicate from last
                while (j < k && third === nums[k]) k--;
            }
        }
    }

    return output;
};
```

