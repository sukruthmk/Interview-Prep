# Duplicate Zeros

Given a fixed length array `arr` of integers, duplicate each occurrence of zero, shifting the remaining elements to the right.

Note that elements beyond the length of the original array are not written.

Do the above modifications to the input array **in place**, do not return anything from your function.

 

**Example 1:**

```
Input: [1,0,2,3,0,4,5,0]
Output: null
Explanation: After calling your function, the input array is modified to: [1,0,0,2,3,0,0,4]
```

**Example 2:**

```
Input: [1,2,3]
Output: null
Explanation: After calling your function, the input array is modified to: [1,2,3]
```

 

**Note:**

1. `1 <= arr.length <= 10000`
2. `0 <= arr[i] <= 9`



### Leetcode

https://leetcode.com/problems/duplicate-zeros/



### Optimal Solution

Time Complexity: 

Space Complexity:

```js
/**
 * @param {number[]} arr
 * @return {void} Do not return anything, modify arr in-place instead.
 */
var duplicateZeros = function(arr) {
    const size = arr.length;
    let i = 0;
    
    while(i < size) {
        if(arr[i] === 0) {
            insertZero(arr, i+1, size);
            i = i+2;
            continue;
        }
        i++;
    }
};

const insertZero = (arr, i, size) => {
    let prev = null;
    
    // insert zero at the start of i
    while(i < size) {
        const insert = prev === null ? 0 : prev;
        prev = arr[i];
        arr[i] = insert;
        i++;
    }
}
```
