# Pow(x, n)

Implement [pow(*x*, *n*)](http://www.cplusplus.com/reference/valarray/pow/), which calculates *x* raised to the power *n* (i.e. xn).



**Example 1:**

```
Input: x = 2.00000, n = 10
Output: 1024.00000
```

**Example 2:**

```
Input: x = 2.10000, n = 3
Output: 9.26100
```

**Example 3:**

```
Input: x = 2.00000, n = -2
Output: 0.25000
Explanation: 2-2 = 1/22 = 1/4 = 0.25
```

 

**Constraints:**

- `-100.0 < x < 100.0`
- `-231 <= n <= 231-1`
- `-104 <= xn <= 104`



### Leetcode

https://leetcode.com/problems/powx-n/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number} x
 * @param {number} n
 * @return {number}
 */
var myPow = function(x, n) {
  if(n < 0) return myPow(1/x, n*-1);
  if(n === 0) return 1;
  if(n === 1) return x;
  // even
  // use exponential squaring or fast exponention
  if(n % 2 === 0) { 
    return myPow(x*x, n/2);
  } else { // odd
    return x*myPow(x*x, (n-1)/2);
  }
};
```



##### Using tail recursion

```js
/**
 * @param {number} x
 * @param {number} n
 * @return {number}
 */
var myPow = function(x, n) {
  return helper(1, x, n);
};

const helper = (y, x, n) => {
  // if n is negative then it is a fraction
  if(n < 0) return helper(y, 1/x, Math.abs(n));
  if(n === 0) return y;
  if(n === 1) return x*y;
  if(n%2 === 0) {
    return helper(y, x*x, n/2); 
  }
  return helper(x*y, x*x, (n-1)/2);
}
```



### Explanation

https://www.youtube.com/watch?v=L8W38-iPdWE

https://www.youtube.com/watch?v=QhYElip1F3I