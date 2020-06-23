# Max Subset Sum No Adjacent

Write a function that takes in an array of positive integers and returns an integer representing the maximum sum of non-adjacent elements in the array. If a sum cannot be generated, the function should return 0.

**Example:**

```
Input: [75, 105, 120, 75, 90, 135]
Output: 330
Explanation: The max non adjacent sum 330 is generated from these elements [75, 120, 135].
```



### HackerRank

https://www.hackerrank.com/challenges/max-array-sum/problem



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(1)

```js
function maxSubsetSum(arr) {
    if(arr.length === 0) return 0;
    if(arr.length === 1) return arr[0];

    let incl = arr[0];
    let excl = 0;

    for(let i=1; i<arr.length; i++) {
        const curr = Math.max(excl + arr[i], incl);
        excl = Math.max(incl, excl);
        incl = curr;
    }

    return Math.max(incl, excl);
}
```

