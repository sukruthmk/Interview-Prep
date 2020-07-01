# Valid Mountain Array

Given an array `A` of integers, return `true` if and only if it is a *valid mountain array*.

Recall that A is a mountain array if and only if:

- `A.length >= 3`

- There exists some

   

  ```
  i
  ```

   

  with 

  ```
  0 < i < A.length - 1
  ```

   such that:

  - `A[0] < A[1] < ... A[i-1] < A[i] `
  - `A[i] > A[i+1] > ... > A[A.length - 1]`


![img](https://assets.leetcode.com/uploads/2019/10/20/hint_valid_mountain_array.png)

 

**Example 1:**

```
Input: [2,1]
Output: false
```

**Example 2:**

```
Input: [3,5,5]
Output: false
```

**Example 3:**

```
Input: [0,3,2,1]
Output: true
```

 

**Note:**

1. `0 <= A.length <= 10000`
2. `0 <= A[i] <= 10000 `



### Leetcode

https://leetcode.com/problems/valid-mountain-array/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} A
 * @return {boolean}
 */
var validMountainArray = function(A) {
    let i = 0;
    
    // find peak
    while(i < A.length - 1 && A[i] < A[i+1]) {
        i++;
    }
    
    // peak cannot be first or last
    if(i === 0 || i === A.length - 1) return false;
    
    // from peak check if it is decreasing or not
    while(i < A.length - 1 && A[i] > A[i+1]) {
        i++;
    }
    
    // check if we successfully reached the end or not
    return i === A.length - 1;
};
```
