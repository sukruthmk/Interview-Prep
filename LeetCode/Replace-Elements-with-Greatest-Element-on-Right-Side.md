# Replace Elements with Greatest Element on Right Side

Given an array `arr`, replace every element in that array with the greatest element among the elements to its right, and replace the last element with `-1`.

After doing so, return the array.

 

**Example 1:**

```
Input: arr = [17,18,5,4,6,1]
Output: [18,6,6,6,1,-1]
```

 

**Constraints:**

- `1 <= arr.length <= 10^4`
- `1 <= arr[i] <= 10^5`



### Leetcode

https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(1) - in place solution

```js
/**
 * @param {number[]} arr
 * @return {number[]}
 */
var replaceElements = function(arr) {
    if(arr.length === 0) return [];
    
    // first assign the last value to -1
    // then use the value at last as max value
    const length = arr.length;
    let max = arr[length - 1];
    arr[length - 1] = -1;
    let i = length - 2;
    
    // iterate from the last
    // keep track of max and assign it arr iteratively
    while(i >= 0) {
        const val = arr[i];
        arr[i] = max;
        max = Math.max(max, val);
        i--;
    }
    
    return arr;
};
```
