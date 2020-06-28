# Sort Array By Parity II

Given an array `A` of non-negative integers, half of the integers in A are odd, and half of the integers are even.

Sort the array so that whenever `A[i]` is odd, `i` is odd; and whenever `A[i]` is even, `i` is even.

You may return any answer array that satisfies this condition.

 

**Example 1:**

```
Input: [4,2,5,7]
Output: [4,5,2,7]
Explanation: [4,7,2,5], [2,5,4,7], [2,7,4,5] would also have been accepted.
```

 

**Note:**

1. `2 <= A.length <= 20000`
2. `A.length % 2 == 0`
3. `0 <= A[i] <= 1000`





### Leetcode

https://leetcode.com/problems/sort-array-by-parity-ii/



### Optimal Solution

#### Approach 1 - Two pass

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} A
 * @return {number[]}
 */
var sortArrayByParityII = function(A) {
    const output = new Array(A.length);
    
    // place number first
    let i = 0;
    for(const num of A) {
        if(num%2 === 0) {
            output[i] = num;
            i += 2;
        }
    }
    
    // place odd numbers next
    let j = 1;
    for(const num of A) {
        if(num%2 > 0) {
            output[j] = num;
            j += 2;
        }
    }
    
    return output;
};
```



#### Approach 2 - In-place

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} A
 * @return {number[]}
 */
var sortArrayByParityII = function(A) {
    let j = 1;
    
    for(let i=0; i<A.length; i += 2) {
        // if odd
        if(A[i] % 2 === 1) {
            // find the position to swap
            while(A[j] % 2 === 1) {
                j += 2;
            }
            
            // swap with even
            swap(A, i, j);
        }
    }
    
    return A;
};

const swap = (A, i, j) => {
    const temp = A[i];
    A[i] = A[j];
    A[j] = temp;
}
```

