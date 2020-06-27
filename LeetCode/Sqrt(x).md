# Sqrt(x)

Implement `int sqrt(int x)`.

Compute and return the square root of *x*, where *x* is guaranteed to be a non-negative integer.

Since the return type is an integer, the decimal digits are truncated and only the integer part of the result is returned.

**Example 1:**

```
Input: 4
Output: 2
```

**Example 2:**

```
Input: 8
Output: 2
Explanation: The square root of 8 is 2.82842..., and since 
             the decimal part is truncated, 2 is returned.
```



### Leetcode

https://leetcode.com/problems/sqrtx/



### Optimal Solution

Time Complexity: O(logn)

Space Complexity: O(1)

```js
/**
 * @param {number} x
 * @return {number}
 */
var mySqrt = function(x) {
    let start = 0;
    let end = x;
    
    // do binary search
    while(start+1 < end) {
        const mid = start + Math.floor((end-start)/2);
        const square = mid * mid;
        if(square === x) {
            return mid;
        }
        if(square < x) {
            start = mid;
        } else {
            end = mid;
        }
    }
    
    // check if end is square root of x
    if(end * end === x) return end;
    
    return start;
};
```



### Explanation

https://www.youtube.com/watch?v=3MyA0dj-_2c