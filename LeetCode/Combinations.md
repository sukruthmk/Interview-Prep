# Combinations

Given two integers *n* and *k*, return all possible combinations of *k*numbers out of 1 ... *n*.

You may return the answer in **any order**.

**Example 1:**

```
Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```

**Example 2:**

```
Input: n = 1, k = 1
Output: [[1]]
```

 

**Constraints:**

- `1 <= n <= 20`
- `1 <= k <= n`



### Leetcode

https://leetcode.com/problems/combinations/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {number} n
 * @param {number} k
 * @return {number[][]}
 */
var combine = function(n, k) {
  const result = [];
  getCombinations(n, k, 1, [], result);
  
  return result;
};

const getCombinations = (n, k, index, curr, result) => {
  if(k==0) {
    result.push([...curr]);
    return;
  }
  for(let i=index; i<=n; i++) {
    curr.push(i);
    getCombinations(n, k-1, i+1, curr, result);
    curr.pop();
  }
}
```

