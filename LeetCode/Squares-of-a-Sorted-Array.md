# Squares of a Sorted Array

Given an array of integers `A` sorted in non-decreasing order, return an array of the squares of each number, also in sorted non-decreasing order.

 

**Example 1:**

```
Input: [-4,-1,0,3,10]
Output: [0,1,9,16,100]
```

**Example 2:**

```
Input: [-7,-3,2,3,11]
Output: [4,9,9,49,121]
```

 

**Note:**

1. `1 <= A.length <= 10000`
2. `-10000 <= A[i] <= 10000`
3. `A` is sorted in non-decreasing order.



### Leetcode

https://leetcode.com/problems/squares-of-a-sorted-array/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(1) - due to in-place change

```js
/**
 * @param {number[]} A
 * @return {number[]}
 */
var sortedSquares = function(A) {
    // square each element in an array
  	// O(n)
    for(let i=0; i<A.length; i++) {
        A[i] = A[i] * A[i];
    }
    
    // sort in ascending order
  	// O(nlogn)
    A.sort((a, b) => a - b);
    
    return A;
};
```
