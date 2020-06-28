# Sort Array By Parity

Given an array `A` of non-negative integers, return an array consisting of all the even elements of `A`, followed by all the odd elements of `A`.

You may return any answer array that satisfies this condition.

 

**Example 1:**

```
Input: [3,1,2,4]
Output: [2,4,3,1]
The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.
```

 

**Note:**

1. `1 <= A.length <= 5000`
2. `0 <= A[i] <= 5000`



### Leetcode

https://leetcode.com/problems/sort-array-by-parity/



### Optimal Solution

#### Approach 1 - Two Pass

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} A
 * @return {number[]}
 */
var sortArrayByParity = function(A) {
    let i = 0;
    let j = 0;
    
    // two pass while loop
    while(j < A.length) {
        const num = A[j];
        // if even move it to front
        if(num % 2 === 0) {
            swap(A, i, j);
            i++;
        }
        j++;
    }
    
    return A;
};

const swap = (A, i, j) => {
    const temp = A[i];
    A[i] = A[j];
    A[j] = temp;
}
```



#### Approach 2 - Sorting

Time Complexity: O(nlogn)

Space Complexity: O(1)

```js
/**
 * @param {number[]} A
 * @return {number[]}
 */
var sortArrayByParity = function(A) {
    // custom sort
    A.sort((a, b) => a % 2 - b % 2);
    return A;
};
```

